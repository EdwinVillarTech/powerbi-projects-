Dashboard de RRHH — Plantilla de Empleados

Autor: Edwin Alberto Villar Díaz

1. El problema

El área de RRHH solicitó un dashboard para conocer el total de empleados, el salario y ausencias promedio, cómo se distribuye la plantilla por departamento y género, si existe relación entre antigüedad y salario, qué empleados presentan más ausencias, y la proporción de empleados activos vs inactivos.

2. El ETL — retos distintos a proyectos anteriores

Este proyecto tuvo desafíos de limpieza distintos a los de ventas:

Nombre Completo dividido en Nombre y Apellido, con la dificultad de que algunos empleados tienen apellidos compuestos de varias palabras ("María de los Santos", "Ramón Antonio Cruz").
Salario con 3 estilos de separador de miles mezclados (sin separador, con coma, con espacio) — resuelto con una fórmula que quita ambos caracteres antes de convertir a número.
Género unificado entre "M/F" y "Masculino/Femenino" con mayúsculas inconsistentes.
Ausencias con algunos valores negativos por error de digitación, detectados y corregidos.
Se detectaron 2 filas duplicadas que inicialmente no había eliminado — de haberlas dejado, el conteo de empleados y la suma de salarios habrían quedado inflados.


3. Lo que encontré
   
Total de empleados: 82 | Salario promedio: ~73,300 | Ausencias promedio: 6.27
Por departamento: Ventas lidera con 31 empleados, seguido de Sistemas con 19; Recursos Humanos es el más pequeño con 5
Por género: distribución relativamente pareja, 55.56% M y 44.44% F
Antigüedad vs Salario (gráfico de dispersión): no se observa una relación clara y constante entre los años de antigüedad y el salario actual — los puntos no siguen una tendencia ascendente sostenida, lo que sugiere que la antigüedad no es el factor principal que determina el salario en esta plantilla
Estado: distribución cercana entre empleados Activos e Inactivos


5. Cómo lo resolví

Conecté el CSV y resolví los retos de limpieza descritos arriba.
Creé una columna calculada de Antigüedad (años desde la fecha de contratación hasta hoy) para poder construir el gráfico de dispersión.
Usé un filtro Top N sobre una tabla ordenada para identificar a los empleados con más ausencias, en vez de intentar mostrar los 82 en un Treemap (que resultaba ilegible con tantas categorías).
Construí el dashboard con: Tarjetas KPI, Dona (departamento/género y estado), Tabla con Top N de ausencias, Matriz de detalle por departamento y empleado, y un gráfico de Dispersión para antigüedad vs salario.


5. Mi conclusión

La plantilla está concentrada en Ventas y Sistemas, que juntos representan más de la mitad de los empleados. El hallazgo más relevante es que la antigüedad no parece explicar por sí sola las diferencias salariales — esto sugiere que otros factores (puesto, departamento, evaluación de desempeño) podrían tener más peso, y valdría la pena analizarlos en un siguiente nivel del proyecto.

6. Qué aprendí
Dividir una columna de texto con estructura irregular (nombres de distinta cantidad de palabras) requiere más cuidado que un delimitador simple.
Un gráfico de Dispersión no acumula valores — cada punto muestra el dato actual de una fila, no un histórico sumado, y hay que tenerlo claro antes de interpretar el patrón.
El filtro "Top N" es una herramienta de análisis en sí misma, no solo un método para "limpiar" un gráfico saturado — sirve para responder directamente preguntas como "¿quiénes destacan?".
Revisar los duplicados sigue siendo un paso que no se debe saltar, sin importar cuántos proyectos ya se hayan hecho.
