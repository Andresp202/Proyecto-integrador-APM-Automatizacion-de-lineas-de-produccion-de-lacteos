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
| Precio de la solución (inversión del cliente, año 0) | 4.604 | 2.807 | M COP |
| Equivalente en dólares | 1.181 | 864 | miles USD |
| Beneficios anuales en régimen | 471 | 1.457 | M COP/año |
| Costos de operación adicionales (OPEX) | 262 | 197 | M COP/año |
| VPN a 10 años | **-3.359** | **1.857** | M COP |
| TIR | < 0 (negativa) | 28,6 % | % E.A. |
| Periodo de recuperación simple | No se recupera en 10 años | 3,3 años | años |
| Periodo de recuperación descontado | No se recupera | 4,6 años | años |
| Utilidad del integrador (margen menos costo financiero) | 424 | 349 | M COP |
| Necesidad máxima de financiación del integrador | 2.033 | 445 | M COP |

**Lectura rápida:**
1. **En el peor caso el proyecto no es viable para el cliente.** Los beneficios tendrían que ser **3,7 veces** mayores para que el VPN llegue a cero. Ningún factor por sí solo lo vuelve viable (sección 9).
2. **En el escenario esperado sí es viable:** TIR de 29 % y recuperación en 3,3 años. Sigue siendo viable aunque los beneficios caigan hasta el 61 % de lo estimado.
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
| TRM | 3.900 COP/USD | 3.250 COP/USD | `PUBLIC`: TRM del 9-oct-2026 = 3.218,75; 1-ene-2026 = 3.757,08; 9-oct-2025 = 3.879,80. El pesimista toma el máximo del último año redondeado |
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

Valores tomados de la versión vigente de las 12 capas de quesos (`Modulos/Modulo 0/Linea_de_quesos.md`, capas 8 a 10) y del modelo de indicadores. Los precios de venta y el margen son supuestos de este documento.

| Parámetro | Q-PRD-001 Campesino | Q-PRD-002 Mozzarella | Q-PRD-003 Sopó | Origen |
|---|---|---|---|---|
| Presentación | Cuña 250 g | Bloque 250 g | Cuña 180 g | `PUBLIC` (capa 1) |
| Leche por lote (tina) | 4.500 kg | 4.500 kg | 4.500 kg | `ASSUMED` (capa 9, Q-CAP-001; 3 tinas de 5.000 L) |
| kg de leche por kg de queso | 8,3 | 9,1 | 10,0 | `ASSUMED` (capa 9, Q-CAP-011: 0,12 / 0,11 / 0,10 kg/kg) |
| Rendimiento | 12,0 % | 11,0 % | 10,0 % | `CALCULATED` |
| Producto por lote | 540 kg | 495 kg | 450 kg | `CALCULATED` |
| Lotes por día | 3 | 2 | 2 | `ASSUMED` (capa 9: 7 lotes/día, 3 tinas, 2 turnos) |
| Producción diaria | 1.620 kg · 6.480 un | 990 kg · 3.960 un | 900 kg · 5.000 un | `CALCULATED` |
| Precio al público (PVP) por unidad | 8.000 COP | 11.300 COP | 15.000 COP | `ASSUMED` / `REFERENCE` (mozzarella 250 g a 11.300 COP en Éxito; queso madurado Alpina 240 g a 20.100 COP en Farmatodo) |
| Precio neto al fabricante (PVP × 0,70) | 22.400 COP/kg | 31.640 COP/kg | 58.333 COP/kg | `ASSUMED` (descuenta margen del canal e impuestos, ≈ 30 %) |
| Ventas anuales | 10.886 M COP | 9.397 M COP | 15.750 M COP | `CALCULATED` |

| Total de la línea | Valor | Origen |
|---|---|---|
| Leche procesada | 31.500 kg/día | `CALCULATED` |
| Producción | 3.510 kg/día · 1.053.000 kg/año | `CALCULATED` |
| Ventas | 36.033 M COP/año | `CALCULATED` |
| Precio neto promedio | 34.220 COP/kg | `CALCULATED` |
| Margen de contribución (precio − costos variables) | 20 % pesimista · 25 % esperado | `ASSUMED`. Referencia pública: Alpina reportó un margen EBITDA ≈ 15,5 % en el primer semestre de 2025 (`PUBLIC`, Valora Analitik). El margen de contribución es mayor que el EBITDA porque este último ya descuenta los costos fijos |
| Personal del escenario base | 10 personas por turno (recepción y tratamiento térmico 1, elaboración 3, empaque 3, calidad 1, supervisor 1, limpieza 1) | `ASSUMED` (capa 10) |

---

# 4. Escenario propuesto — paquetes de automatización

| Paquete | Alcance | Operaciones / equipos de quesos | Beneficio que habilita |
|---|---|---|---|
| P1 | Automatización de las 3 tinas: RTD, pH en línea, sensor óptico de coagulación, dosificación automática de cultivo, cuajo y CaCl₂, válvulas de camisa y desuerado, variadores de lira y agitador | Q-OP-006 a Q-OP-010 · Q-EQ-005 a Q-EQ-008 | Rendimiento quesero (corte en el punto óptimo), menos rechazos, recetas ISA-88 |
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
| P1 | Automatización de 3 tinas queseras (RTD, pH en línea, sensor óptico de coagulación, dosificación de cultivo/cuajo/CaCl2, válvulas de camisa y desuerado, variadores de lira/agitador) | 3 | 26.000 | 78.000 | 417,1 | `ASSUMED` (precio de referencia, sin cotización) |
| P2 | Integración del pasteurizador al PLC (RTD, caudalímetro, señal de FDV) | 1 | 8.000 | 8.000 | 42,8 | `ASSUMED` |
| P3 | Prensado con control de presión y tiempo (transmisores, válvulas proporcionales) | 1 | 15.000 | 15.000 | 80,2 | `ASSUMED` |
| P4 | Control de temperatura de la hiladora de mozzarella | 1 | 6.000 | 6.000 | 32,1 | `ASSUMED` |
| P5 | Monitoreo y control de cámara de maduración (T y HR) | 1 | 6.000 | 6.000 | 32,1 | `ASSUMED` |
| P6a | Báscula de control (checkweigher) con rechazador | 1 | 30.000 | 30.000 | 160,4 | `REFERENCE` (rango medio de checkweighers industriales con rechazo: AUD 25–60 mil) |
| P6b | Impresora-etiquetadora print & apply con lote y vencimiento | 1 | 15.000 | 15.000 | 80,2 | `ASSUMED` |
| P7 | Celda robotizada de encajonado y paletizado llave en mano (robot, gripper, transportadores, cerramiento y seguridad) | 1 | 220.000 | 220.000 | 1.176,4 | `REFERENCE` (celdas de paletizado de nivel de entrada: AUD 190–250 mil, más gripper, transportadores y seguridad) / `ASSUMED` |
| P8 | Tablero de control: PLC CompactLogix 5380, E/S distribuidas, HMI local, gabinete inoxidable | 1 | 45.000 | 45.000 | 240,6 | `ASSUMED` |
| P9 | Red OT/IT: switches administrables, fibra, firewall, servidor industrial, UPS | 1 | 25.000 | 25.000 | 133,7 | `ASSUMED` |
| | **Total hardware** | | | **448.000** | **2.395,5** | `CALCULATED` |

Desglose de la nacionalización pesimista (USD): CIF 483.840 · arancel 24.192 · agencia 9.677 · IVA 96.526.

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
| Hardware nacionalizado | 2.395,5 | 1.424,9 |
| Software | 346,7 | 242,8 |
| Instalación eléctrica y mecánica | 262,1 | 194,0 |
| Ingeniería (salarios) | 369,0 | 287,0 |
| Gastos generales | 108,0 | 70,0 |
| **Costo directo** | **3.481,3** | **2.218,7** |
| Contingencia | 522,2 | 221,9 |
| **Costo total del proyecto** | **4.003,5** | **2.440,6** |
| Margen del integrador | 600,5 | 366,1 |
| **Precio de la oferta = CAPEX del cliente** | **4.604,0** | **2.806,7** |
| Participación de la celda robotizada en el precio | 1.726,0 (37 %) | — |

---

# 6. Costos de operación adicionales (OPEX)

| Concepto | Pesimista (M COP/año) | Esperado (M COP/año) | Base de cálculo | Origen |
|---|---|---|---|---|
| Mantenimiento de equipos nuevos | 104,5 | 49,9 | Pesimista: 5 % del FOB de equipos y 7 % de la celda. Esperado: 3 % y 5 % | `REFERENCE` (robots: 5–10 % anual) / `ASSUMED` |
| Soporte anual de software (TotalCare) | 58,3 | 48,6 | 20 % del precio de lista | `PUBLIC` |
| Técnico de automatización adicional | 49,8 | 49,8 | 1 técnico, 3,0 M COP/mes + prestaciones | `ASSUMED` |
| Energía de la celda y de los equipos nuevos | 49,0 | 49,0 | 12 kW × 16 h × 300 días × 850 COP/kWh | `ASSUMED` |
| **Total OPEX** | **261,6** | **197,2** | | `CALCULATED` |

---

# 7. Beneficios anuales (escenario propuesto frente al base)

| Beneficio | Supuesto pesimista | Supuesto esperado | Pesimista (M COP/año) | Esperado (M COP/año) | Cálculo |
|---|---|---|---|---|---|
| Menos operarios | 4 (solo la celda robotizada, 2 por turno) | 6 (celda + tinas automáticas) | 130,3 | 195,5 | n × 2.715.497 COP/mes × 12 |
| Menos sobrepeso (*giveaway*) con checkweigher y prensado controlado | −0,5 pt | −1,0 pt | 162,2 | 324,3 | pt × 1.053.000 kg × precio neto × 0,90 |
| Mayor rendimiento quesero (corte en el punto óptimo, dosificación exacta) | +0,3 % | +1,0 % | 97,3 | 324,3 | Igual |
| Menos lotes rechazados o reprocesados | −0,25 pt | −0,5 pt | 81,1 | 162,2 | Igual |
| Ventas adicionales por mayor OEE | 0 % (sin demanda adicional) | +5 % de volumen | 0,0 | 450,4 | % × ventas × margen de contribución (20 % / 25 %) |
| **Total** | | | **470,9** | **1.456,7** | `CALCULATED` |

**Por qué el producto recuperado se valora al 90 % del precio:** el queso que deja de regalarse en sobrepeso o de perderse en rechazos ya consumió leche. Venderlo solo agrega empaque y energía (≈ 10 %, `ASSUMED`). Las ventas adicionales, en cambio, requieren más leche, por eso se valoran solo con el margen de contribución.

Todos los porcentajes de mejora son `ASSUMED` y deben reemplazarse por la comparación de KPI del Módulo 2 (OEE, rechazos, rendimiento) y por la simulación en Tecnomatix.

---

# 8. Flujo de caja de la inversión (perspectiva del cliente)

## 8.1 Escenario pesimista (M COP)

| Año | Beneficios | OPEX | Depreciación | Utilidad antes de impuestos | Impuesto (35 %) | Flujo de caja libre | Acumulado |
|---|---|---|---|---|---|---|---|
| 0 | — | — | — | — | — | -4.604,0 | -4.604,0 |
| 1 | 235,4 | -261,6 | -523,9 | -550,0 | 192,5 | 166,4 | -4.437,6 |
| 2 | 470,9 | -261,6 | -523,9 | -314,6 | 110,1 | 319,4 | -4.118,2 |
| 3 | 470,9 | -261,6 | -523,9 | -314,6 | 110,1 | 319,4 | -3.798,7 |
| 4 | 470,9 | -261,6 | -523,9 | -314,6 | 110,1 | 319,4 | -3.479,3 |
| 5 | 470,9 | -261,6 | -523,9 | -314,6 | 110,1 | 319,4 | -3.159,9 |
| 6 | 470,9 | -261,6 | -396,9 | -187,6 | 65,6 | 275,0 | -2.884,9 |
| 7 | 470,9 | -261,6 | -396,9 | -187,6 | 65,6 | 275,0 | -2.610,0 |
| 8 | 470,9 | -261,6 | -396,9 | -187,6 | 65,6 | 275,0 | -2.335,0 |
| 9 | 470,9 | -261,6 | -396,9 | -187,6 | 65,6 | 275,0 | -2.060,1 |
| 10 | 470,9 | -261,6 | -396,9 | -187,6 | 65,6 | 275,0 | -1.785,1 |

**Indicadores pesimistas:** VPN (18 %) = **-3.358,9 M COP** · TIR = **negativa (-8,0 %)** · la inversión **no se recupera** en el horizonte (flujo acumulado al año 10 = -1.785,1 M COP).

Una utilidad antes de impuestos negativa genera un "impuesto negativo": es el ahorro fiscal que la empresa obtiene en el resto de su operación, que es rentable. Es la práctica estándar en la evaluación incremental.

## 8.2 Escenario esperado (M COP)

| Año | Beneficios | OPEX | Depreciación | Utilidad antes de impuestos | Impuesto (35 %) | Flujo de caja libre | Acumulado |
|---|---|---|---|---|---|---|---|
| 0 | — | — | — | — | — | -2.806,7 | -2.806,7 |
| 1 | 1.092,5 | -197,2 | -322,7 | 572,6 | -200,4 | 694,9 | -2.111,8 |
| 2 | 1.456,7 | -197,2 | -322,7 | 936,8 | -327,9 | 931,6 | -1.180,1 |
| 3 | 1.456,7 | -197,2 | -322,7 | 936,8 | -327,9 | 931,6 | -248,5 |
| 4 | 1.456,7 | -197,2 | -322,7 | 936,8 | -327,9 | 931,6 | 683,1 |
| 5 | 1.456,7 | -197,2 | -322,7 | 936,8 | -327,9 | 931,6 | 1.614,7 |
| 6 | 1.456,7 | -197,2 | -238,6 | 1.020,9 | -357,3 | 902,2 | 2.516,9 |
| 7 | 1.456,7 | -197,2 | -238,6 | 1.020,9 | -357,3 | 902,2 | 3.419,2 |
| 8 | 1.456,7 | -197,2 | -238,6 | 1.020,9 | -357,3 | 902,2 | 4.321,4 |
| 9 | 1.456,7 | -197,2 | -238,6 | 1.020,9 | -357,3 | 902,2 | 5.223,6 |
| 10 | 1.456,7 | -197,2 | -238,6 | 1.020,9 | -357,3 | 1.140,8 (incluye salvamento) | 6.364,4 |

**Indicadores esperados:** VPN (14 %) = **1.857,1 M COP** · TIR = **28,6 %** · recuperación simple = **3,3 años** · recuperación descontada = **4,6 años**.

---

# 9. Análisis de sensibilidad (riesgos económicos)

## 9.1 Qué tanto mejora el VPN pesimista cada supuesto

Partiendo del escenario pesimista, se cambia **un solo** supuesto a su valor esperado:

| Supuesto que se cambia | Mejora del VPN (M COP) | VPN resultante (M COP) |
|---|---|---|
| Ventas adicionales 0 % → 5 % (margen 25 %) | +1.192 | -2.167 |
| TRM 3.900 → 3.250 | +631 | -2.728 |
| Rendimiento quesero +0,3 % → +1,0 % | +601 | -2.758 |
| IVA y arancel recuperables (Art. 258-1 ET, arancel 0 %) | +580 | -2.779 |
| Sobrepeso −0,5 → −1,0 pt | +429 | -2.930 |
| Celda robotizada USD 220k → 170k | +370 | -2.989 |
| Contingencia 15 % → 10 % y 9 → 7 meses | +295 | -3.064 |
| Rechazos −0,25 → −0,5 pt | +215 | -3.144 |
| Tasa de descuento 18 % → 14 % | +208 | -3.151 |
| Reducción de operarios 4 → 6 | +172 | -3.187 |
| Arranque año 1 50 % → 75 % y salvamento 10 % | +141 | -3.218 |
| Mantenimiento 5 %/7 % → 3 %/5 % | +102 | -3.257 |

Ningún cambio individual hace viable el peor caso. Los cuatro que más pesan son ventas adicionales, TRM, recuperación del IVA y rendimiento quesero. Dos de ellos son de proceso y dos tributarios o cambiarios.

## 9.2 Multiplicador de beneficios

| Beneficios × | VPN pesimista (M COP) | VPN esperado (M COP) |
|---|---|---|
| 0,50 | -3.982 | -509 |
| 0,66 | -3.783 | 248 |
| 0,80 | -3.608 | 911 |
| 1,00 | -3.359 | 1.857 |
| 1,50 | -2.736 | 4.223 |
| 2,00 | -2.113 | 6.588 |
| 3,00 | -867 | 11.320 |
| 3,70 | 5 | 14.631 |

- **Punto de equilibrio pesimista:** beneficios ≥ 3,70 × lo estimado ≈ 1.740 M COP/año.
- **Punto de equilibrio esperado:** beneficios ≥ 0,61 × lo estimado ≈ 885 M COP/año. Es decir, el caso esperado resiste una caída de beneficios de 39 %.

## 9.3 Efecto de la celda robotizada (pesimista)

| Variante pesimista | Precio (M COP) | Beneficios (M COP/año) | OPEX (M COP/año) | VPN (M COP) |
|---|---|---|---|---|
| Con celda | 4.604 | 471 | 262 | -3.359 |
| Sin celda | 2.878 | 341 | 161 | -1.955 |
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
| 1 | 920,8 | 41,0 | 12,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 867,8 | 867,8 | 1 % |
| 2 | 0,0 | 41,0 | 12,0 | 480,2 | 370,7 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | -903,8 | -36,0 | 24 % |
| 3 | 0,0 | 41,0 | 12,0 | 0,0 | 0,0 | 0,0 | 346,7 | 0,0 | 0,0 | 0,7 | -400,4 | -436,4 | 34 % |
| 4 | 0,0 | 41,0 | 12,0 | 480,2 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 8,3 | -541,5 | -977,9 | 47 % |
| 5 | 0,0 | 41,0 | 12,0 | 0,0 | 370,7 | 508,5 | 0,0 | 0,0 | 104,4 | 18,6 | -1.055,2 | -2.033,1 | 73 % |
| 6 | 1.381,2 | 41,0 | 12,0 | 0,0 | 0,0 | 0,0 | 0,0 | 104,8 | 104,4 | 38,6 | 1.080,3 | -952,8 | 80 % |
| 7 | 0,0 | 41,0 | 12,0 | 0,0 | 0,0 | 0,0 | 0,0 | 104,8 | 104,4 | 18,1 | -280,4 | -1.233,1 | 86 % |
| 8 | 0,0 | 41,0 | 12,0 | 0,0 | 185,3 | 0,0 | 0,0 | 52,4 | 104,4 | 23,4 | -418,6 | -1.651,8 | 96 % |
| 9 | 0,0 | 41,0 | 12,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 104,4 | 31,4 | -188,8 | -1.840,6 | 100 % |
| 10 | 1.841,6 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 35,0 | 1.806,6 | -33,9 | 100 % |
| 11 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,6 | -0,6 | -34,6 | 100 % |
| 12 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,7 | -0,7 | -35,3 | 100 % |
| 13 | 460,4 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,0 | 0,7 | 459,7 | 424,5 | 100 % |

**Resultados pesimistas para el integrador:**
- **Necesidad máxima de financiación:** 2.033 M COP en el mes 5, cuando coinciden la nacionalización, el segundo pago de la celda y la contingencia, y todavía no llega el cobro de equipos en sitio.
- **Costo financiero:** 176 M COP, que consume el 29 % del margen.
- **Utilidad final:** 424 M COP (9,2 % del precio).
- **Lección:** con un anticipo de solo 20 % y pagos tardíos, la empresa integradora necesita una línea de crédito o una negociación de hitos. Subir el anticipo al 30–40 % o cobrar contra la orden de compra de equipos reduce casi toda la necesidad de financiación.

## 10.3 Escenario esperado (resumen)

| Mes | Saldo acumulado (M COP) | Curva S (% del costo) |
|---|---|---|
| 1 | 791,0 | 2 % |
| 2 | 101,2 | 30 % |
| 3 | -192,6 | 42 % |
| 4 | 475,3 | 61 % |
| 5 | 83,7 | 77 % |
| 6 | -238,2 | 90 % |
| 7 | -445,3 | 98 % |
| 8 | 68,8 | 100 % |
| 9 | 68,8 | 100 % |
| 10 | 349,4 | 100 % |

Necesidad máxima de financiación: 445 M COP (mes 7) · intereses 17 M COP · utilidad 349 M COP.

---

# 11. Oferta comercial preliminar

| Elemento | Propuesta |
|---|---|
| Alcance | Paquetes P1 a P9 y S1 a S6, con ingeniería, instalación, FAT/SAT, puesta en marcha, capacitación y documentación (repositorio, manuales, planos) |
| Precio | 2.807 M COP + IVA en condiciones esperadas. Se mantiene el precio pesimista de 4.604 M COP como techo con el dólar a 3.900 COP/USD y el IVA no recuperado |
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
