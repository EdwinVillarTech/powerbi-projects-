# Dashboard de Ventas — Cadena de Cafeterías

**Autor:** Edwin Alberto Villar Díaz

---

## 1. El problema

Una cadena de 4 cafeterías necesita saber cómo van sus ventas en general y en
qué horas del día vende más, para organizar mejor el personal y el inventario.

## 2. Lo que encontré

- Ventas totales: **203 mil**
- Total de órdenes: **420**
- Ticket promedio: **484**
- Dos picos de venta al día: uno en la mañana (~9:00 am) y otro en la tarde
  (~3:00-6:00 pm).

## 3. Un error que detecté y corregí

Al conectar los datos, los montos salieron 89 veces más grandes de lo real
(18 millones en vez de 203 mil). La causa: el archivo usaba punto como
separador decimal, pero Power Query lo interpretó como separador de miles.
Lo corregí cambiando el tipo de dato con la configuración regional correcta
(Inglés, Estados Unidos).

## 4. Cómo lo resolví

- Conecté el CSV a Power BI.
- Corregí el tipo de dato de las columnas numéricas.
- Armé el dashboard: título, 3 tarjetas KPI, y un gráfico de ventas por hora.
- Le apliqué un tema oscuro para que se viera más cuidado.

## 5. Mi conclusión

Los dos picos de venta indican que el personal y el inventario deberían
reforzarse justo antes de esas horas, en vez de mantener la misma capacidad
todo el día.

## 6. Qué aprendí

Un archivo puede "verse limpio" y aun así dar números mal calculados por un
tema de formato regional. Ahora reviso el tipo de dato apenas conecto un
archivo nuevo, antes de construir cualquier visual.

---

📁 Archivo del proyecto: `dashboard-ventas-cafeteria.pbix`
