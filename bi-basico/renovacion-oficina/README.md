Readme · MD
Dashboard de Presupuesto — Renovación de Oficina

Autor: Edwin Alberto Villar Díaz

1. El problema

El Gerente de Proyecto solicitó un dashboard para dar seguimiento al presupuesto de una renovación de oficinas: total gastado, gastos pendientes de pago, cómo se distribuye el gasto por categoría, el detalle por proveedor, y si se está gastando dentro del límite de 3,000,000 de pesos.

2. El ETL — un nuevo tipo de formato sucio

La columna Monto venía en 3 estilos: números normales, y dos con abreviaturas de escala (60.84K para miles, 0.022M para millones). Se resolvió con una fórmula condicional que revisa si el texto termina en "K" o "M", quita esa letra, convierte a número y multiplica por 1,000 o 1,000,000 según corresponda.

3. Lo que encontré
Total gastado: 2,576,532.81 (86% del presupuesto de 3,000,000)
Total pendiente de pago: ~1,450,000
Categoría líder: Materiales (832,609), seguida de Mano de Obra (669,993) — juntas superan la mitad del gasto total
Proveedor destacado: Constructora Belén, con el gasto más alto en enero (139,520 en ese mes)
El presupuesto no se ha excedido, pero está cerca del límite


4. Cómo lo resolví
   
Conecté el CSV y limpié el formato de Monto, Proveedor y Estado.
Construí un gráfico de Cascada para mostrar cómo se acumula el gasto categoría por categoría — primer uso de este tipo de visual.
Usé un Medidor para comparar el gasto actual contra la meta de 3,000,000 (86% de avance).
Intenté primero un gráfico de Dispersión para relacionar fecha y monto de cada gasto, pero resultó saturado e ilegible — se reemplazó por Columnas apiladas (mes en el eje, monto en valores, proveedor en leyenda), que comunica la misma información de forma más clara.
Creé mis primeras medidas DAX (Meta Presupuesto), como primer contacto con este lenguaje antes de pasar al Nivel Intermedio.
Probé el visual de KPI para comparar gasto vs meta, pero descubrí que su comportamiento no es el adecuado para datos transaccionales sueltos: al usar una fecha como eje de tendencia, el KPI muestra solo el valor del último punto en el tiempo, no el acumulado — por eso se reemplazó por el Medidor, que sí responde correctamente a esta pregunta.


6. Mi conclusión

El proyecto va dentro del presupuesto, aunque cerca del límite (86% ejecutado). Materiales y Mano de Obra concentran más de la mitad del gasto, lo cual es esperable en una renovación. El monto pendiente de pago (~1.45 millones) es una cifra considerable que debe monitorearse para no comprometer el flujo de caja del proyecto en los meses restantes.

6. Qué aprendí
No toda combinación de 2 variables numéricas necesita un gráfico de Dispersión — solo tiene sentido cuando existe una relación de negocio esperable entre ellas. Fecha y monto de un gasto puntual no la tienen.
El visual de KPI y el Medidor no son intercambiables aunque ambos comparen un valor contra una meta: el KPI está pensado para series de tiempo recurrentes, no para totales acumulados de datos transaccionales.
Antes de confiar en que una opción de formato hace lo que su nombre sugiere (como una "etiqueta de total"), conviene verificarlo contra el cálculo manual.
Empezar a usar medidas DAX simples, aunque sea con fórmulas básicas, es un buen primer paso antes de entrar de lleno al Nivel Intermedio.
