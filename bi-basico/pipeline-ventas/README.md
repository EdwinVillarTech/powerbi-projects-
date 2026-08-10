Dashboard de Pipeline de Ventas B2B

Autor: Edwin Alberto Villar Díaz

1. El problema

Se solicitó un dashboard del proceso de ventas B2B para conocer cuántas oportunidades 
hay en cada etapa del embudo, qué producto genera más pipeline, la evolución mensual 
del monto, y el detalle por vendedor.

2. El ETL — un nuevo reto: formatos de porcentaje

La columna "Probabilidad Cierre" venía en 3 estilos: con símbolo % (17%), en formato
decimal (0.15), y como número plano sin símbolo (18, ya en escala de 0-100). Se 
resolvió con una fórmula que primero revisa si el texto termina en % (y lo quita), y si no 
tiene símbolo, evalúa si el número es menor a 1 para decidir si hay que multiplicarlo por 
100 o dejarlo tal cual.

Un detalle de criterio: varias filas de la etapa "Cerrada Perdida" tienen probabilidad en 0 — se confirmó que es un valor real y correcto (una oportunidad perdida efectivamente tiene 0% de probabilidad), no un dato faltante, así que se dejó sin modificar.

3. Lo que encontré
Embudo de ventas: 61 Leads → 40 Calificados → 26 Propuestas → 15 Negociaciones → 9 Cerradas Ganadas / 8 Cerradas Perdidas — una conversión total de 13.1% de leads a ventas ganadas

Cuello de botella identificado: la transición de Propuesta a Negociación tiene la tasa de supervivencia más baja del proceso (57.7%), peor que cualquier otra etapa

Evolución mensual (gráfico de Área): patrón irregular, sin tendencia sostenida — pico en mayo (~27 millones) y valle en marzo (~6.5 millones)

Vendedora líder: Solangel Feliz, con el mayor pipeline acumulado, distribuido entre los 6 productos del catálogo


4. Cómo lo resolví
Conecté el CSV, limpié fechas, probabilidad de cierre y duplicados.
Construí el dashboard con: Embudo (primera vez usándolo) para ver la progresión de etapas,
Gráfico de Área (primera vez) para la tendencia mensual, y Matriz para el detalle por vendedor y producto.

6. Mi conclusión
   
El cuello de botella real del proceso no está en generar leads ni en calificarlos, sino en convertir propuestas en negociaciones activas. Antes de asumir la causa, se recomienda cruzar esta caída por vendedor para saber si es un problema generalizado del proceso o se concentra en personas específicas, y evaluar si se necesita una validación previa con el cliente antes de enviar cada propuesta formal.

6. Qué aprendí
   
- El gráfico de Embudo no se lee comparando el tamaño de cada etapa contra las demás, sino analizando la tasa de supervivencia
entre etapas consecutivas 

— ahí está el hallazgo real, no en el número absoluto.
El gráfico de Área muestra exactamente los mismos datos que un gráfico de Líneas 

— la diferencia es puramente visual (el relleno le da más peso visual), útil cuando hay una sola serie de datos, 
pero puede saturar la lectura si se superponen varias series.

- Antes de "corregir" un valor en cero, hay que evaluar si tiene sentido de negocio que sea genuinamente cero (como una probabilidad de cierre en una venta perdida) antes de tratarlo como un dato faltante.
