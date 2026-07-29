# Dashboard de Ventas — Cadena de Farmacias

**Autor:** Edwin Alberto Villar Díaz

---

## 1. El problema

Una cadena de 4 farmacias (Naco, Piantini, Los Ríos, San Isidro) solicitó un
dashboard para responder: cuánto se vendió en total, cómo se distribuyen las
ventas entre sucursales, qué categorías de medicamentos lideran, qué % de las
ventas requiere receta médica, quién es el farmacéutico líder, y cómo se
comportaron las ventas mes a mes.

## 2. Un ETL más complejo que resolví

El archivo tenía los precios en 3 formatos mezclados: normal, con símbolo
`RD$` y coma de miles, y con coma como separador decimal. Usé una columna
condicional en Power Query que primero limpia cualquier símbolo de moneda y
espacio, y luego decide si debe quitar comas o reemplazarlas por punto, según
si el texto ya contiene un punto decimal o no. También validé que la
fórmula no fallara con los valores nulos.

También detecté que una columna de "Mes" en texto (enero, febrero...) se
ordenaba alfabéticamente en vez de cronológicamente — lo corregí creando una
columna numérica de mes y usando "Ordenar por columna" para fijar el orden
correcto.

## 3. Lo que encontré

- **Ventas totales:** 645,532.85 | **Órdenes:** 405 | **Ticket promedio:** 1,600
- **Sucursal líder:** Piantini, con 45.15% de las ventas totales
- **Categoría líder:** Equipos (termómetros, tensiómetros) — productos de
  precio alto aunque se vendan pocas unidades
- **Categoría más baja:** Cuidado Personal
- **Requiere receta:** 66.07% de las ventas NO requieren receta, 33.93% sí
- **Farmacéutico líder:** Franklin Soto, con 139,621.11 en ventas
- **Tendencia mensual:** forma de "V" — enero fue el mes más alto (~140 mil),
  cayó progresivamente hasta mayo (~76 mil), y se recuperó fuerte en junio
  (~130 mil)

## 4. Cómo lo resolví

- Conecté el CSV, limpié duplicados, valores nulos y el precio con formato
  mixto usando una fórmula condicional.
- Construí un dashboard en una sola página con: Tarjetas KPI, gráfico de
  líneas por mes, Treemap por categoría, Dona por sucursal, Dona por
  requiere receta, y una Matriz de detalle por farmacéutico y producto.
- Filtré del gráfico de tendencia una fila con fecha vacía que distorsionaba
  la lectura visual, manteniéndola visible en la Matriz de detalle para no
  perder la trazabilidad del dato.

## 5. Mi conclusión

La alta concentración de ventas en Piantini (45%) sugiere dependencia de una
sola sucursal. La categoría Equipos lidera por precio alto, no
necesariamente por volumen — vale la pena revisar cantidad vendida aparte
del monto. La caída de ventas entre febrero y mayo, seguida de la
recuperación en junio, parece estacional más que un declive real del
negocio, aunque merece investigarse qué cambió en junio para replicarlo.

## 6. Qué aprendí

- Un archivo puede tener más de 2 formatos de precio mezclados a la vez, no
  solo uno — hay que revisar con calma antes de asumir que ya se limpió todo.
- Una columna de texto (como nombres de mes) no se ordena cronológicamente
  por sí sola — hay que decirle explícitamente a Power BI cómo ordenarla.
- Sacar una conclusión con datos parciales (viendo solo hasta un mes) puede
  llevar a una lectura equivocada — conviene revisar el panorama completo
  antes de afirmar un patrón.

---

📁 Archivo del proyecto: `dashboard-ventas-farmacia.pbix`
