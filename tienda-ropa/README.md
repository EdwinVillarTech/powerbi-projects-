Dashboard de Ventas — Tienda de Ropa

Autor: Edwin Alberto Villar Díaz

1. El problema

Una tienda de ropa con 4 sucursales (Agora Mall, Blue Mall, Sambil, Megacentro) necesita saber cómo van sus ventas del semestre, qué categorías funcionan mejor, qué sucursal concentra más ventas, y si se está cumpliendo la meta.

2. Un error que detecté y corregí (ETL)

El archivo de origen tenía los precios en 2 formatos distintos mezclados en la misma columna: unos con símbolo $ y coma de miles ($2,855.24) y otros con coma como separador decimal (1652,57). Un solo "Reemplazar valores" no servía para los dos casos a la vez, así que usé una columna condicional en Power Query que revisa si el texto tiene punto: si lo tiene, quita las comas; si no, cambia la coma por punto. También tuve que agregar una validación para que la fórmula no fallara con los valores vacíos (null).

3. Lo que encontré
Ventas totales: 1,542,260
Categoría líder: Vestidos, con 137,048 en ventas
Categoría más baja: Camisetas, con 38,575
Sucursal líder: Blue Mall, con el 43.49% de las ventas totales — casi iguala ella sola a las otras 3 sucursales combinadas (56.51%)
Meta semestral: cumplida en un 74.5% (1.49 millones de 2 millones)
4. Cómo lo resolví
Conecté el CSV a Power BI y limpié los datos (duplicados, precios, valores vacíos) en Power Query.
Construí varios tipos de visual para practicar cuándo usar cada uno:
Gráfico de líneas con jerarquía de fechas para ver la tendencia
Treemap para comparar categorías por tamaño
Dona para ver la proporción de ventas entre sucursales
Medidor para ver el avance contra la meta semestral
Matriz para poder revisar el detalle de ventas por vendedor y producto
5. Mi conclusión

Blue Mall concentra una parte muy alta de las ventas totales, lo cual es una señal de dependencia riesgosa hacia una sola sucursal. Valdría la pena investigar qué está funcionando ahí (ubicación, personal, tráfico) para replicarlo en las demás. Respecto a la meta, con un 74.5% de avance, es probable cerrar cerca del objetivo si el ritmo se mantiene, aunque conviene reforzar el resto del período.

6. Qué aprendí
Una misma columna puede tener más de un formato de dato sucio mezclado (no solo un problema, sino dos o más superpuestos), y hay que revisar caso por caso antes de aplicar una limpieza masiva.
Aprendí a elegir el tipo de gráfico según la pregunta de negocio: tendencia en el tiempo, proporción entre partes, comparación de tamaños, o avance contra una meta — cada uno responde algo distinto.
