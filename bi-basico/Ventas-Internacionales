Dashboard de Ventas Internacionales

Autor: Edwin Alberto Villar Díaz

1. El problema

Se solicitó un dashboard de ventas en 6 países

(República Dominicana, Estados Unidos, España, México, Colombia, Panamá)

para conocer el total en pesos dominicanos, ventas por país, categoría de producto líder, estado de las ventas (cerradas vs en proceso), y detalle por vendedor.

2. El ETL — conversión de moneda

El mayor reto de este proyecto: las ventas venían mezcladas en 3 monedas (USD, EUR, DOP) 

dentro de la misma columna Monto, sin que el número por sí solo indicara la moneda real. S

e resolvió con una columna condicional que revisa el valor de la columna Moneda (normalizando mayúsculas/minúsculas) 

y aplica la tasa de conversión correspondiente (USD × 58.5, EUR × 63.5, DOP sin cambio), 

generando una columna nueva "Monto DOP" para poder sumar correctamente entre países. T

ambién se unificaron los nombres de país (ej. "RD", "Rep. Dominicana" y "Republica Dominicana" como un solo valor).

Error detectado a mitad de camino: al construir el gráfico de categorías por producto, los resultados no coincidían con lo esperado — la causa fue usar por accidente la columna "Monto" original (sin convertir) en vez de "Monto DOP", mezclando magnitudes de distintas monedas como si fueran comparables. Se corrigió reemplazando el campo en todos los visuales afectados.

3. Una limitación técnica y cómo se resolvió

El visual de Mapa (y Mapa coroplético) no estaba disponible por una restricción de la cuenta 

("Map and filled map visuals not enabled"), 

un problema reportado también por otros usuarios de cuentas personales. 

Se intentó habilitar desde Opciones > Seguridad sin éxito, 

y se optó por una Tabla ordenada por País como alternativa funcional para responder la misma pregunta de negocio,

sin depender de un visual bloqueado.

4. Lo que encontré

País líder: República Dominicana

Categoría líder: Hardware, con 228,664,483.50 — Educación es la más baja, con 17,016,308.00

Ventas Cerradas vs En Proceso: 51 ventas cerradas frente al resto en proceso, 

con montos de aproximadamente 381 millones cerradas y 226 millones en proceso (ya en DOP)

Vendedor líder: Alejandro Núñez, con 159,051,938.50 en ventas

5. Cómo lo resolví

Construí el dashboard con: Tarjeta de Total, Tabla por País, Barras por Categoría, comparación de montos por Estado, 

y Matriz de detalle por Vendedor y Producto.

Mantuve el total general de ventas incluyendo todas las filas,

incluso las que tienen campos vacíos (Estado o Fecha sin registrar), 

porque esas ventas sí ocurrieron — solo desglosé el hallazgo de datos incompletos en los visuales de detalle, 

no en el total general.

6. Mi conclusión

República Dominicana como mercado líder tiene sentido al ser la base local de operaciones. 

La diferencia entre ventas Cerradas y En Proceso muestra un pipeline activo con margen de conversión pendiente. 

La brecha entre Hardware, y Educación sugiere enfocar esfuerzos comerciales en diversificar 

la oferta de bajo desempeño o reforzar lo que ya funciona bien.

7. Qué aprendí

Cuando los datos vienen en más de una moneda, hay que convertirlos a una base común ANTES de construir cualquier visual 

 de lo contrario, los totales y comparaciones quedan mal aunque el gráfico "se vea" correcto.

Un gráfico puede dibujarse sin errores visibles y aun así estar mal, si se usó la columna equivocada como fuente 

siempre vale la pena verificar qué campo exacto está alimentando cada visual.

Una limitación técnica de una herramienta (como el Mapa bloqueado) no detiene un proyecto: 

siempre hay una alternativa funcional para responder la misma pregunta de negocio.

La decisión de incluir o excluir valores vacíos depende del propósito de cada visual espe
