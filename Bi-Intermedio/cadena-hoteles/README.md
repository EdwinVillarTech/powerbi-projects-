# Dashboard de Ingresos — Cadena de Hoteles

**Nivel:** Intermedio (Proyecto 2)
**Autor:** Edwin Alberto Villar Díaz

---

## 1. El problema

El Gerente General solicitó un dashboard para conocer los ingresos totales
y el total de reservas, el cumplimiento de la meta mensual, qué hotel
genera más ingresos, la distribución de reservas por tipo de habitación,
y el detalle por agente.

## 2. Relaciones entre tablas y nuevas funciones DAX

Se trabajó con 3 tablas: **Reservas** (transaccional), **Hoteles**
(catálogo con Ciudad, Estrellas, Gerente) y **Metas** (ingreso objetivo
por mes). Se crearon 5 medidas DAX:

- `Ingresos Totales = SUM(reservas[Precio Noche])`
- `Meta del Mes = SUM(metas_hoteles[Meta Ingresos])`
- `% Cumplimiento Meta = DIVIDE([Ingresos Totales], [Meta del Mes])`
- `Total Reservas = COUNTROWS(reservas)` — primera vez usando esta función
  para contar registros en vez de sumar montos
- `Ingresos 5 Estrellas = CALCULATE(SUM(reservas[Precio Noche]), hoteles[Estrellas] = 5)`
  — primer uso de `CALCULATE` con una condición explícita sobre una
  columna de otra tabla relacionada

## 3. Un hallazgo importante: una relación faltante que no daba error

Durante la construcción, la medida `Ingresos 5 Estrellas` mostraba el
mismo valor que `Ingresos Totales`, cuando debía ser un subconjunto más
pequeño. La causa: **la relación entre las tablas Reservas y Hoteles no
existía** — se había perdido en algún momento del proceso. Sin esa
relación, `CALCULATE` no tenía forma de aplicar el filtro de Estrellas, y
terminaba sumando todo el total sin excepción, sin mostrar ningún error
visible. Se corrigió recreando la relación por el campo "Hotel" (que
requería estar bien unificado en mayúsculas y espacios para que la
relación se creara sin conflictos).

Este hallazgo confirma una lección ya vista antes con columnas
equivocadas: una fórmula puede "funcionar" sin ningún error visible y aun
así calcular algo completamente distinto a lo esperado si el modelo de
datos no está bien construido.

## 4. Lo que encontré

- **Ingresos totales del semestre:** ~12,729,729 frente a una meta
  acumulada de ~21,000,000 — **ningún mes individual cumplió su meta**
- **Hotel líder:** Palma Real Resort (508,175.82) — el único hotel de 5
  estrellas de la cadena
- **Hotel más bajo:** Montaña Verde Lodge (367,910.40)
- **Agente líder:** Nelson Antigua (513,488.04) — el más bajo, Elvin
  Grullón (366,500.24)
- **Tipo de habitación líder:** Junior Suite (26.83%) — la distribución
  entre los 4 tipos de habitación es relativamente pareja, sin una
  diferencia dramática entre ellos

## 5. Cómo lo resolví

- Conecté 3 tablas relacionadas, con especial cuidado en unificar el
  texto de "Hotel" antes de crear la relación correspondiente.
- Construí 5 medidas DAX, incluyendo mi primer `CALCULATE` con condición
  explícita y mi primer `COUNTROWS`.
- Corregí el orden cronológico de los meses con la misma técnica de
  proyectos anteriores (columna numérica auxiliar + "Ordenar por
  columna").
- Intenté aplicar formato condicional para colorear automáticamente el
  cumplimiento de meta — queda pendiente de perfeccionar según la
  interfaz específica de mi versión de Power BI.

## 6. Mi conclusión

El incumplimiento generalizado de la meta en los 6 meses sugiere revisar
si los objetivos fueron fijados de forma muy ambiciosa respecto a la
capacidad real de reservas del negocio, más que asumir automáticamente un
problema de desempeño comercial. Palma Real Resort, como único hotel de 5
estrellas, concentra el liderazgo en ingresos — el segmento premium
podría ser la palanca de crecimiento más fuerte a reforzar en las demás
propiedades.

## 7. Qué aprendí

- Una relación faltante entre tablas puede hacer que una medida DAX
  calcule algo incorrecto sin lanzar ningún error — hay que verificar el
  resultado contra la lógica esperada, no solo confiar en que "si no da
  error, está bien".
  
- `[NombreMedida]` (sin nombre de tabla) se usa para referirse a una
  medida ya creada; `Tabla[Columna]` se usa para referirse a una columna
  cruda — confundir ambos formatos es un error común al empezar con DAX.
  
- `CALCULATE` cambia el contexto de un cálculo aplicando una condición,
  mientras que `COUNTROWS` cuenta registros en vez de sumar valores — cada
  pregunta de negocio determina cuál función usar.
`
