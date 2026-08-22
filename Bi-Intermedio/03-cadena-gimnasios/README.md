# Dashboard de Ingresos — Cadena de Gimnasios

**Nivel:** Intermedio (Proyecto 3)
**Autor:** Edwin Alberto Villar Díaz

---

## 1. El problema

Se solicitó un dashboard para conocer los ingresos totales y membresías
vendidas, el cumplimiento de la meta mensual, cuánto generan las
sucursales Premium frente a las Estándar, qué sucursal vende más, la
distribución por tipo de plan, y el detalle por vendedor.

## 2. Repetición con independencia

A diferencia de los 2 proyectos anteriores de Intermedio, este se resolvió
sin guía paso a paso — el objetivo fue reforzar las mismas medidas DAX
(`SUM`, `DIVIDE`, `CALCULATE`, `COUNTROWS`) hasta que el razonamiento se
sintiera natural. El tiempo total de trabajo bajó a aproximadamente 1
hora, frente a sesiones más largas en los proyectos anteriores.

Se corrigió un error de estructura en `CALCULATE`: la primera versión
intentó poner la condición de categoría dentro del `SUM` (en vez de como
segundo argumento separado por coma), lo cual no es válido — se corrigió
la sintaxis a `CALCULATE(SUM(membresias[Precio]), sucursales_gym[Categoria] = "Premium")`.

## 3. Lo que encontré

- **Ingresos totales:** ~1.49 millones | **Membresías vendidas:** 262
- **Sucursal líder:** Santiago Power Gym (412,845.69) — una de las 2
  sucursales de categoría Premium de la cadena
- **Cumplimiento de meta:** no se cumplió en enero (65% de la meta) — un
  patrón similar al observado en el proyecto de Hoteles
- **Plan líder:** Plan Anual, con cerca del 57-58% del total de ingresos
  — muy por encima de los otros 3 planes combinados
- **Vendedor líder:** Mario Sánchez (416,866.85) — el más bajo, Katiuska
  Peralta (310,647.94)

## 4. Cómo lo resolví

- Conecté 3 tablas relacionadas (Membresías, Sucursales, Metas), limpiando
  la columna Sucursal antes de crear la relación correspondiente.
- Construí 5 medidas DAX por cuenta propia: Ingresos Totales, Meta del
  Mes, % Cumplimiento Meta, Ingresos Premium (con `CALCULATE`), y
  reconocí que faltaba `COUNTROWS` para el total de membresías.
- Armé el dashboard con Tarjetas, comparación Premium vs Estándar, Dona
  por tipo de plan, Matriz por vendedor, y Slicer por sucursal.

## 5. Mi conclusión

El Plan Anual domina claramente las ventas, lo que sugiere que los
clientes prefieren comprometerse a largo plazo cuando se les ofrece esa
opción — vale la pena evaluar si promocionarlo más activamente podría
mejorar el cumplimiento de la meta mensual, que actualmente no se alcanza.
La concentración de ingresos en las sucursales Premium (Santiago Power Gym
liderando) sugiere que ese formato de negocio funciona mejor que el
Estándar, y podría valer la pena evaluar si conviene expandir ese modelo.

## 6. Qué aprendí

- La condición de `CALCULATE` siempre va como un argumento separado por
  coma, nunca dentro de la función de agregación (`SUM`, `AVERAGE`, etc.)
  — es un error de sintaxis fácil de cometer al empezar.
- Repetir el mismo tipo de medidas DAX en distintos proyectos consolida
  el razonamiento mucho más rápido que intentar aprender fórmulas nuevas
  en cada proyecto — el tiempo de trabajo bajó considerablemente en esta
  repetición.
- `COUNTROWS` sigue siendo la función menos automática de recordar en
  comparación con `SUM` y `CALCULATE` — requiere más repetición
  consciente para interiorizarla del todo.

---

📁 Archivo del proyecto: `dashboard-cadena-gimnasios.pbix`
