Dashboard de Ventas — Panadería / Repostería

Autor: Edwin Alberto Villar Díaz

1. El problema

Una cadena de 4 panaderías (Naco, Piantini, Bella Vista, Arroyo Hondo) solicitó un dashboard para responder: ventas totales, distribución entre sucursales, categorías que más y menos venden, proporción de ventas por Mostrador vs Encargo, vendedor líder con su detalle, y comportamiento de ventas mes a mes.

2. El ETL

El archivo tenía precios en 3 formatos mezclados (normal, con símbolo RD$ y coma decimal), resuelto con una columna condicional en Power Query. Un detalle nuevo: un paso previo de "Poner en mayúsculas" había alterado el símbolo de moneda de RD$ a Rd$, lo que rompió la primera versión de la fórmula — hubo que ajustarla para reconocer tanto mayúsculas como minúsculas. Este ETL tomó 12 minutos, frente a los 21 del proyecto anterior.

3. Lo que encontré
Ventas totales: 485,348.46 | Órdenes: 395 | Ticket promedio: ~1,232
Sucursal líder: Naco, con 38.97% de las ventas — casi el doble que Bella Vista, la más baja con 13.69%
Categoría líder: Pasteles (373,464), muy por encima de Galletas (15,157) — la diferencia responde más al precio del producto que al volumen: Bebidas y Pasteles tienen cantidades de unidades vendidas parecidas (399 vs 503), pero el precio unitario cambia todo el resultado
Mostrador vs Encargo: 52.35% Mostrador, 47.65% Encargo — una distribución equilibrada, con oportunidad de crecer en encargos planificados (eventos, cumpleaños)
Vendedora líder: Carla Espinal, con 113,125.03 en ventas, con productos variados (panes, postres, bebidas)
Tendencia mensual: las ventas subieron hasta un pico en febrero (102,228), y desde ahí bajaron de forma sostenida hasta junio, el mes más bajo del semestre (54,067) — sin recuperación hacia el cierre, a diferencia del patrón en forma de "V" visto en un proyecto anterior
4. Cómo lo resolví
Conecté el CSV, limpié duplicados, nulos y el precio con formato mixto.
Construí el dashboard en una sola página, decidiendo por mi cuenta qué visual usar para cada pregunta de negocio: Dona (sucursal y tipo de pedido), Treemap (categoría), Matriz (vendedor y producto), Líneas (tendencia mensual) y Tarjetas (KPIs generales).
5. Mi conclusión

La brecha entre Naco y Bella Vista amerita revisar factores como ubicación o tamaño del local antes de asumir un problema de desempeño. La categoría Pasteles lidera por su precio alto, no necesariamente por mayor demanda en unidades. El equilibrio entre Mostrador y Encargo es una señal saludable del negocio, con espacio para crecer en encargos. La caída sostenida de ventas de febrero a junio, sin recuperación, merece investigarse — podría tratarse de temporada baja o cambios en el mercado que no se repitieron como en otros negocios analizados.

6. Qué aprendí
Un paso de limpieza de texto (como "Poner en mayúsculas") puede alterar sin querer un símbolo que otra fórmula depende para funcionar — el orden de los pasos en Power Query importa.
Un total alto en dinero no siempre significa mayor demanda en unidades — hay que comparar ambos datos antes de sacar conclusiones.
Al comunicar hallazgos donde alguien "queda mal" en el número (una sucursal o vendedor con bajo desempeño), es mejor describir el dato y proponer investigar las causas, en vez de atribuir la causa como un hecho sin evidencia.
