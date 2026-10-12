# Parámetros a cargar en Plant Simulation — queso campesino (v1.2)

Resumen para cargar en el modelo. El detalle y la justificación están en `Parametros_simulacion_queso_campesino_v1_2.md`. Los tiempos van en formato días:horas:minutos:segundos. Los nombres de los campos pueden variar según la versión del programa. Los valores no se han probado en una corrida.

## Source

| Campo | Valor |
|---|---|
| Intervalo | `0:05:20:00` con calendario de 2 turnos de 8 h, o `0:08:00:00` sin calendario |
| Cantidad | `-1` |

## Estaciones

| Objeto | Operación | Tiempo de proceso | Disponibilidad | MTTR | MTBF equivalente |
|---|---|---|---:|---|---|
| `SingleProc 1` | Recepción y control | `0:00:50:00` | 93 % | `0:01:00:00` | 13 h 17 min |
| `SingleProc 2` | Tratamiento térmico | `0:01:07:00` | 91 % | `0:02:00:00` | 20 h 13 min |
| `SingleProc 3` | Elaboración de cuajada (con 50 min de CIP) | `0:02:50:00` | 90 % | `0:01:30:00` | 13 h 30 min |
| `SingleProc 4` | Salado, moldeo y prensado | `0:01:15:00` | 91 % | `0:01:06:00` | 11 h 07 min |
| `SingleProc 5` | Enfriamiento (las 12 h pasan al buffer previo) | `0:00:05:00` | 94 % | `0:02:00:00` | 31 h 20 min |
| `SingleProc 6` | Empaquetado | `0:04:27:00` | 88 % | `0:01:30:00` | 11 h 00 min |

## Buffers

| Posición | Función | Capacidad | Permanencia mínima |
|---|---|---:|---|
| Antes de `SingleProc 1` | Cisterna en espera | 2 | `0:00:00:00` |
| Después de `SingleProc 1` | Silo de leche | 3 | `0:12:00:00` |
| Después de `SingleProc 2` | Traslado a la tina | 1 | `0:00:03:00` |
| Después de `SingleProc 3` | Reposo y traslado de la cuajada | 1 | `0:00:10:00` |
| Después de `SingleProc 4` | Cámara de enfriamiento | 4 | `0:12:00:00` |
| Producto terminado | Paletizado, inspección y retención de 3 días | 10 | `3:00:55:00` |

## Corrida

| Parámetro | Valor |
|---|---|
| Horizonte | `14:00:00:00` (14 días) |
| Calentamiento | `5:00:00:00` (5 días) |
| Réplicas | 10, con una semilla distinta en cada una |

## Distribuciones y calendario

- **Tiempo entre fallas:** exponencial.
- **Tiempo de reparación:** lognormal, con coeficiente de variación de ≈ 0,5. Para la primera corrida se pueden dejar fijos en su valor medio.
- **Calendario:** 2 turnos de 8 h, 6 días a la semana, en las estaciones 1, 2, 3, 4 y 6 y en el `Source`.
- **Sin calendario:** `SingleProc 5` y los buffers de silo, cámara de enfriamiento y producto terminado no paran.

## Métricas para anotar al final

- Lotes generados y lotes que salen de `SingleProc 6`.
- Por estación: porcentaje de tiempo trabajando, esperando, bloqueada y en falla.
- Contenido máximo y medio de cada buffer.
- Tiempo de paso de cada lote.

## Cómo calcular a partir de las métricas

- **Disponibilidad:** tiempo trabajando ÷ (tiempo trabajando + tiempo en falla), por estación.
- **Calidad:** 0,98 aplicado al final: producción buena = lotes terminados × 540 kg × 0,98.
- **OEE:** disponibilidad × desempeño (0,81 en el caso base) × calidad. Se compara con el 67 % del modelo de indicadores.

## Valores esperados de la corrida base

| Indicador | Valor esperado |
|---|---|
| Lotes por día | 3 |
| Producción de queso | ≈ 1.620 kg/día antes del rechazo; ≈ 1.590 kg/día después |
| Carga de `SingleProc 6` | ≈ 83 % del intervalo (267 min ÷ 320 min) |
| Carga de `SingleProc 3` | ≈ 53 % del intervalo (170 min ÷ 320 min) |
| Tiempo de paso de un lote | ≈ 4,5 días hasta el `Drain` |
