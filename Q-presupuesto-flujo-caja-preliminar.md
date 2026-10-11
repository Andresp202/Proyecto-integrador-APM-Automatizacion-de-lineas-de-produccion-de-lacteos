# Línea de Quesos — Presupuesto y flujo de caja PRELIMINAR

## Información general

**Proyecto:** Transformación Digital Industrial (TDI) — APM 2026-2S
**Módulo:** 3 — Planeación y evaluación de proyectos
**Línea evaluada:** Quesos (código `Q`), línea seleccionada para el gemelo digital
**Empresa integradora:** equipo de 6 ingenieros mecatrónicos
**Cliente de referencia:** Alpina Productos Alimenticios S.A.S., planta de Sopó (modelo académico)
**Estado:** 🟡 PRELIMINAR. Todas las cifras están sujetas a cambio al confirmar el alcance, cerrar las capas 8 a 10 de la línea de quesos y conseguir cotizaciones formales.
**Fecha de corte de precios:** octubre de 2026

> **Criterio de evaluación:** se pidió evaluar el **peor escenario posible** (escenario *pesimista*). Todos los supuestos se inclinan en contra del proyecto: costos altos, beneficios bajos, dólar alto, tasa exigente y arranque lento. Para tener un punto de comparación se calcula también un escenario *esperado* con supuestos típicos de la industria. Las etiquetas de origen siguen la convención del proyecto: `PUBLIC`, `REFERENCE`, `ASSUMED`, `CALCULATED`, `PROPOSED`.

---

# 0. Resumen

| Indicador | Pesimista (peor caso) | Esperado | Unidad |
|---|---|---|---|
| Precio de la solución (inversión del cliente, año 0) | 4.400 | 2.673 | M COP |
| Equivalente en dólares | 1.128 | 822 | miles USD |
| Beneficios anuales en régimen | 427 | 1.295 | M COP/año |
| Costos de operación adicionales (OPEX) | 256 | 195 | M COP/año |
| VPN a 10 años | **-3.288** | **1.446** | M COP |
| TIR | < 0 (negativa) | 26,1 % | % E.A. |
| Periodo de recuperación simple | No se recupera en 10 años | 3,5 años | años |
| Periodo de recuperación descontado | No se recupera | 5,1 años | años |
| Utilidad del integrador (margen menos costo financiero) | 407 | 333 | M COP |
| Necesidad máxima de financiación del integrador | 1.928 | 425 | M COP |

**Lectura rápida:**
1. **En el peor caso el proyecto no es viable para el cliente.** Los beneficios tendrían que ser **3,9 veces** mayores para que el VPN llegue a cero. Ningún factor por sí solo lo vuelve viable (sección 9).
2. **En el escenario esperado sí es viable:** TIR de 26 % y recuperación en 3,5 años. Sigue siendo viable aunque los beneficios caigan hasta el 66 % de lo estimado.
3. **La celda robotizada es el componente que más destruye valor en el peor caso.** Cuesta 1.726 M COP con todos los cargos y solo ahorra 4 operarios. Por sí sola resta 1.404 M COP de VPN. Al ser un requisito académico del curso, su justificación debe apoyarse en seguridad, ergonomía y trazabilidad, no solo en el ahorro de mano de obra.
4. **Lo que decide la viabilidad no es el CAPEX sino los beneficios de proceso:** rendimiento quesero, sobrepeso y ventas adicionales. Estos beneficios deben sustentarse con los KPI del Módulo 2 (escenario base frente a propuesto) y con la simulación.

---

# 1. Alcance y criterios

- **Por línea:** el presupuesto cubre solo la línea de quesos, porque será la línea del gemelo digital. Los recursos de planta (`PL-*`) no se presupuestan aquí.
- **Celda robotizada:** se incluye aunque su ubicación final no está definida. Se asume al final de la línea de quesos (encajonado y paletizado, Q-OP-018 a Q-OP-020). Si se ubica en otra línea, se traslada su costo y su beneficio.
- **Dos perspectivas y dos flujos de caja:**
  - **Flujo de caja de la inversión (cliente):** ¿le conviene a la planta pagar la solución? Anual, 10 años, con VPN, TIR y periodo de recuperación (sección 8).
  - **Flujo de caja de ejecución (integrador):** ¿cómo se mueve el dinero de la empresa integradora mientras ejecuta el proyecto? Mensual, con curva S (sección 10).
- **Salarios de los ingenieros:** los 6 integrantes trabajan en la línea de quesos durante toda la implementación. Su salario es un costo directo del proyecto y entra en el precio de la oferta.
- **Moneda:** pesos colombianos corrientes, sin indexar beneficios por inflación (supuesto conservador). Los equipos importados se cotizan en USD y se convierten con la TRM del escenario.

---

# 2. Parámetros financieros

| Parámetro | Pesimista | Esperado | Origen / justificación |
|---|---|---|---|
| TRM | 3.900 COP/USD | 3.250 COP/USD | `PUBLIC`: TRM del 9-oct-2026 = 3.218,75; 1-ene-2026 = 3.757,08; 9-oct-2025 = 3.879,80. El pesimista toma el nivel de hace un año (≈ 3.880), redondeado hacia arriba |
| Horizonte de evaluación | 10 años | 10 años | `ASSUMED` = vida útil fiscal de maquinaria y equipo |
| Tasa de descuento (TMAR, nominal en COP) | 18 % | 14 % | `ASSUMED`: costo de capital típico de una manufacturera colombiana en el esperado; +4 puntos de prima de riesgo en el pesimista |
| Impuesto de renta | 35 % | 35 % | `PUBLIC` (Estatuto Tributario, art. 240) |
| Depreciación | Línea recta: equipos 10 años; software, red y servidores 5 años | Igual | `REFERENCE` (tasas fiscales usuales en Colombia, ET art. 137) |
| Valor de salvamento | 0 % | 10 % del activo de 10 años | `ASSUMED` |
| Beneficios en el año 1 (arranque) | 50 % | 75 % | `ASSUMED` (curva de aprendizaje) |
| Flete y seguro internacional | 8 % FOB | 8 % FOB | `ASSUMED` |
| Arancel | 5 % | 0 % | `ASSUMED`: bienes de capital entre 0 y 5 % según subpartida |
| IVA de importación tratado como costo | 19 % | 0 % | `PUBLIC` (19 %). En el esperado se recupera como descuento tributario por bienes de capital (ET art. 258-1); en el pesimista no |
| Agente de aduanas y nacionalización | 2 % CIF | 2 % CIF | `ASSUMED` |
| Instalación eléctrica y mecánica (subcontratada) | 15 % del FOB del hardware | 15 % | `ASSUMED` |
| Contingencia | 15 % | 10 % | `ASSUMED` |
| Margen del integrador | 15 % sobre costo | 15 % | `ASSUMED`: rango habitual de integradores, 10–20 % |
| Duración de la implementación | 9 meses | 7 meses | `ASSUMED`, hasta tener cronograma (EDT) |
| Tasa de financiación del integrador | 1,9 % mensual (≈ 25,3 % E.A.) | Igual | `ASSUMED` (crédito comercial de corto plazo) |
| Días de producción por año | 300 | 300 | `ASSUMED` (6 días/semana) |

## Costo de la mano de obra

| Concepto | Valor | Origen |
|---|---|---|
| Salario mínimo 2026 | 1.750.905 COP/mes | `PUBLIC` (Decretos 1469 y 1470 de 2025) |
| Auxilio de transporte 2026 | 249.095 COP/mes | `PUBLIC` |
| Factor prestacional de operarios (con exoneración de salud, SENA e ICBF, ET art. 114-1) | 1,3835 | `CALCULATED`: cesantías 8,33 % + intereses 1 % + prima 8,33 % + vacaciones 4,17 % + pensión 12 % + ARL 0,522 % + caja 4 % |
| Costo empresa de un operario (1 SMMLV) | 2.715.497 COP/mes | `CALCULATED`. En el pesimista se toma el operario de menor costo, lo que reduce el ahorro |
| Salario de cada ingeniero del integrador | 4.500.000 COP/mes | `ASSUMED`: por encima del rango junior (2,6–3,5 M) y dentro del semi-senior (3,5–5,5 M) de la guía salarial 2026 (Tributi) |
| Factor prestacional de ingenieros (peor caso, sin exoneración) | 1,5185 | `CALCULATED`: el anterior + salud 8,5 % + ICBF 3 % + SENA 2 % |
| Costo empresa de un ingeniero | 6.833.340 COP/mes | `CALCULATED` |
| Equipo de ingeniería | 6 ingenieros, salario igual, 100 % de dedicación | Decisión del equipo |

---

# 3. Base productiva supuesta de la línea de quesos

La línea de quesos dejó en `PENDING` los tamaños de lote, las capacidades y los tiempos (capas 8 a 10). Para poder valorar los beneficios se fijan aquí **supuestos típicos de la industria**, marcados `ASSUMED`. Deben trasladarse a las capas 9 y 10 del documento de quesos o reemplazarse cuando se cierren.

| Parámetro | Q-PRD-001 Campesino | Q-PRD-002 Mozzarella | Q-PRD-003 Sopó | Origen |
|---|---|---|---|---|
| Presentación | Cuña 250 g | Bloque 250 g | Cuña 180 g | `PUBLIC` (capa 1) |
| Leche por lote (tina) | 5.000 L | 5.000 L | 5.000 L | `ASSUMED` (tinas industriales de 5.000–20.000 L) |
| Litros de leche por kg de queso | 7,7 | 9,5 | 10,5 | `ASSUMED` (regla general de ≈ 10 L/kg, ajustada por humedad de cada tipo, `REFERENCE`) |
| Rendimiento | 13,0 % | 10,5 % | 9,5 % | `CALCULATED` |
| Producto por lote | 649 kg | 526 kg | 476 kg | `CALCULATED` |
| Lotes por día | 3 | 2 | 1 | `ASSUMED` (2 tinas, 2 turnos) |
| Producción diaria | 1.948 kg · 7.792 un | 1.053 kg · 4.211 un | 476 kg · 2.646 un | `CALCULATED` |
| Precio al público (PVP) por unidad | 8.000 COP | 11.300 COP | 15.000 COP | `ASSUMED` / `REFERENCE` (mozzarella 250 g a 11.300 COP en Éxito; queso madurado Alpina 240 g a 20.100 COP en Farmatodo, de donde se escala el Sopó 180 g) |
| Precio neto al fabricante (PVP × 0,70) | 22.400 COP/kg | 31.640 COP/kg | 58.333 COP/kg | `ASSUMED` (descuenta margen del canal e impuestos, ≈ 30 %) |
| Ventas anuales | 13.091 M COP | 9.992 M COP | 8.333 M COP | `CALCULATED` |

| Total de la línea | Valor | Origen |
|---|---|---|
| Leche procesada | 30.000 L/día | `CALCULATED` |
| Producción | 3.477 kg/día · 1.043.062 kg/año | `CALCULATED` |
| Ventas | 31.416 M COP/año | `CALCULATED` |
| Precio neto promedio | 30.119 COP/kg | `CALCULATED` |
| Margen de contribución (precio − costos variables) | 20 % pesimista · 25 % esperado | `ASSUMED`. Referencia pública: Alpina reportó un margen EBITDA ≈ 15,5 % en el primer semestre de 2025 (`PUBLIC`, Valora Analitik). El margen de contribución es mayor que el EBITDA porque este último ya descuenta los costos fijos |
| Personal del escenario base | 14 operarios por turno (recepción 1, tinas 3, moldeo y prensado 2, hilado 1, empaque 3, encajonado y paletizado 2, maduración 1, supervisor 1) | `ASSUMED` (operación semimanual con registros en papel) |

---

# 4. Escenario propuesto — paquetes de automatización

| Paquete | Alcance | Operaciones / equipos de quesos | Beneficio que habilita |
|---|---|---|---|
| P1 | Automatización de las 2 tinas: RTD, pH en línea, sensor óptico de coagulación, dosificación automática de cultivo, cuajo y CaCl₂, válvulas de camisa y desuerado, variadores de lira y agitador | Q-OP-006 a Q-OP-010 · Q-EQ-005 a Q-EQ-008 | Rendimiento quesero (corte en el punto óptimo), menos rechazos, recetas ISA-88 |
| P2 | Integración del pasteurizador al PLC | Q-OP-005 · Q-EQ-004 | Registro de inocuidad por batch |
| P3 | Prensado con control de presión y tiempo | Q-OP-014 · Q-EQ-012 | Uniformidad de humedad y peso |
| P4 | Control de temperatura de la hiladora | Q-OP-015 · Q-EQ-013 | Calidad de la mozzarella |
| P5 | Monitoreo y control de la cámara de maduración | Q-OP-016 · Q-EQ-014 | Trazabilidad de maduración del Sopó |
| P6 | Checkweigher con rechazo + impresora-etiquetadora con lote | Q-OP-018 · Q-EQ-016 | Menos sobrepeso, cumplimiento metrológico, trazabilidad |
| P7 | Celda robotizada de encajonado y paletizado | Q-OP-018 a Q-OP-020 · Q-EQ-016 a Q-EQ-018 | Menos operarios, ergonomía, seguridad |
| P8 | Tablero de control (PLC CompactLogix, compatible con Logix Emulate del curso) | Toda la línea | Control secuencial y recetas |
| P9 | Red OT/IT y servidor | Toda la línea | Arquitectura ISA-95 |
| S1–S3 | SCADA Ignition (el SCADA del curso) | Nivel 2 | Supervisión, alarmas, historiador |
| S4–S6 | MES Sepasoft: OEE, Track & Trace, recetas | Nivel 3 | OEE en línea, genealogía de lotes, cambios de producto |

---

# 5. Presupuesto de inversión (CAPEX)

## 5.1 Hardware importado

Factor de nacionalización pesimista = (CIF + arancel + agencia + IVA) ÷ FOB = **1,371** (esperado: 1,102).

| ID | Ítem | Cant. | Precio unitario FOB (USD) | Total FOB (USD) | Nacionalizado pesimista (M COP) | Origen |
|---|---|---|---|---|---|---|
| P1 | Automatización de 2 tinas queseras (RTD, pH en línea, sensor óptico de coagulación, dosificación de cultivo/cuajo/CaCl2, válvulas de camisa y desuerado, variadores de lira/agitador) | 2 | 26.000 | 52.000 | 278,1 | `ASSUMED` (precio de referencia, sin cotización) |
| P2 | Integración del pasteurizador al PLC (RTD, caudalímetro, señal de FDV) | 1 | 8.000 | 8.000 | 42,8 | `ASSUMED` |
| P3 | Prensado con control de presión y tiempo (transmisores, válvulas proporcionales) | 1 | 15.000 | 15.000 | 80,2 | `ASSUMED` |
| P4 | Control de temperatura de la hiladora de mozzarella | 1 | 6.000 | 6.000 | 32,1 | `ASSUMED` |
| P5 | Monitoreo y control de cámara de maduración (T y HR) | 1 | 6.000 | 6.000 | 32,1 | `ASSUMED` |
| P6a | Báscula de control (checkweigher) con rechazador | 1 | 30.000 | 30.000 | 160,4 | `REFERENCE` (rango medio de checkweighers industriales con rechazo: AUD 25–60 mil) |
| P6b | Impresora-etiquetadora print & apply con lote y vencimiento | 1 | 15.000 | 15.000 | 80,2 | `ASSUMED` |
| P7 | Celda robotizada de encajonado y paletizado llave en mano (robot, gripper, transportadores, cerramiento y seguridad) | 1 | 220.000 | 220.000 | 1.176,4 | `REFERENCE` (celdas de paletizado de nivel de entrada: AUD 190–250 mil, más gripper, transportadores y seguridad) / `ASSUMED` |
| P8 | Tablero de control: PLC CompactLogix 5380, E/S distribuidas, HMI local, gabinete inoxidable | 1 | 45.000 | 45.000 | 240,6 | `ASSUMED` |
| P9 | Red OT/IT: switches administrables, fibra, firewall, servidor industrial, UPS | 1 | 25.000 | 25.000 | 133,7 | `ASSUMED` |
| | **Total hardware** | | | **422.000** | **2.256,5** | `CALCULATED` |

Desglose de la nacionalización pesimista (USD): CIF 455.760 · arancel 22.788 · agencia 9.115 · IVA 90.924.

## 5.2 Software (licencias perpetuas, precio de lista)

| ID | Licencia | Precio de lista (USD) | Con IVA pesimista (M COP) | Origen |
|---|---|---|---|---|
| S1 | Ignition: Application Building Suite (Perspective + Reporting) | 13.500 | 62,7 | `PUBLIC` (lista oficial de Inductive Automation / Sepasoft, 2026) |
| S2 | Ignition: Industrial Historian Suite | 3.500 | 16,2 | `PUBLIC` (lista oficial de Inductive Automation / Sepasoft, 2026) |
| S3 | Ignition: Alarm Management Suite | 3.200 | 14,9 | `PUBLIC` (lista oficial de Inductive Automation / Sepasoft, 2026) |
| S4 | Sepasoft MES: OEE Downtime | 22.700 | 105,4 | `PUBLIC` (lista oficial de Inductive Automation / Sepasoft, 2026) |
| S5 | Sepasoft MES: Track & Trace | 22.700 | 105,4 | `PUBLIC` (lista oficial de Inductive Automation / Sepasoft, 2026) |
| S6 | Sepasoft MES: Settings & Changeover (recetas) | 9.100 | 42,2 | `PUBLIC` (lista oficial de Inductive Automation / Sepasoft, 2026) |
| | **Total software** | **74.700** | **346,7** | `CALCULATED` |

Los integradores certificados suelen recibir entre 15 y 30 % de descuento sobre el precio de lista. En ambos escenarios se usa el precio de lista (conservador).

## 5.3 Ingeniería del integrador (salarios de los 6 ingenieros)

| Concepto | Pesimista | Esperado | Origen |
|---|---|---|---|
| Ingenieros | 6 | 6 | Decisión del equipo |
| Costo empresa por ingeniero | 6.833.340 COP/mes | 6.833.340 COP/mes | `CALCULATED` |
| Duración | 9 meses | 7 meses | `ASSUMED` |
| Esfuerzo | 54 meses-ingeniero | 42 meses-ingeniero | `CALCULATED` |
| **Costo de ingeniería** | **369,0 M COP** | **287,0 M COP** | `CALCULATED` |
| Gastos generales del integrador (licencias Studio 5000 y RobotStudio, pólizas de cumplimiento, transporte a Sopó, contabilidad) | 12,0 M COP/mes → 108,0 M COP | 10,0 M COP/mes → 70,0 M COP | `ASSUMED` |

Actividades que cubre la ingeniería: levantamiento, diseño detallado (P&ID, lista de E/S, arquitectura), programación de PLC (Grafcet y Ladder), SCADA y MES, simulación y gemelo digital, programación de la celda (RobotStudio), pruebas FAT/SAT, puesta en marcha, capacitación y documentación.

## 5.4 Resumen del presupuesto y precio de la oferta

| Concepto | Pesimista (M COP) | Esperado (M COP) |
|---|---|---|
| Hardware nacionalizado | 2.256,5 | 1.331,8 |
| Software | 346,7 | 242,8 |
| Instalación eléctrica y mecánica | 246,9 | 181,3 |
| Ingeniería (salarios) | 369,0 | 287,0 |
| Gastos generales | 108,0 | 70,0 |
| **Costo directo** | **3.327,0** | **2.113,0** |
| Contingencia | 499,1 | 211,3 |
| **Costo total del proyecto** | **3.826,1** | **2.324,3** |
| Margen del integrador | 573,9 | 348,6 |
| **Precio de la oferta = CAPEX del cliente** | **4.400,0** | **2.672,9** |
| Participación de la celda robotizada en el precio | 1.726,0 (39 %) | — |

---

# 6. Costos de operación adicionales (OPEX)

| Concepto | Pesimista (M COP/año) | Esperado (M COP/año) | Base de cálculo | Origen |
|---|---|---|---|---|
| Mantenimiento de equipos nuevos | 99,5 | 47,3 | Pesimista: 5 % del FOB de equipos y 7 % de la celda. Esperado: 3 % y 5 % | `REFERENCE` (robots: 5–10 % anual) / `ASSUMED` |
| Soporte anual de software (TotalCare) | 58,3 | 48,6 | 20 % del precio de lista | `PUBLIC` |
| Técnico de automatización adicional | 49,8 | 49,8 | 1 técnico, 3,0 M COP/mes + prestaciones | `ASSUMED` |
| Energía de la celda y de los equipos nuevos | 49,0 | 49,0 | 12 kW × 16 h × 300 días × 850 COP/kWh | `ASSUMED` |
| **Total OPEX** | **256,5** | **194,6** | | `CALCULATED` |

---

# 7. Beneficios anuales (escenario propuesto frente al base)

| Beneficio | Supuesto pesimista | Supuesto esperado | Pesimista (M COP/año) | Esperado (M COP/año) | Cálculo |
|---|---|---|---|---|---|
| Menos operarios | 4 (solo la celda robotizada, 2 por turno) | 6 (celda + tinas automáticas) | 130,3 | 195,5 | n × 2.715.497 COP/mes × 12 |
| Menos sobrepeso (*giveaway*) con checkweigher y prensado controlado | −0,5 pt | −1,0 pt | 141,4 | 282,7 | pt × 1.043.062 kg × precio neto × 0,90 |
| Mayor rendimiento quesero (corte en el punto óptimo, dosificación exacta) | +0,3 % | +1,0 % | 84,8 | 282,7 | Igual |
| Menos lotes rechazados o reprocesados | −0,25 pt | −0,5 pt | 70,7 | 141,4 | Igual |
| Ventas adicionales por mayor OEE | 0 % (sin demanda adicional) | +5 % de volumen | 0,0 | 392,7 | % × ventas × margen de contribución (20 % / 25 %) |
| **Total** | | | **427,2** | **1.295,1** | `CALCULATED` |

**Por qué el producto recuperado se valora al 90 % del precio:** el queso que deja de regalarse en sobrepeso o de perderse en rechazos ya consumió leche. Venderlo solo agrega empaque y energía (≈ 10 %, `ASSUMED`). Las ventas adicionales, en cambio, requieren más leche, por eso se valoran solo con el margen de contribución.

Todos los porcentajes de mejora son `ASSUMED` y deben reemplazarse por la comparación de KPI del Módulo 2 (OEE, rechazos, rendimiento) y por la simulación en Tecnomatix.

---

# 8. Flujo de caja de la inversión (perspectiva del cliente)

## 8.1 Escenario pesimista (M COP)

| Año | Beneficios | OPEX | Depreciación | Utilidad antes de impuestos | Impuesto 35 % (− pago, + ahorro fiscal) | Flujo de caja libre | Acumulado |
|---|---|---|---|---|---|---|---|
| 0 | — | — | — | — | — | -4.400,0 | -4.400,0 |
| 1 | 213,6 | -256,5 | -503,5 | -546,4 | 191,2 | 148,4 | -4.251,6 |
| 2 | 427,2 | -256,5 | -503,5 | -332,8 | 116,5 | 287,2 | -3.964,4 |
| 3 | 427,2 | -256,5 | -503,5 | -332,8 | 116,5 | 287,2 | -3.677,2 |
| 4 | 427,2 | -256,5 | -503,5 | -332,8 | 116,5 | 287,2 | -3.390,0 |
| 5 | 427,2 | -256,5 | -503,5 | -332,8 | 116,5 | 287,2 | -3.102,8 |
| 6 | 427,2 | -256,5 | -376,5 | -205,7 | 72,0 | 242,7 | -2.860,0 |
| 7 | 427,2 | -256,5 | -376,5 | -205,7 | 72,0 | 242,7 | -2.617,3 |
| 8 | 427,2 | -256,5 | -376,5 | -205,7 | 72,0 | 242,7 | -2.374,5 |
| 9 | 427,2 | -256,5 | -376,5 | -205,7 | 72,0 | 242,7 | -2.131,8 |
| 10 | 427,2 | -256,5 | -376,5 | -205,7 | 72,0 | 242,7 | -1.889,0 |

**Indicadores pesimistas:** VPN (18 %) = **-3.287,7 M COP** · TIR = **negativa (-9,1 %)** · la inversión **no se recupera** en el horizonte (flujo acumulado al año 10 = -1.889,0 M COP).

Una utilidad antes de impuestos negativa genera un "impuesto negativo": es el ahorro fiscal que la empresa obtiene en el resto de su operación, que es rentable. Es la práctica estándar en la evaluación incremental.

## 8.2 Escenario esperado (M COP)

| Año | Beneficios | OPEX | Depreciación | Utilidad antes de impuestos | Impuesto 35 % (− pago, + ahorro fiscal) | Flujo de caja libre | Acumulado |
|---|---|---|---|---|---|---|---|
| 0 | — | — | — | — | — | -2.672,9 | -2.672,9 |
| 1 | 971,3 | -194,6 | -309,3 | 467,3 | -163,6 | 613,1 | -2.059,8 |
| 2 | 1.295,1 | -194,6 | -309,3 | 791,1 | -276,9 | 823,5 | -1.236,3 |
| 3 | 1.295,1 | -194,6 | -309,3 | 791,1 | -276,9 | 823,5 | -412,7 |
| 4 | 1.295,1 | -194,6 | -309,3 | 791,1 | -276,9 | 823,5 | 410,8 |
| 5 | 1.295,1 | -194,6 | -309,3 | 791,1 | -276,9 | 823,5 | 1.234,4 |
| 6 | 1.295,1 | -194,6 | -225,3 | 875,2 | -306,3 | 794,1 | 2.028,5 |
| 7 | 1.295,1 | -194,6 | -225,3 | 875,2 | -306,3 | 794,1 | 2.822,6 |
| 8 | 1.295,1 | -194,6 | -225,3 | 875,2 | -306,3 | 794,1 | 3.616,7 |
| 9 | 1.295,1 | -194,6 | -225,3 | 875,2 | -306,3 | 794,1 | 4.410,8 |
| 10 | 1.295,1 | -194,6 | -225,3 | 875,2 | -306,3 | 1.019,4 (incluye salvamento) | 5.430,2 |

**Indicadores esperados:** VPN (14 %) = **1.446,5 M COP** · TIR = **26,1 %** · recuperación simple = **3,5 años** · recuperación descontada = **5,1 años**.

---

# 9. Análisis de sensibilidad (riesgos económicos)

## 9.1 Qué tanto mejora el VPN pesimista cada supuesto

Partiendo del escenario pesimista, se cambia **un solo** supuesto a su valor esperado:

| Supuesto que se cambia | Mejora del VPN (M COP) | VPN resultante (M COP) |
|---|---|---|
| Ventas adicionales 0 % → 5 % (margen 25 %) | +1.039 | -2.249 |
| TRM 3.900 → 3.250 | +600 | -2.688 |
| IVA y arancel recuperables (Art. 258-1 ET, arancel 0 %) | +549 | -2.738 |
| Rendimiento quesero +0,3 % → +1,0 % | +524 | -2.764 |
| Sobrepeso −0,5 → −1,0 pt | +374 | -2.914 |
| Celda robotizada USD 220k → 170k | +370 | -2.917 |
| Contingencia 15 % → 10 % y 9 → 7 meses | +287 | -3.000 |
| Rechazos −0,25 → −0,5 pt | +187 | -3.101 |
| Tasa de descuento 18 % → 14 % | +185 | -3.103 |
| Reducción de operarios 4 → 6 | +172 | -3.115 |
| Arranque año 1 50 % → 75 % y salvamento 10 % | +131 | -3.157 |
| Mantenimiento 5 %/7 % → 3 %/5 % | +96 | -3.192 |

Ningún cambio individual hace viable el peor caso. Los cuatro que más pesan son ventas adicionales, TRM, recuperación del IVA y rendimiento quesero. Dos de ellos son de proceso y dos tributarios o cambiarios.

## 9.2 Multiplicador de beneficios

| Beneficios × | VPN pesimista (M COP) | VPN esperado (M COP) |
|---|---|---|
| 0,50 | -3.853 | -657 |
| 0,66 | -3.672 | 16 |
| 0,80 | -3.514 | 605 |
| 1,00 | -3.288 | 1.446 |
| 1,50 | -2.723 | 3.550 |
| 2,00 | -2.157 | 5.653 |
| 3,00 | -1.027 | 9.859 |
| 3,91 | 2 | 13.687 |

- **Punto de equilibrio pesimista:** beneficios ≥ 3,91 × lo estimado ≈ 1.670 M COP/año.
- **Punto de equilibrio esperado:** beneficios ≥ 0,66 × lo estimado ≈ 850 M COP/año. Es decir, el caso esperado resiste una caída de beneficios de 34 %.

## 9.3 Efecto de la celda robotizada (pesimista)

| Variante pesimista | Precio (M COP) | Beneficios (M COP/año) | OPEX (M COP/año) | VPN (M COP) |
|---|---|---|---|---|
| Con celda | 4.400 | 427 | 256 | -3.288 |
| Sin celda | 2.674 | 297 | 156 | -1.883 |
| Aporte de la celda | 1.726 | 130 | 101 | -1.404 |

Con un costo de operario de ≈ 2,7 M COP/mes, la celda ahorra 130 M COP/año, pero agrega 101 M COP/año de mantenimiento y energía. Su flujo neto anual es casi nulo frente a una inversión de 1.726 M COP. Para justificarla hay que sumar beneficios no monetarios o difíciles de medir: lesiones por carga repetitiva evitadas, continuidad sin rotación de personal, trazabilidad por estiba y velocidad sostenida en tres turnos.

---

# 10. Flujo de caja de ejecución (perspectiva del integrador)

## 10.1 Hitos de cobro

| Hito | Pesimista | Esperado |
|---|---|---|
| Anticipo a la firma | 20 % en el mes 1 | 30 % en el mes 1 |
| Equipos en sitio | 30 % en el mes 6 | 40 % en el mes 4 |
| Recibo a satisfacción (SAT) | 40 % en el mes 10 (30 días después del cierre) | 20 % en el mes 8 |
| Retención de garantía | 10 % en el mes 13 | 10 % en el mes 10 |

Pagos a proveedores (`ASSUMED`): equipos con 50 % al ordenar (mes 2) y 50 % antes del despacho (mes 4); celda con 40/40/20 (meses 2, 5 y 8); nacionalización en el mes 5; licencias en el mes 3; instalación en 40/40/20 (meses 6 a 8); contingencia repartida entre los meses 5 y 9.

## 10.2 Flujo mensual — escenario pesimista (M COP)

| Mes | Cobros | Salarios | Gastos generales | Equipos | Celda | Nacionalización | Software | Instalación | Contingencia | Intereses | Flujo neto | Saldo acumulado | Curva S (% del costo) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 880,0 | 41,0 | 12,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 827,0 | 827,0 | 1 % |
| 2 | 0,0 | 41,0 | 12,0 | 425,4 | 370,7 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | -849,1 | -22,1 | 24 % |
| 3 | 0,0 | 41,0 | 12,0 | 0,0 | 0,0 | 0,0 | 346,7 | 0,0 | 0,0 | 0,4 | -400,1 | -422,2 | 34 % |
| 4 | 0,0 | 41,0 | 12,0 | 425,4 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 8,0 | -486,4 | -908,6 | 47 % |
| 5 | 0,0 | 41,0 | 12,0 | 0,0 | 370,7 | 479,0 | 0,0 | 0,0 | 99,8 | 17,3 | -1.019,8 | -1.928,4 | 73 % |
| 6 | 1.320,0 | 41,0 | 12,0 | 0,0 | 0,0 | 0,0 | 0,0 | 98,7 | 99,8 | 36,6 | 1.031,8 | -896,6 | 79 % |
| 7 | 0,0 | 41,0 | 12,0 | 0,0 | 0,0 | 0,0 | 0,0 | 98,7 | 99,8 | 17,0 | -268,6 | -1.165,1 | 86 % |
| 8 | 0,0 | 41,0 | 12,0 | 0,0 | 185,3 | 0,0 | 0,0 | 49,4 | 99,8 | 22,1 | -409,7 | -1.574,8 | 96 % |
| 9 | 0,0 | 41,0 | 12,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 99,8 | 29,9 | -182,7 | -1.757,5 | 100 % |
| 10 | 1.760,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 33,4 | 1.726,6 | -30,9 | 100 % |
| 11 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,6 | -0,6 | -31,5 | 100 % |
| 12 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,6 | -0,6 | -32,1 | 100 % |
| 13 | 440,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,6 | 439,4 | 407,3 | 100 % |

**Resultados pesimistas para el integrador:**
- **Necesidad máxima de financiación:** 1.928 M COP en el mes 5, cuando coinciden la nacionalización, el segundo pago de la celda y la contingencia, y todavía no llega el cobro de equipos en sitio.
- **Costo financiero:** 167 M COP, que consume el 29 % del margen.
- **Utilidad final:** 407 M COP (9,3 % del precio).
- **Lección:** con un anticipo de solo 20 % y pagos tardíos, la empresa integradora necesita una línea de crédito o una negociación de hitos. Subir el anticipo al 30–40 % o cobrar contra la orden de compra de equipos reduce casi toda la necesidad de financiación.

## 10.3 Escenario esperado (resumen)

| Mes | Saldo acumulado (M COP) | Curva S (% del costo) |
|---|---|---|
| 1 | 750,9 | 2 % |
| 2 | 106,7 | 30 % |
| 3 | -187,1 | 43 % |
| 4 | 473,0 | 60 % |
| 5 | 86,8 | 77 % |
| 6 | -226,5 | 90 % |
| 7 | -424,8 | 98 % |
| 8 | 65,4 | 100 % |
| 9 | 65,4 | 100 % |
| 10 | 332,7 | 100 % |

Necesidad máxima de financiación: 425 M COP (mes 7) · intereses 16 M COP · utilidad 333 M COP.

---

# 11. Oferta comercial preliminar

| Elemento | Propuesta |
|---|---|
| Alcance | Paquetes P1 a P9 y S1 a S6, con ingeniería, instalación, FAT/SAT, puesta en marcha, capacitación y documentación (repositorio, manuales, planos) |
| Precio | 2.673 M COP + IVA en condiciones esperadas. Se mantiene el precio pesimista de 4.400 M COP como techo con el dólar a 3.900 COP/USD y el IVA no recuperado |
| Forma de pago recomendada | 30 % anticipo · 40 % equipos en sitio · 20 % SAT · 10 % al cumplir 3 meses de garantía |
| Plazo | 7 meses (máximo 9) |
| Garantía | 12 meses sobre equipos e ingeniería |
| Validez de la oferta | 30 días (sujeta a la TRM y a cotizaciones formales) |
| Propuesta de valor | Corte de cuajada en el punto óptimo, trazabilidad lote a lote (Track & Trace), OEE en tiempo real y gemelo digital para validar recetas antes de producir |

---

# 12. Pendientes para pasar de preliminar a definitivo

- [ ] **Cotizaciones formales** con fecha y proveedor de P1–P9: Rockwell/distribuidor local, Endress+Hauser o similar, integrador ABB para la celda, Mettler-Toledo o similar para el checkweigher. La guía exige "evidencias de cotizaciones".
- [ ] **Cerrar las capas 8 a 10 de quesos** (lote, tiempos, capacidades, personal) y confirmar o reemplazar la base productiva de la sección 3.
- [ ] **Reemplazar los porcentajes de mejora** de la sección 7 por los resultados del Módulo 2 (KPI base frente a propuesto y Tecnomatix).
- [ ] **Construir la EDT y el cronograma** para fijar la duración real y los hitos de cobro.
- [ ] **Confirmar con el profesor Méndez** si piden los dos flujos de caja y si aceptan el tratamiento del IVA y la tasa de descuento.
- [ ] **Definir la ubicación de la celda robotizada** y su justificación no monetaria.
- [ ] **Confirmar con la línea de quesos** los precios de venta y el margen de contribución.

---

# Fuentes

- Salario mínimo 2026 (1.750.905 COP + 249.095 de auxilio): https://newsroom.rcnradio.com/colombia/salario-minimo-2026-en-colombia-en-cuanto-quedo-tras-decision-del-consejo-de-estado
- TRM histórica (9-oct-2026: 3.218,75 COP/USD): https://dolar.wilkinsonpc.com.co/2026-10-09
- Guía salarial Colombia 2026 (profesionales junior y semi-senior): https://www.tributi.com/blog/finanzas-personales/post/cuanto-deberias-ganar-en-colombia-en-2026-guia-salarial
- Precios de Ignition (suites y soporte): https://inductiveautomation.com/pricing/ignition
- Precios de Sepasoft MES: https://www.sepasoft.com/?p=36010
- Rangos de precio de sistemas de paletizado robotizado: https://img0.medicalsearch.com.au/robotic-palletising-system-prices-and-buying-guide/f/26241
- Rangos de precio de checkweighers: https://img0.hospitalityhub.com.au/how-much-do-checkweighers-cost-a-practical-price-and-cost-guide-for-australia/f/27456
- Rendimiento quesero (regla general ≈ 10 L/kg): https://www.cheesescience.org/yield.html
- Alpina, resultados primer semestre 2025 (EBITDA ≈ 15,5 % de ventas): https://www.valoraanalitik.com/?p=491388
- Precio de queso mozzarella 250 g: https://www.exito.com/queso-mozarella-x-250-gr-366529/p
- Precio de queso madurado Alpina 240 g: https://www.farmatodo.com.co/producto/273550569-queso-sabana-alpina--tajado-x-240-gr
- Caso de automatización de planta de quesos (productividad +20 %, errores de operador −95 %): https://www.rockwellautomation.com/en-au/company/news/case-studies/dairy-modernizes--and-captures-competitive-edge.html
- Documento base de la línea: `Linea_de_quesos.md` (12 capas)
