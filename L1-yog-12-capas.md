# Línea 1 — Yogures y leches fermentadas (código `Y`)
## Caracterización completa — 12 capas

**Última actualización:** ver historial de commits del repositorio

**Leyenda de origen de los datos**

| Etiqueta | Significado |
|---|---|
| `PUBLIC` | Dato público verificable (cifra oficial, normativa, ficha técnica, portafolio real) |
| `REFERENCE` | Dato técnico de literatura, normativa internacional o equipos industriales reales, no específico de Alpina |
| `ASSUMED` | Supuesto del equipo, justificado, para poder avanzar sin dato público |
| `CALCULATED` | Derivado matemáticamente de otros datos de este documento |
| `PROPOSED` | Elemento propuesto por el proyecto (escenario futuro) |

**Unidad principal de producción:** kg/lote (unidades/lote como dato complementario).

---

## Capa 1 — Contexto (productos y referencias)

| ID | Producto | Diferenciador clave | Origen |
|---|---|---|---|
| Y-PRD-001 | Yogur semidescremado sabor fresa con trozos de fruta, vaso 150 g  | Yogur batido: fermentación termófila en tanque, rompimiento del coágulo y mezcla con preparación de fruta; estabilizantes, azúcar y probióticos | `PUBLIC` (producto, 150 g, ingredientes) |
| Y-PRD-002 | Yogur griego natural, vaso 150 g  | Leche fermentada concentrada: etapa exclusiva de concentración (ultrafiltración) tras la fermentación; ≈ 2,7 kg de base por kg de producto; genera suero ácido como subproducto; sin azúcar ni estabilizantes | `PUBLIC` (producto, 150 g) / `ASSUMED` (sabor natural) |
| Y-PRD-003 | Kumis dulce entero, botella 200 g  | Leche fermentada mesófila (*Lactococcus lactis*), fermentación más larga y a menor temperatura; producto semilíquido, envasado en botella en lugar de vaso | `PUBLIC` (producto, 200 g) / `ASSUMED` (envase botella) |


**Mezcla de producción (en masa):** Y-PRD-001 50 % · Y-PRD-002 20 % · Y-PRD-003 30 % (`ASSUMED`)

### Requisitos normativos por referencia

| Requisito | Y-PRD-001 Yogur semidescremado | Y-PRD-002 Yogur griego | Y-PRD-003 Kumis entero | Origen |
|---|---|---|---|---|
| Cultivo obligatorio | *S. thermophilus* + *L. delbrueckii* subsp. *bulgaricus* | *S. thermophilus* + *L. delbrueckii* subsp. *bulgaricus* | *Streptococcus* (hoy *Lactococcus*) *lactis* o *cremoris* | `PUBLIC` (Res. 2310/1986, arts. 11 y 14) |
| Materia grasa | ≥ 1,5 % m/m | Sin requisito propio de concentrado; < 15 % (yogur) | ≥ 2,5 % m/m | `PUBLIC` (Res. 2310 art. 13; ficha ICBF) / `REFERENCE` (Codex 243) |
| Sólidos lácteos no grasos | ≥ 7,0 % m/m | ≥ 7,0 % m/m | ≥ 7,0 % m/m | `PUBLIC` (Res. 2310 art. 13) |
| Proteína láctea | ≥ 2,6 % m/m | **≥ 5,6 %** (leche fermentada concentrada) | ≥ 2,6 % m/m | `PUBLIC` (NTC 805, ficha ICBF) / `REFERENCE` (Codex 243, secc. 2.2) |
| Acidez (ácido láctico) | 0,70–1,50 % m/m | 0,70–1,50 % m/m | 0,60–1,20 % m/m | `PUBLIC` (Res. 2310 arts. 13 y 16) |
| Fruta neta (si lleva preparación) | ≥ 3 % m/m | — | — | `PUBLIC` (Res. 2310 art. 20) |
| Cultivo viable en producto final | ≥ 10⁷ UFC/g | ≥ 10⁷ UFC/g | ≥ 10⁷ UFC/g | `REFERENCE` (Codex 243, secc. 3.3) |
| Proteína objetivo del diseño | — | 8 % | — | `ASSUMED` (por encima del mínimo de 5,6 %, en el rango comercial de 6–10 %) |
| Almacenamiento y vida útil | 4 °C · 15–21 días | 4 °C · 15–21 días | 4 °C · 15–21 días | `PUBLIC` (ficha técnica ICBF de yogur y kumis) |

**Nota:** a diferencia de la línea UHT, los tres productos requieren **cadena de frío** desde el envasado hasta el despacho y no pasan por cuarentena de esterilidad comercial.

---

## Capa 2 — Materias primas

### Ingredientes

| ID | Nombre | Unidad | Valor | Aplica a | Origen | Observaciones |
|---|---|---|---|---|---|---|
| Y-MP-001 | Leche cruda | % grasa tras estandarización | 1,5–2,0 (Y-PRD-001, 002) · 3,0 (Y-PRD-003) | Las 3 | `REFERENCE` / `ASSUMED` | Recurso compartido de planta (recepción `PL-EQ-001`). Se estandariza por encima de los mínimos legales |
| Y-MP-002 | Leche en polvo descremada | % m/m de la fórmula | 2,5 (Y-PRD-001) · 1,0 (Y-PRD-003) | Y-PRD-001, 003 | `PUBLIC` (en etiqueta) / `REFERENCE` (dosis) | Sube sólidos no grasos y firmeza del coágulo |
| Y-MP-003 | Azúcar | % m/m | 5,5 (Y-PRD-001, más el azúcar de la preparación de fruta) · 7,0 (Y-PRD-003) | Y-PRD-001, 003 | `ASSUMED` | Y-PRD-002 natural, sin azúcar |
| Y-MP-004 | Estabilizantes (almidón modificado, gelatina, pectina) | % m/m | 0,5 | Solo Y-PRD-001 | `PUBLIC` (en etiqueta) / `REFERENCE` (dosis; límite legal de gelificantes 0,5 %, Res. 2310 art. 19) | El griego obtiene la textura por concentración, no por aditivos |
| Y-MP-005 | Preparación de fresa con trozos | % m/m | 15 | Solo Y-PRD-001 | `PUBLIC` (en etiqueta) / `ASSUMED` (dosis) | Con ≈ 30–40 % de fruta, aporta 4,5–6 % de fruta neta (≥ 3 % legal) |
| Y-MP-006 | Aditivos menores (aroma de fresa, colorantes carmín y achiote, sucralosa) | % m/m | < 0,1 | Solo Y-PRD-001 | `PUBLIC` (en etiqueta) / `ASSUMED` (dosis) | Masa despreciable en el balance |
| Y-MP-007 | Cultivo termófilo de yogur (*S. thermophilus* + *L. bulgaricus*) | — | Dosis DVS según ficha del proveedor | Y-PRD-001, 002 | `PUBLIC` (cultivo) / `ASSUMED` (DVS) | Liofilizado o congelado de adición directa; masa despreciable |
| Y-MP-008 | Cultivo probiótico (*L. acidophilus*, *L. casei*) | — | Dosis DVS según ficha del proveedor | Solo Y-PRD-001 | `PUBLIC` (en etiqueta) | Diferencia el yogur saborizado |
| Y-MP-009 | Cultivo mesófilo de kumis (*Lactococcus lactis* subsp. *lactis* / *cremoris*) | — | Dosis DVS según ficha del proveedor | Solo Y-PRD-003 | `PUBLIC` (Res. 2310 art. 14) / `ASSUMED` (DVS) | Cultivo exclusivo del kumis |

### Fórmula base por 1.000 kg de producto terminado

| Ingrediente | Y-PRD-001 Yogur fresa (kg) | Y-PRD-002 Griego (kg) | Y-PRD-003 Kumis (kg) |
|---|---|---|---|
| Y-MP-001 Leche estandarizada | 765 | 2.700 | 920 |
| Y-MP-002 Leche en polvo descremada | 25 | — | 10 |
| Y-MP-003 Azúcar | 55 | — | 70 |
| Y-MP-004 Estabilizantes | 5 | — | — |
| Y-MP-005 Preparación de fresa | 150 | — | — |
| Y-MP-006 a 009 (cultivos y aditivos menores) | < 1 | < 1 | < 1 |
| **Total de entrada** | **1.000** | **2.700** | **1.000** |
| Subproducto Y-SUB-001 (suero ácido / permeado) | — | 1.700 | — |
| Origen | `ASSUMED` | `CALCULATED` | `ASSUMED` |

**Cálculo del griego (`CALCULATED`):** Tetra Pak reporta que 1.000 L de leche con 3 % de proteína rinden 300 L de concentrado con 10 % de proteína (3,3:1), o 500 L con 6 % (2:1). Interpolando para 8 % de proteína se obtienen ≈ 2,7 kg de base fermentada por kg de griego. Los 1.700 kg restantes salen como permeado ácido por cada 1.000 kg de producto. Este subproducto debe gestionarse (tanque, disposición o venta) y entra en los recursos de planta.

### Materiales de empaque

| ID | Nombre | Unidad | Valor por 1.000 kg | Aplica a | Origen | Observaciones |
|---|---|---|---|---|---|---|
| Y-MP-010 | Vaso termoformado impreso 150 g | unidades | 6.667 | Y-PRD-001, 002 | `CALCULATED` | 1.000 kg ÷ 0,150 kg |
| Y-MP-011 | Tapa de aluminio termosellable | unidades | 6.667 | Y-PRD-001, 002 | `CALCULATED` | Una por vaso |
| Y-MP-012 | Botella PEAD 200 g con tapa | unidades | 5.000 | Y-PRD-003 | `CALCULATED` / `ASSUMED` (material) | 1.000 kg ÷ 0,200 kg |
| Y-MP-013 | Etiqueta tipo manga termoencogible | unidades | 5.000 | Y-PRD-003 | `ASSUMED` | Los vasos vienen impresos y no la necesitan |
| Y-MP-014 | Caja corrugada de 24 unidades | cajas | 278 (vasos) · 209 (botellas) | Las 3 | `ASSUMED` (24 un/caja) / `CALCULATED` | Se redondea hacia arriba |

---

## Pendientes y supuestos a confirmar

- Dosis de cultivos DVS (Y-MP-007 a 009): se dejan según la ficha del proveedor; no afectan el balance de masa.
- Método de concentración del griego: se asume ultrafiltración. La alternativa es un separador centrífugo (tipo quark); la decisión afecta los equipos (capa 5) y el CAPEX.
- Vigencia normativa: la Res. 1407 de 2022 reemplazó los criterios **microbiológicos** de la Res. 2310 de 1986. Los requisitos fisicoquímicos de esta tabla se toman de la Res. 2310 y de la ficha técnica del ICBF, que la sigue citando. Por verificar si algún artículo fisicoquímico fue modificado.
- Mezcla de producción 50/20/30: supuesto del equipo, que se ajusta al definir la capacidad (capa 9).
