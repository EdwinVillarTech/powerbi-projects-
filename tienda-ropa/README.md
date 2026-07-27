# Dashboard de Ventas — Nivel Básico (Power BI)

**Autor:** Edwin Alberto Villar Díaz
**Nivel:** Básico — Roadmap Power BI
**Herramientas:** Power BI Desktop, Excel

---

## 1. El problema

La gerencia de una empresa con presencia en 3 sucursales (Norte, Sur, Este) necesita
un reporte simple que muestre el total de ventas, el desempeño por sucursal, y qué
categorías de producto están funcionando mejor o peor, para decidir dónde enfocar
esfuerzos comerciales.

## 2. Lo que encontré en los datos

- El total general de ventas ronda los **26 mil** en el período analizado.
- La categoría **Electrónicos** lidera claramente las ventas por encima de las demás.
- La categoría **Cables** es la de menor facturación de todo el catálogo.
- Al comparar sucursales, el desempeño no es uniforme — hay diferencias visibles
  entre Norte, Sur y Este que vale la pena seguir investigando en el siguiente nivel
  (cuando se agregue comparación año contra año).

## 3. Cómo lo resolví

- Conecté los datos de ventas desde Excel a Power BI Desktop.
- Construí 3 vistas separadas para no saturar un solo dashboard:
  - **Resumen General**: Tarjeta de Total de Ventas + Slicer interactivo por Vendedor.
  - **Ventas por sucursal**: comparación de montos entre Norte, Sur y Este.
  - **Ventas por categoria**: gráfico de barras para identificar qué productos
    mueven más dinero.
- Agregué un Slicer de Vendedor para que el reporte sea explorable sin tocar nada
  más que un click — cualquier persona no técnica puede filtrar por vendedor.

## 4. Mi opinión / conclusión analítica

Cables tiene la venta más baja, pero antes de asumir que es un problema de demanda,
hay que preguntarse **si se está midiendo bien el éxito de esa categoría**. Un cable
cuesta una fracción de lo que cuesta una laptop o un monitor, así que aunque se
vendan varias unidades, nunca va a competir en monto total contra Electrónicos.

Mi recomendación no es lanzar una promoción aislada de cables, sino implementar
**venta cruzada (cross-selling)**: ofrecer el cable, el mouse o el cargador en el
mismo momento en que el cliente compra la laptop o el monitor. El cliente ya está
en modo de compra y el costo adicional es bajo, lo que facilita mucho más la venta
que esperar a que alguien entre buscando solo un cable.

## 5. Qué aprendí / qué haría distinto

- Aprendí que un número bajo en un gráfico no siempre significa "poco interés" —
  puede significar que la categoría se mide de forma incompleta (monto vs unidades).
- La próxima vez, agregaría desde el inicio una tarjeta de **Cantidad vendida**
  junto a la de monto, para poder distinguir entre "se vende poco" y "se vende
  barato" sin tener que volver atrás a revisarlo.
- Para el siguiente nivel (Intermedio), quiero relacionar esta tabla de Ventas con
  una tabla de Productos y una de Sucursales, en vez de trabajar con una sola tabla
  plana, para practicar el modelo relacional real de Power BI.

---
