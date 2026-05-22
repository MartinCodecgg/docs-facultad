# Veredicto Final: Registro de Materias y Notas en Moodle

## Objetivo definido

Que el alumno ingrese todas las materias que cursó junto con la nota de cada una, y que cada par materia-nota quede guardado individualmente en Moodle, asociado al alumno. El profesor debe poder ver qué alumnos completaron la carga y exportar los datos para análisis.

---

## Contexto y limitaciones del entorno

- Moodle de una facultad (ingenieria.campus.mdp.edu.ar), sin acceso de administrador
- Rol: Profesor en un curso específico
- Webservices AJAX deshabilitados para llamadas externas
- El sesskey de Moodle NO es un token de webservice válido
- Módulos disponibles sin instalar nada: Base de Datos, Lección, Encuesta (Feedback), entre otros

---

## Opciones evaluadas

### Opción 1 — Lección + Base de Datos (ya instalados)

**Cómo funciona:**

El alumno primero entra a la actividad Base de Datos y carga una entrada por cada materia cursada (nombre de materia + nota). Una vez que cargó el mínimo de entradas requeridas, la Base de Datos se marca como completa automáticamente. Recién entonces se desbloquea la Lección, que es una pantalla final de confirmación que el alumno completa para registrar que terminó el proceso.

**Flujo del alumno:**

```
Base de Datos → carga materia + nota (repetir por cada materia)
      ↓ (al cumplir mínimo de entradas, BD se marca completa)
Lección → pantalla final de confirmación → Moodle registra como completada
```

**Restricción de acceso (CONFIRMADO, no es intuición):**

Moodle permite restringir el acceso a la Lección condicionado a que la Base de Datos esté marcada como completa. Esto se configura en los ajustes de la Lección → sección "Restricciones de acceso" → "Finalización de actividad" → seleccionar la Base de Datos. Es una funcionalidad nativa de Moodle documentada oficialmente.

**Matiz importante sobre la restricción:** Moodle valida que el alumno cargó N entradas (el número que vos definís), no que haya cargado sus materias específicas reales. Un alumno podría cargar entradas vacías o inventadas para desbloquear la Lección. En un contexto académico esto se considera aceptable dado que es responsabilidad del alumno cargar datos verídicos.

**Configuración recomendada del mínimo de entradas:** Poner el mínimo en 1. Esto significa que la Base de Datos se marca como completa al cargar la primera entrada, desbloqueando la Lección. El alumno puede seguir cargando más entradas libremente después sin ningún problema, ya que el mínimo es un piso, no un techo. Si el alumno cursó 5 materias, carga las 5 aunque la BD ya esté marcada como completa desde la primera. Poner 0 no funciona porque la actividad nunca se marcaría como completa automáticamente.

**Ventajas:**

- Ya está disponible, no requiere al administrador
- Datos exportables a Excel desde la Base de Datos (formato: una fila por materia, columnas: alumno, materia, nota)
- El formato de exportación es flexible para análisis: filtrar por alumno, calcular promedios por materia, pivot tables
- El profesor ve exactamente quién completó y quién no desde el informe de finalización del curso
- Restricción de acceso real entre las dos actividades

**Desventajas:**

- El alumno carga una entrada por materia, no todo en un solo formulario
- El diseño visual es el nativo de Moodle, no personalizable
- No hay validación de que el alumno cargó todas sus materias reales
- Son dos actividades separadas, puede confundir a algunos alumnos
- El número mínimo de entradas para completar la BD es fijo (definido por el profesor), no dinámico por alumno

---

### Extensión futura: Página de análisis para profesores

**Exportación desde Moodle:**

Moodle exporta la Base de Datos en formato CSV estándar con todas las entradas. No hay forma de hacer una consulta SELECT personalizada desde la interfaz de profesor, eso solo lo puede hacer el administrador con acceso directo a la base de datos. El CSV exportado tiene formato vertical (una fila por entrada), con columnas fijas: fecha, nombre del alumno, username, y los campos definidos (materia, nota).

**Página JS para análisis (viable y recomendada como extensión):**

Es posible crear una Página en Moodle, visible únicamente para profesores mediante restricción de acceso por rol, que permita subir el CSV exportado de Moodle y mostrarlo como tabla filtrable con promedios calculados automáticamente.

**¿Se puede hacer con JS nativo sin módulos externos?**

- **CSV:** Sí, completamente viable con JS nativo usando la API `FileReader` del navegador, que es una API estándar disponible en todos los navegadores modernos sin necesidad de importar ningún módulo. El profesor selecciona el archivo CSV con un `<input type="file">`, el JS lo lee como texto, lo parsea splitteando por líneas y comas/tabs, y construye la tabla en el DOM. No requiere `import` ni librerías externas.

- **Excel (.xlsx):** No es viable con JS nativo puro. El formato .xlsx es binario y complejo, requiere una librería como SheetJS para parsearlo. Como en las Páginas de Moodle no se pueden usar módulos ES6 (`import`), habría que cargar SheetJS desde un CDN con una etiqueta `<script src="...">`, lo cual sí es posible dentro de una Página de Moodle. Sin embargo, la recomendación es exportar desde Moodle en formato CSV y no en Excel, para evitar esta dependencia.

**Conclusión:** exportar como CSV desde Moodle y subirlo a la Página JS es la ruta más simple, robusta y sin dependencias externas.

---

### Opción 2 — Questionnaire (plugin, NO instalado)

**Cómo funcionaría:**

Un formulario de encuesta con número fijo de páginas (máximo de materias, ej. 7). Cada página tiene: nombre de materia (texto corto) + nota (numérico). Si el alumno cursó menos materias, en la página N responde "no cursé" y el branching condicional lo salta directo a la página final. Al completar, Moodle lo registra automáticamente como finalizado.

**Ventajas:**

- Todo en una sola actividad, flujo más limpio para el alumno
- Branching condicional nativo y visual en tiempo real
- Registro de completitud automático al enviar
- Exportación CSV compatible con Excel

**Desventajas:**

- NO está instalado, requiere que el administrador lo instale
- La exportación CSV tiene formato horizontal (una columna por materia), menos flexible para análisis cruzado entre alumnos que el formato vertical de la Base de Datos
- El número de materias debe ser fijo de antemano
- Si el administrador no lo instala, esta opción no existe

---

### Opción 3 — Encuesta nativa de Moodle / Feedback (ya instalada)

La dependencia entre preguntas existe pero no es visual en tiempo real, se evalúa al enviar. No hay branching real. Descartada para este caso.

---

### Opción 4 — Lección sola con materias fijas (ya instalada)

Podría funcionar con número fijo de materias (máximo 7 páginas, cada una con una pregunta numérica para la nota). El branching lleva al final si el alumno responde "no cursé". Registra completitud.

**Problema:** las respuestas quedan dentro de la Lección y son muy difíciles de exportar masivamente para análisis. No hay exportación directa a CSV/Excel de las respuestas individuales. Descartada como opción principal por limitaciones de análisis posterior.

---

### Opción 5 — JS + API REST de Moodle (descartada)

Técnicamente inviable en este entorno. Los webservices AJAX están deshabilitados para roles no administrador. El sesskey no es un token de webservice válido. Requeriría al administrador para habilitar los endpoints y generar tokens, con el problema adicional de que el token quedaría expuesto en el código JS visible para cualquier alumno.

---

### Opción 6 — Google Forms embebido via iframe (fuera de Moodle)

Resuelve el formulario dinámico, condicionalidad visual perfecta, registro automático de completitud por email, diseño personalizable. Los datos van a Google Sheets.

**Descartada** porque los datos quedan fuera de Moodle y el objetivo es que queden en Moodle.

---

## Tabla comparativa final

| Criterio | Lección + BD | Questionnaire | Lección sola |
|---|---|---|---|
| Ya disponible sin admin | ✅ | ❌ | ✅ |
| Registro de completitud | ✅ | ✅ | ✅ |
| Restricción de acceso entre actividades | ✅ confirmado | N/A (1 actividad) | N/A |
| Branching condicional | ✅ (en Lección) | ✅ nativo | ✅ |
| Exportación flexible (análisis) | ✅ formato vertical | ⚠️ formato horizontal | ❌ |
| Formulario en una sola pantalla | ❌ | ✅ | ❌ |
| Diseño personalizable | ❌ | ❌ | ❌ |
| Materias dinámicas por alumno | ⚠️ parcial | ❌ fijo | ❌ fijo |

---

## Veredicto

### Si no hay acceso al administrador:

**Lección + Base de Datos es la única opción viable** que cumple todos los requisitos: registro de datos por materia, completitud rastreable, restricción de acceso real entre actividades, y exportación flexible para análisis. Es la recomendación final.

### Si se puede hablar con el administrador:

**Questionnaire es la opción superior** en términos de experiencia del alumno (todo en una sola actividad, flujo limpio con branching visual). Sin embargo, la exportación de datos es menos flexible para análisis cruzado. Si el análisis posterior es prioritario, Lección + Base de Datos sigue siendo preferible incluso con acceso al administrador.

### Implementación recomendada (Lección + Base de Datos):

1. Crear actividad Base de Datos con dos campos: `materia` (texto corto, obligatorio) y `nota` (número, obligatorio)
2. En la configuración de la Base de Datos, establecer "Condiciones de finalización" → "Require entries" → mínimo 1 entrada (o el número que consideres apropiado)
3. Crear actividad Lección con una única página de confirmación final
4. En la configuración de la Lección, sección "Restricciones de acceso" → agregar restricción por "Finalización de actividad" → seleccionar la Base de Datos → condición: marcada como completa
5. Indicar claramente en las instrucciones del curso el flujo: primero Base de Datos, luego Lección de confirmación
6. (Opcional) Crear una Página adicional visible solo para profesores con un formulario JS para subir el CSV exportado de Moodle y analizarlo con filtros y promedios automáticos

---

*Documento generado el 22/05/2026*
