# Dashboard de Ventas — Concesionario de Vehículos

**Nivel:** Intermedio (Proyecto 1)
**Autor:** Edwin Alberto Villar Díaz

---

## 1. El problema

Se solicitó un dashboard para el concesionario que muestre las ventas
totales, el cumplimiento de la meta mensual, el desempeño por sucursal, y
que permita filtrar por región — el primer proyecto que requiere trabajar
con más de una tabla conectada, en vez de una sola tabla plana.

## 2. Primer contacto con relaciones entre tablas y DAX

Este proyecto usó 3 tablas en vez de una: **Ventas** (transaccional, con
datos sucios), **Sucursales** (catálogo con Región y Gerente), y **Metas**
(objetivo de ventas por mes). Se crearon relaciones en la Vista de Modelo
para conectarlas — algunas incluso se detectaron automáticamente por
Power BI al compartir nombre de columna.

Se crearon las primeras medidas DAX reales:
- `Ventas Totales = SUM(ventas_vehiculos[Precio])`
- `Meta del Mes = SUM(metas[Meta Ventas])`
- `% Cumplimiento Meta = DIVIDE([Ventas Totales], [Meta del Mes])`

Gracias a la relación entre tablas, estas medidas se recalculan
automáticamente al filtrar por cualquier campo relacionado (mes, región,
sucursal), sin necesidad de escribir una fórmula distinta para cada caso.

## 3. Un error de ETL que reapareció y su lección

Al convertir la columna Precio, se coló otra vez el mismo tipo de error de
proyectos anteriores: el punto decimal se perdió en la conversión,
inflando los montos por 100 (ej. `1713885.33` se convirtió en `171388533`).
Se corrigió eliminando los pasos dañados y aplicando "Cambiar tipo usando
configuración regional" una sola vez, de forma limpia. Se verificó contra
un cálculo de referencia externo antes de continuar.

## 4. Lo que encontré

- **Ventas totales del semestre:** ~254.8 millones
- **Meta acumulada:** 166 millones — cumplimiento del 154%, superando la
  meta en más de la mitad
- **Sucursal líder:** Santiago Centro (región Cibao), con 82.6 millones
- **Sucursal más baja:** Autopista Las Américas (región Este), con 41.9
  millones — casi la mitad que la líder

## 5. Cómo lo resolví

- Conecté 3 tablas relacionadas en la Vista de Modelo.
- Construí medidas DAX con `SUM` y `DIVIDE` para el cumplimiento de meta.
- Corregí el orden cronológico de los meses (texto) usando "Ordenar por
  columna" con una columna numérica auxiliar, igual que en proyectos
  anteriores.
- Armé una Matriz de Ventas por Sucursal y Región, y un Slicer de Región
  conectado a través de la relación entre tablas — confirmando que el
  filtro recalcula automáticamente las medidas DAX sin fórmulas extra.

## 6. Mi conclusión

El concesionario superó su meta semestral con holgura, liderado
fuertemente por la sucursal de Santiago Centro. La brecha entre la mejor y
la peor sucursal (casi el doble) merece investigarse, aunque a diferencia
de otros hallazgos previos, aquí el resultado general es positivo — el
enfoque debería ser replicar lo que funciona en Santiago Centro en las
demás sucursales, más que corregir un problema.

## 7. Qué aprendí

- Las relaciones entre tablas permiten que una sola medida DAX se
  recalcule automáticamente según cualquier filtro relacionado, sin
  escribir una fórmula distinta para cada combinación posible — ese es el
  verdadero valor de separar los datos en varias tablas en vez de una sola.
- El mismo error de conversión de decimales puede repetirse en proyectos
  distintos si no se verifica el resultado contra un número de referencia
  externo antes de construir visuales sobre él.
- Leer números grandes sin separador de miles es propenso a errores de
  interpretación (contar mal los ceros) — conviene activar el formato de
  separador de miles en cuanto sea posible.

---

📁 Archivo del proyecto: `dashboard-concesionario-vehiculos.pbix`
