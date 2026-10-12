# Parámetros refinados de simulación — queso campesino (v1.2)

Complemento de la documentación v1.1 del modelo en Plant Simulation. **No cambia la topología**: se mantienen `Source` → `Buffer` → `SingleProc 1…6` → `Buffer` → `Drain`. Solo se ajustan parámetros, con base en las 12 capas de la línea de quesos y en el modelo de indicadores (OEE ≈ 67 %).

Etiquetas de origen: `CAPAS` (definido en las 12 capas), `CALCULADO`, `PUBLICADO` (referencia de la sección 9 de v1.1), `SUPUESTO` (hipótesis de simulación, sin validar en planta).

---

## 1. Tres hallazgos que cambian cómo se configura el modelo

**1.1. El horizonte de 24 h no alcanza para ver producción terminada.**
Un lote recorre la ruta en 50 + 54 + 170 + 75 + 720 + 216 = 1.285 min ≈ **21,4 h**, sin contar esperas. Con la espera de la leche (12 h) y la retención antes de liberar (72 h), el lote llega al `Drain` a las ≈ **105 h (4,4 días)**. Con 24 h solo sale, como mucho, el primer lote. Se recomienda un horizonte de **14 días con 5 días de calentamiento** (sección 6).

**1.2. `SingleProc 5` (enfriamiento de 12 h) limita la línea a 2 lotes/día.**
Un `SingleProc` procesa una entidad a la vez. Con 12 h por lote, la salida máxima es 24 h ÷ 12 h = **2 lotes/día**, menos que los 3 planificados. El modelo mostraría el enfriamiento como cuello de botella, cuando en las capas el cuello de botella es la tina y el empaque, y la cámara de enfriamiento recibe varios lotes a la vez. Sin tocar la topología, la solución es repartir el tiempo así (sección 3):
- el `Buffer` anterior a `SingleProc 5` hace de cámara de enfriamiento: **permanencia de 12 h y capacidad de 4 lotes**;
- `SingleProc 5` queda con un tiempo mínimo (**5 min**, el traslado y la inspección de peso y forma).

La alternativa (dejar 12 h en `SingleProc 5`) se conserva como escenario de sensibilidad "cuello de botella en frío" (sección 7).

**1.3. El intervalo de 5 h 20 min solo funciona con una jornada de 16 h.**
El valor sale de 16 h ÷ 3 lotes. Si la planta se simula las 24 h sin calendario, ese intervalo genera 4,5 lotes/día, no 3. Hay dos formas coherentes de usarlo (sección 2): calendario de 16 h con intervalo de 5 h 20 min, o sin calendario con intervalo de 8 h.

---

## 2. Generación de lotes (`Source`)

| Parámetro | v1.1 | v1.2 | Origen |
|---|---|---|---|
| Entidad | `*.Mus.Part` (lote abstracto) | igual; atributos nuevos en la sección 8 | — |
| Intervalo | 5 h 20 min | **5 h 20 min con calendario de 16 h** (opción A, recomendada) o **8 h 00 min sin calendario** (opción B) | CALCULADO: 16 h ÷ 3 lotes; 24 h ÷ 3 lotes |
| Lotes por día resultantes | 3 (supuesto) | 3 en ambas opciones | CAPAS (Capa 9: 3 lotes de campesino) |
| Primer lote | por defecto | en t = 0 (verificar la semántica de `Start`) | SUPUESTO |
| Variabilidad de llegada | ninguna | ninguna en el caso base; opcional ±15 min en el escenario estocástico | SUPUESTO |
| Cantidad | −1 (sin límite) | −1 | — |

Opción A: el calendario es de 2 turnos de 8 h, 6 días a la semana (Capa 10). Opción B es más simple para una primera corrida, pero las estaciones trabajan 24 h y los porcentajes de utilización salen más bajos que en las capas.

---

## 3. Tiempos de proceso por estación (caso base)

Todos son por lote de 4.500 kg de leche (540 kg de queso, 2.160 cuñas de 250 g).

| Objeto | Operación | v1.1 | v1.2 | Qué incluye | Origen |
|---|---|---:|---:|---|---|
| `SingleProc 1` | Recepción y control | 50 min | **50 min** | 30 min de recepción + 20 min de control (temperatura, acidez, antibióticos) | CAPAS |
| `SingleProc 2` | Tratamiento térmico | 54 min | **67 min** = 54 ÷ 0,81 (con PE) | 4.500 kg a 5.000 kg/h; en el mismo tiempo se llena la tina | CAPAS / CALCULADO |
| `SingleProc 3` | Elaboración de cuajada | 120 min | **170 min** | 30 min de inoculación + 90 min del cuajo al vaciado + **50 min de limpieza CIP** | CAPAS |
| `SingleProc 4` | Salado, moldeo y prensado | 75 min | **75 min** | 15 min de salado en masa + 60 min de moldeo y prensado | CAPAS |
| `SingleProc 5` | Enfriamiento y acondicionamiento | 12 h | **5 min** (traslado e inspección); las 12 h pasan al `Buffer` previo | ver 1.2 | CAPAS / SUPUESTO |
| `SingleProc 6` | Empaquetado | 216 min | **267 min** = 216 ÷ 0,81 | 2.160 cuñas ÷ 600 u/h = 216 min nominales, ajustados por la eficiencia de desempeño del modelo de indicadores (PE = 0,88 × 0,92) | CALCULADO |

Notas:
- **Tina ocupada 224 min.** La capa dice 224 min por lote (54 de llenado + 30 + 90 + 50 de CIP). Los 54 min de llenado ya están en `SingleProc 2` (la leche pasa por el pasteurizador al llenar la tina), por eso `SingleProc 3` lleva 170 min y no 224. Si el programa tiene un campo de tiempo de recuperación o limpieza, los 50 min del CIP pueden ir ahí, con el mismo efecto.
- **El desempeño (PE) se aplica solo a lo que se mueve por velocidad de máquina**: pasteurizador y empaque. La coagulación, el prensado y el enfriamiento dependen del tiempo de proceso y no se alargan.
- Los 3 min de traslado de `SingleProc 5` a `SingleProc 6` no se modelan (menos del 0,5 % del tiempo del lote).

### Buffers (capacidades y permanencias)

| Posición | Función | Capacidad | Permanencia mínima | Origen |
|---|---|---:|---:|---|
| Antes de `SingleProc 1` | Cisterna en espera | 2 lotes | 0 | SUPUESTO |
| Después de `SingleProc 1` | Silo de leche | 3 lotes (≈ 13,5 t de 15,8 t) | **12 h** | CAPAS (Q-EQ-002, espera promedio de 12 h) |
| Después de `SingleProc 2` | Traslado a la tina | 1 lote | 3 min | CAPAS |
| Después de `SingleProc 3` | Reposo y traslado de la cuajada | 1 lote | **10 min** | CAPAS (5 min de reposo + 5 de traslado) |
| Después de `SingleProc 4` | Cámara de enfriamiento | **4 lotes** | **12 h** | CAPAS (enfriamiento de 12 h) |
| Después de `SingleProc 6` (producto terminado) | Paletizado, inspección, traslado y retención hasta liberar | **10 lotes** | **72 h 55 min** = 72 h de retención + 10 min de inspección + 40 min de paletizado + 5 min de traslado | CAPAS (retención de 3 días; 4.860 kg = 9 lotes) |

Si una permanencia no se puede configurar en el `Buffer` de la versión de Plant Simulation, se suma al proceso de la estación vecina y se anota.

---

## 4. Fallas y mantenimiento

Los valores siguen siendo **supuestos de simulación**. Se afinan con dos criterios: (1) las referencias publicadas, con disponibilidades de 88–91 % y MTTR de ≈ 66 min, y (2) la lógica de la línea: las estaciones con equipos de parada larga o de más carga tienen menos disponibilidad que las pasivas.

Con las disponibilidades de v1.1 (85–92 %) en serie, el producto de las seis da ≈ 50 %, muy por debajo del 80 % global que busca el modelo. Los buffers lo compensan en parte, pero los valores eran más pesimistas que cualquier referencia publicada, por eso se suben.

| Estación | A (v1.1) | A (v1.2) | MTTR (v1.1) | MTTR (v1.2) | MTBF = MTTR · A / (1 − A) | Criterio |
|---|---:|---:|---:|---:|---:|---|
| `SingleProc 1` Recepción y control | 92 % | **93 %** | 60 min | 60 min | 13 h 17 min | Bomba y medidor; poca carga |
| `SingleProc 2` Tratamiento térmico | 88 % | **91 %** | 120 min | 120 min | 20 h 13 min | Pasteurizador de placas, reparación larga pero poco frecuente |
| `SingleProc 3` Elaboración de cuajada | 88 % | **90 %** | 90 min | 90 min | 13 h 30 min | Tina con agitación, liras y válvulas; recurso restrictivo |
| `SingleProc 4` Salado, moldeo y prensado | 90 % | **91 %** | 90 min | **66 min** | 11 h 07 min | Equipos simples; MTTR de la referencia publicada |
| `SingleProc 5` Enfriamiento | 92 % | **94 %** | 120 min | 120 min | 31 h 20 min | Refrigeración, equipo pasivo con reparación larga |
| `SingleProc 6` Empaquetado | 85 % | **88 %** | 90 min | 90 min | 11 h 00 min | Termoformadora y etiquetadora; recurso restrictivo |

Distribuciones recomendadas (`SUPUESTO`): tiempo entre fallas **exponencial** y tiempo de reparación **lognormal** con coeficiente de variación de ≈ 0,5. En el caso base se pueden dejar las dos en valor medio constante para comprobar que el flujo es correcto.

Qué falla se cuenta en qué parte: estas fallas son averías de equipo. Las paradas por limpieza (CIP) ya están en el tiempo de `SingleProc 3`, y las pérdidas de velocidad ya están en los tiempos de `SingleProc 2` y `SingleProc 6`. No hay que contarlas dos veces.

---

## 5. Calendario y calidad

| Parámetro | Valor | Origen |
|---|---|---|
| Turnos | 2 turnos de 8 h al día, 6 días a la semana (domingo sin operar) | CAPAS (Capa 10) |
| Estaciones con calendario de turnos | `SingleProc 1`, `2`, `3`, `4` y `6` y el `Source` (opción A) | CAPAS |
| Estaciones que no paran | `SingleProc 5` y los `Buffer` de silo, enfriamiento y producto terminado (refrigeración continua) | SUPUESTO |
| Rechazo de calidad | 2 % (Q = 98 %) | SUPUESTO del modelo de indicadores |
| Cómo aplicar el rechazo | Después de la corrida: producción buena = lotes terminados × 540 kg × 0,98. No se crea una ruta de rechazo, para no cambiar la topología | SUPUESTO |
| Personal | 10 personas por turno (no se modela como recurso en esta versión) | CAPAS (Capa 10) |

---

## 6. Corrida de simulación

| Parámetro | v1.1 | v1.2 | Razón |
|---|---|---|---|
| Horizonte | 24 h | **14 días (336 h)** | Un lote tarda ≈ 4,4 días en llegar al `Drain` (hallazgo 1.1) |
| Calentamiento (*warm-up*) | no definido | **5 días** | El sistema se llena con el silo, la cámara de enfriamiento y la retención antes de tener régimen |
| Ventana de medición | 24 h | 9 días | 14 − 5 |
| Réplicas | 1 | **10** (informe de la media y del intervalo de confianza al 95 %) | Hay fallas aleatorias |
| Semilla | no definida | distinta por réplica, anotada | Reproducibilidad |

---

## 7. Escenarios para comparar

| Escenario | Qué cambia respecto al caso base |
|---|---|
| **Base** | Los parámetros de las secciones 2 a 6 |
| **Optimista** | Disponibilidades +3 puntos y MTTR −20 % en todas las estaciones |
| **Pesimista** | Disponibilidades −3 puntos y MTTR +20 % en todas las estaciones |
| **Sin pérdidas** | Disponibilidades de 100 %, PE = 1 (tiempos nominales: `SingleProc 2` 54 min y `SingleProc 6` 216 min). Da la capacidad teórica |
| **Cuello de botella en frío** | `SingleProc 5` con 12 h y el `Buffer` previo sin permanencia, como en v1.1; sirve para ver el efecto de una cámara de un solo lote |
| **Sin calendario** | Opción B de la sección 2: 24 h, intervalo de 8 h |

---

## 8. Estadísticas que conviene registrar

Sin cambiar la topología se pueden leer, por réplica:
- lotes generados en el `Source` y lotes que llegan al `Drain`;
- lotes que salen de `SingleProc 6` (producción terminada, antes de la retención);
- por estación: porcentaje de tiempo trabajando, esperando, bloqueada y en falla;
- contenido máximo y medio de cada `Buffer`;
- tiempo de paso de cada lote (de su creación al `Drain`).

Atributos útiles en la entidad del lote: hora de creación, hora de salida de `SingleProc 6` y hora de llegada al `Drain`.

Con esos datos:
- **Disponibilidad (A):** tiempo trabajando ÷ (trabajando + en falla), por estación.
- **Desempeño (PE):** producción real ÷ producción ideal en el mismo tiempo; en el caso base está fijado en 0,81 (≈ 0,88 × 0,92).
- **Calidad (Q):** 0,98 aplicado después de la corrida.
- **OEE** = A × PE × Q, que se compara con el 67 % del modelo de indicadores.

---

## 9. Qué se espera de la corrida base

Es una comprobación, no un objetivo que haya que forzar:

| Indicador | Valor esperado | Cómo sale |
|---|---|---|
| Lotes por día | 3 | Intervalo de 5 h 20 min con calendario de 16 h |
| Producción de queso | ≈ 1.620 kg/día antes del rechazo; ≈ 1.590 kg/día después | 3 × 540 kg; × 0,98 |
| Carga de `SingleProc 6` | ≈ 83 % del intervalo | 267 min ÷ 320 min |
| Capacidad de `SingleProc 6` con fallas | ≈ 3,2 lotes/día | 16 h × 0,88 ÷ 267 min |
| Carga de `SingleProc 3` | ≈ 53 % del intervalo | 170 min ÷ 320 min |
| Tiempo de paso de un lote | ≈ 4,5 días hasta el `Drain` | 22,6 h de proceso y enfriamiento + 12 h de silo + 72 h 55 min de retención |

El empaque queda con poca holgura (margen del 5 al 6 % sobre los 3 lotes), que coincide con lo que dicen las capas y los VSM: el empaque es uno de los puntos críticos. Si la corrida muestra una producción distinta, revisar primero el calendario, que es lo que más cambia el resultado.

---

## 10. Trazabilidad

| Parámetro | v1.2 | Origen | Estado |
|---|---|---|---|
| Lote, rendimiento, unidades | 4.500 kg, 540 kg, 2.160 | Receta del proyecto | CAPAS |
| Tiempos de `SingleProc 1`, `3`, `4` y permanencias de los `Buffer` | Sección 3 | Capas 4 y 8 | CAPAS |
| Tiempos de `SingleProc 2` y `6` | 67 y 267 min | 54 min y 216 min de las capas, ajustados con PE = 0,81 | CALCULADO |
| Calendario | 2 × 8 h, 6 días | Capa 10 | CAPAS |
| Intervalo del `Source` | 5 h 20 min (con calendario) u 8 h (sin calendario) | 16 h ÷ 3; 24 h ÷ 3 | CALCULADO |
| Disponibilidades y MTTR | Sección 4 | Rango publicado de 88–91 % y de ≈ 66 min | SUPUESTO |
| MTBF | Sección 4 | A · MTTR ÷ (1 − A) | CALCULADO |
| PE = 0,88 × 0,92; rechazo del 2 % | Sección 3 y 5 | Modelo de indicadores | SUPUESTO |
| Horizonte, calentamiento y réplicas | 14 días, 5 días, 10 | Tiempo de paso del lote | CALCULADO / SUPUESTO |
