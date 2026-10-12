# Lectura de los resultados de la simulación — queso campesino, corrida de 14 días

Interpretación del gráfico *Resource Statistics* de la primera corrida. Los porcentajes se leyeron a ojo del gráfico, así que son aproximados.

## 1. Cómo leer el gráfico

Cada barra es una estación y muestra en qué estado estuvo durante los 336 h de la corrida:

| Color | Estado | Significado |
|---|---|---|
| Verde | Working | Procesando un lote |
| Gris | Waiting | Libre, esperando que llegue un lote |
| Rojo | Failed | Averiada |
| Amarillo | Blocked | Terminó su lote, pero no puede soltarlo porque la siguiente estación está ocupada |

No aparece "Paused" (azul), lo que indica que no se aplicó un calendario de turnos.

## 2. Resultados por estación

| Estación | Trabajando | Esperando | Falla | Bloqueada | Lectura |
|---|---:|---:|---:|---:|---|
| Recepción | ≈ 10 % | ≈ 82 % | ≈ 8 % | — | Casi siempre libre |
| Tratamiento térmico | ≈ 13 % | ≈ 78 % | ≈ 9 % | — | Casi siempre libre |
| Elaboración de cuajada | ≈ 34 % | ≈ 58 % | ≈ 8 % | — | La tina, segunda más cargada |
| Salado, moldeo y prensado | ≈ 14 % | ≈ 77 % | ≈ 8 % | — | Casi siempre libre |
| Enfriamiento | ≈ 1 % | ≈ 79 % | ≈ 11 % | ≈ 8 % | Ver sección 4 |
| Empaque | ≈ 50 % | ≈ 34 % | ≈ 15 % | — | La más cargada |

## 3. Lo que sí tiene sentido

- **Fallas.** El 8–9 % de las estaciones 1 a 4 es casi 100 − disponibilidad configurada (93, 91, 90 y 91 %). El empaque, con ≈ 15 %, se acerca al 12 % esperado (disponibilidad de 88 %).
- **Cuello de botella.** El empaque es la estación más cargada y la tina le sigue. Coincide con lo que dicen las capas y los VSM.
- **Bloqueo del enfriamiento.** Entre el enfriamiento y el empaque no hay buffer. La estación de enfriamiento termina su traslado de 5 min y no puede soltar el lote cuando el empaque está ocupado o averiado. Ese ≈ 8 % de bloqueo confirma que el empaque limita la línea.

## 4. Dos cosas que pueden confundir

**4.1. La barra de enfriamiento no muestra el enfriamiento real.** Las 12 h de enfriamiento se pasaron al buffer previo, y este gráfico solo muestra las estaciones. El ≈ 1 % de trabajo y el ≈ 79 % de espera no significan que el enfriamiento no se use.

**4.2. Los porcentajes parecen medidos sobre 24 h, no sobre 16 h.** Por los porcentajes de trabajo (≈ 42 lotes en 14 días), parece que corrieron la opción sin calendario: 24 h de operación y un lote cada 8 h. Con esa opción los porcentajes salen más bajos que en las capas, que usan jornadas de 16 h. Para compararlos, se multiplican por 1,5:

| Estación | En el gráfico | Equivalente sobre 16 h | Esperado según las capas |
|---|---:|---:|---:|
| Elaboración de cuajada (tina) | ≈ 34 % | ≈ 51 % | ≈ 53 % |
| Empaque | ≈ 50 % | ≈ 75 % | ≈ 83 % |

Esto es una inferencia, no un dato confirmado: hay que verificar qué intervalo del `Source` se usó realmente.

## 5. Variabilidad de una sola réplica

El enfriamiento falló ≈ 11 % (esperado ≈ 6 %) y el empaque ≈ 15 % (esperado ≈ 12 %). Con una sola réplica y reparaciones de 1,5 a 2 h, esa diferencia es normal. Conviene correr las 10 réplicas previstas, con una semilla distinta en cada una, y promediar.

## 6. Qué no se puede concluir con este gráfico

El gráfico no permite calcular el OEE, ni la producción, ni saber si se respetan las 12 h de enfriamiento y la retención.

Para eso hacen falta estos datos:

- lotes generados por el `Source`;
- lotes que salen del empaque y lotes que llegan al `Drain`;
- contenido máximo y medio de cada buffer;
- tiempo de paso de cada lote.

Con esos datos se pueden calcular la producción, la disponibilidad y el OEE, y compararlos con el 67 % del modelo de indicadores.
