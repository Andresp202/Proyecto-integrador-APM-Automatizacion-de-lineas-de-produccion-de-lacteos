# Modelo de cálculo — Línea de quesos

Plantilla en Excel para calcular demanda, lotes, Takt, OEE, capacidad, utilización, rendimiento y MLT de una línea de producción de quesos (Campesino, Mozzarella y Sopó), con las definiciones del curso (Cortés y García) y los IDs del archivo `Linea_de_quesos.md` (Q-CAP, Q-TMP, Q-RES).

> **Todos los valores son ilustrativos (ASSUMED).** No son datos de una planta real ni del equipo. Sirven para que el modelo calcule y se reemplazan cuando existan valores reales. Los valores están calibrados para una **planta colombiana pequeña/mediana con OEE ≈ 65 %**.

**Archivo:** [`modelo_calculo_quesos_realista.xlsx`](modelo_calculo_quesos_realista.xlsx)

## Estructura del libro

```mermaid
flowchart LR
    A[Entradas<br/>celdas editables] --> B[Cálculos<br/>fórmulas]
    B --> C[Indicadores<br/>resumen]
```

| Hoja | Contenido |
|---|---|
| **Entradas** | Parámetros editables (azul sobre amarillo) con columna *Origen* (`PUBLIC`, `REFERENCE`, `ASSUMED`, `CALCULATED`, `PROPOSED`, `PENDING`) y nota. |
| **Cálculos** | Lotes, balance de masa, tiempo disponible y OEE, Takt, capacidad, utilización, MLT y WIP. Todo son fórmulas. |
| **Indicadores** | Resumen con el nivel de OEE según la tabla de Cortés. |

Colores: azul sobre amarillo = entrada editable · negro = fórmula · verde = vínculo directo a otra hoja.

## Entradas del modelo

### Parámetros generales

| Parámetro | Valor | Unidad | Base |
|---|---|---|---|
| Demanda total de queso | 3.000 | kg/día | Ejemplo de la sección Convenciones del archivo (6 lotes × 500 kg) |
| Turnos por día | 2 | turnos/día | Supuesto |
| Horas por turno | 8 | h/turno | Supuesto |
| Días operativos por semana | 6 | días/sem | Supuesto (solo capacidad semanal) |
| Equipos restrictivos en paralelo (tinas) | 4 | unidades | Supuesto; con 3 tinas la utilización supera 100 % |
| Tiempo de cambio de producto | 40 | min/cambio | Supuesto |
| MTBF | 22 | h | Supuesto |
| MTTR | 4 | h | Supuesto |
| Tasa de eficiencia RE | 88 % | — | Supuesto, calibrado al OEE objetivo |
| Eficiencia en velocidad SE | 92 % | — | Supuesto, calibrado al OEE objetivo |
| Personas por turno (línea) | 6 | personas | Supuesto (una por rol de la capa 10) |
| Densidad de la leche | 1.03 | kg/L | Referencia (análisis de UHT) |

### Parámetros por producto

| Parámetro | Unidad | Campesino | Mozzarella | Sopó |
|---|---|---|---|---|
| Mezcla de demanda | % | 40 % | 35 % | 25 % |
| Tamaño de lote (leche) | kg leche/lote | 4.500 | 4.500 | 4.500 |
| Rendimiento | kg queso/kg leche | 0.105 | 0.1 | 0.095 |
| Rechazo | % | 4 % | 4 % | 4 % |
| Ocupación de la tina | h/lote | 3.5 | 4 | 3.5 |
| Preparación | min/lote | 30 | 30 | 30 |
| Limpieza (CIP) | min/lote | 45 | 45 | 45 |
| Fabricación activa | h/lote | 5 | 5.5 | 5 |
| Esperas y transferencias | h/lote | 1 | 1 | 1 |
| Maduración | días | 0 | 0 | 30 |
| Almacenamiento de producto terminado | h | 24 | 24 | 24 |

## Fórmulas principales

```text
Lotes/día (enteros)   = ROUNDUP( demanda_producto / (kg_leche_lote × rendimiento × (1 − rechazo)) )

Tt  = turnos × horas × 60                              (min/día por equipo)
Tip = Σ lotes × (preparación + CIP) / n  +  cambios × t_cambio
Tep = Tt − Tip
A   = MTBF / (MTBF + MTTR)
Ter = Tep × A                                          (tiempo neto disponible)
PE  = RE × SE
Q   = (producción − defectuosos) / producción          (ponderada por lotes)
OEE = A × PE × Q

Takt T = Ter / lotes_por_día
Tc     = (ocupación_diseñada / PE) / n                 (ciclo efectivo de la etapa restrictiva)
Cumple si Tc ≤ T

PC  = n · S · H · Rp                                   (capacidad nominal)
U   = Q / PC                                           (utilización, definición del curso)
Q-CAP-010 = ocupación real / (n · Ter)                 (utilización de la capa 9)

MLT = Tsu + fabricación activa + esperas + maduración + almacenamiento
```

Los lotes se redondean hacia arriba, por lo que la producción planificada supera la demanda (sobreproducción por lotes enteros). Con el lote como unidad (Q = 1), el término (Q−1)·Tc_n del curso vale cero.

## Resultados con las entradas actuales

| Indicador | Valor |
|---|---|
| Lotes requeridos por día | 8 (3 + 3 + 2) |
| Producción buena planificada | 3.478 kg/día (15,9 % sobre la demanda) |
| Disponibilidad A | 84,6 % |
| Eficiencia de desempeño PE | 81,0 % |
| Tasa de calidad Q | 96 % |
| **OEE** | **65,8 %** — nivel «Regular» (tabla de Cortés) |
| Takt / Tc | 77,2 / 68,3 min/lote — Cumple el Takt (margen 11,5 %) |
| Capacidad diaria con la mezcla planificada | 3.717 kg/día |
| Capacidad nominal PC | 7.545 kg/día |
| Utilización U = Q/PC | 46,1 % |
| Utilización Q-CAP-010 | 88,5 % |
| Rendimiento físico ponderado | 0,101 kg/kg |
| Productividad de materia prima | 0,097 kg bueno/kg leche |
| Productividad de mano de obra | 290 kg/persona-turno |
| MLT Campesino / Mozzarella / Sopó | 1,3 / 1,3 / 31,3 días |
| % de valor agregado | 11,5 % / 12,9 % / 0,5 % |
| Inventario en maduración (Sopó) | 24.624 kg |

## Supuestos y limitaciones

- **Todo es ASSUMED.** Las referencias respaldan solo el OEE típico y los rendimientos; MTBF, MTTR, RE, SE, rechazo y tiempos son criterio propio y deben reemplazarse con registros de la planta.
- **Tinas:** con pérdidas realistas, 3 tinas no alcanzan para la demanda de ejemplo; se usan 4. Si se confirma otro número, cambiar `Entradas!D10`.
- **Lotes enteros diarios:** la sobreproducción baja si los lotes se reparten entre días.
- **Capacidad dedicada:** se cuentan solo lotes completos por turno (conservador).
- **Inactividad:** preparación, CIP y cambios de producto se tratan como inactividad planeada; según la definición del curso podrían ir como no planeada, lo que bajaría la disponibilidad y el OEE.
- **Dos utilizaciones distintas** (U = Q/PC y Q-CAP-010); conviene alinear con el equipo cuál se reporta.
- **Fuera de alcance:** eficiencia económica (ventas/costos), que requiere precios y costos.

## Referencias

- Cortés y García — definiciones de OEE, Takt, capacidad, utilización, rendimiento y MLT (material del curso).
- Reliamag, *OEE Benchmarks by Industry: What World Class Really Means* — alimentos y bebidas: OEE típico 60–78 %.
- Enaovision, *OEE benchmark by industry* — alimentos y bebidas: mediana 62 %, rango 49–73 % (58 plantas).
- Vorne / Nakajima (TPM) — origen del 85 % «world class» (manufactura discreta).
- CONtexto Ganadero, *¿Cuántos litros de leche se necesitan para producir 1 kg de queso?* — rendimiento ~10 % (≈10 L/kg) y 10–12 L/kg en quesos frescos.
- Universidad de Chile (repositorio.uchile.cl) — rendimiento práctico de queso Gouda: 10,81 kg/100 kg de leche.

Los benchmarks de OEE son referencias generales de la industria, no específicas de Colombia.
