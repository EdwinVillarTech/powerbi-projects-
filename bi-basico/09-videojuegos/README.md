Dashboard de Ventas — Tienda de Videojuegos

Autor: Edwin Alberto Villar Díaz

1. El problema

Se solicitó un dashboard para conocer las ventas totales, qué plataforma vende más, 
cómo cambia el ranking de géneros mes a mes, la relación entre precio y calificación de los juegos,
y el detalle de ventas por vendedor.

2. El ETL — dividir columna por número de caracteres

La columna "Codigo" venía como un código sin separadores (ej. PS5DEP001), sin ningún símbolo que lo dividiera.
Se resolvió usando "Dividir columna" → "Por número de caracteres" — una herramienta 100% visual, sin necesidad de escribir fórmulas 
— tomando los primeros 3 caracteres como Plataforma, los siguientes 3 como Género, y los últimos 3 como número de secuencia. 
Luego se usó "Reemplazar valores" para convertir los códigos cortos (PS5, DEP...) en nombres completos (PlayStation 5, Deportes...).

La columna Calificación venía con coma decimal (7,8), pero como el formato del archivo coincidía con la configuración regional en español de Power BI, se pudo convertir directamente a Número Decimal sin necesidad de especificar configuración regional adicional — a diferencia de proyectos anteriores donde sí hacía falta ese paso extra.

3. Lo que encontré

   
Ventas totales: ~1 millón de pesos
Plataforma líder: PC, con 319,947 — Nintendo Switch es la más baja, con 231,976
Ranking de géneros (gráfico de Cintas): el liderazgo cambia cada mes — Deportes en enero, Acción en febrero, Aventura en marzo, Estrategia en abril, Simulación en mayo, y Deportes de nuevo en junio. No existe un género dominante estable.
Precio vs Calificación (Dispersión): se observa una leve tendencia donde juegos de mayor precio tienden a agruparse en calificaciones más altas, aunque con excepciones — el precio no es el único factor de la percepción de calidad.
Vendedora líder: Dahiana Marte, con 295,372 en ventas


5. Cómo lo resolví

Conecté el CSV y resolví el ETL descrito arriba, sin usar fórmulas condicionales 
— todo con herramientas de menú (Dividir columna, Reemplazar valores, Cambiar tipo).
Construí el dashboard con: Tarjeta de Ventas Totales, Tabla por Plataforma, gráfico de Cintas
(primera vez) para el ranking mensual de géneros, gráfico de Dispersión (repaso) para precio vs calificación, 
y Matriz de detalle por Vendedor.

7. Mi conclusión

La rotación constante del género líder mes a mes sugiere que las ventas no dependen de una preferencia de mercado fija, 
sino de factores puntuales como lanzamientos de nuevos títulos o promociones específicas. 
Esto implica que la estrategia comercial debería planificarse mes a mes según el calendario de lanzamientos, 
en vez de asumir un género "seguro" de forma permanente. La relación entre precio y calificación, aunque no es perfecta, 
sugiere que invertir en calidad del producto sí se refleja en mejor percepción del cliente.

6. Qué aprendí
   
Dividir una columna por número de caracteres (posición fija) es una alternativa útil cuando el texto no tiene un delimitador visible como coma o guion 
— todo resuelto sin escribir ninguna fórmula.
No siempre hace falta especificar "configuración regional" al cambiar un tipo de dato 
solo cuando el formato del archivo choca con el idioma configurado del programa. Conviene verificar el resultado antes de asumir que hace falta ese paso extra.

En un gráfico de Dispersión, agregar el campo de detalle (como "Juego")
es indispensable para que cada punto represente un registro individual
 dejar solo agregaciones tipo "Suma" colapsa todos los puntos en uno solo.

El gráfico de Cintas se distingue de Barras apiladas cuando el orden de las categorías cambia entre períodos 
si el ranking se mantiene siempre igual, ambos gráficos comunican lo mismo.
