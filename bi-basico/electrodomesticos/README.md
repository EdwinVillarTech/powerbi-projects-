Dashboard de Ventas — Electrodomésticos
Autor: Edwin Alberto Villar Díaz
---
1. El problema
Se solicitó un dashboard de ventas de electrodomésticos con jerarquía
profunda (Región → Categoría → Subcategoría → Producto) para permitir
explorar de dónde vienen las ventas, además de conocer el detalle por
vendedor y la tendencia mensual.

2. El ETL
Limpieza estándar: unificación de Región (espacios y mayúsculas
inconsistentes), eliminación de duplicados, y tratamiento de valores
nulos en filas con datos incompletos — todo resuelto con herramientas
visuales de Power Query, sin fórmulas personalizadas.

3. Dos herramientas nuevas: Slicer sincronizado y Esquema Jerárquico

Se configuró un Slicer de Región sincronizado entre páginas, para
que el mismo filtro aplique en todo el dashboard sin necesidad de
repetirlo en cada página.

Se construyó un Esquema Jerárquico (Decomposition Tree) con Precio
como valor a analizar, y Región, Categoría, Subcategoría, Producto y
Vendedor como campos disponibles para explorar en cualquier orden.

4. Lo que encontré

Total de ventas: ~3.5 millones durante el semestre
Categoría líder (vía Esquema Jerárquico): Refrigeración, con
1,662,300 — dentro de esa categoría, Neveras lidera con 780,000
Vendedora líder: Jhoselin Abreu, con 840,300 — Nairoby Suero es la
más baja, con 514,100

Vía Matriz y gráfico de Líneas: se complementó la exploración libre
del Esquema Jerárquico con una vista fija de Vendedor por Mes y la
tendencia mensual general

5. Cómo lo resolví

Construí el dashboard combinando dos tipos de visual con propósitos
distintos: el Esquema Jerárquico para exploración abierta (sin saber de
antemano qué combinación querría ver el usuario), y una Matriz + gráfico
de Líneas para las preguntas específicas que ya sabía que necesitaba
responder de forma fija.

6. Mi conclusión

El Esquema Jerárquico es una herramienta poderosa para dar autonomía de
exploración a quien usa el dashboard, pero no reemplaza a los visuales
tradicionales cuando ya se sabe exactamente qué comparación se necesita
mostrar de forma consistente — ambos enfoques son complementarios, no
sustitutos.

7. Qué aprendí

El Esquema Jerárquico responde una pregunta distinta a los demás
gráficos: no muestra una vista fija, sino que permite que el usuario
decida el camino de exploración en el momento.
Sincronizar un Slicer entre páginas evita tener que repetir el mismo
filtro manualmente en cada página del reporte.
Ningún visual debería quedarse con su título automático genérico — un
título en lenguaje de negocio hace que el dashboard se entienda sin
necesidad de que el analista esté presente explicándolo.
---
📁 Archivo del proyecto: `dashboard-ventas-electrodomesticos.pbix`
