# Especificación Formal: Sistema de Seguimiento de Trayectorias Estudiantiles
**Departamento de Ingeniería Industrial - Facultad de Ingeniería**

---

## 1. Introducción y Justificación
El presente documento tiene como objetivo formalizar los requerimientos para el desarrollo de una herramienta de gestión orientada al seguimiento integral de las trayectorias estudiantiles. La problemática central abordada es la deserción (en sus diversas fases) y el alargamiento de las carreras, fenómenos que impactan en la eficiencia académica del Departamento.

Dada la imposibilidad de acceder a bases de datos cerradas como el SIU Guaraní para integraciones dinámicas en tiempo real, se establece la necesidad de un sistema de **relevamiento voluntario y proactivo** vinculado al Campus Virtual (Moodle).

## 2. Objetivos Estratégicos
El sistema debe permitir la intervención en tres momentos críticos detectados:

### 2.1. Mitigación de la Deserción Temprana
*   **Alcance:** Ingresantes en su primer y segundo cuatrimestre.
*   **Problema:** Alta tasa de abandono en materias básicas extra-departamentales.
*   **Acción:** Relevamiento de notas de parciales de materias "troncales" (Matemática, Física, Química) para detección de patrones de riesgo antes del cierre del cuatrimestre.

### 2.2. Control de la Elongación de la Carrera
*   **Alcance:** Alumnos a partir del segundo año (propiamente de la carrera de Industrial).
*   **Problema:** Ritmo de avance inferior al plan teórico de estudios.
*   **Acción:** Identificación de situaciones de recursado múltiple o trabas en correlativas.

### 2.3. Prevención de la Deserción Tardía o "Estancamiento Final"
*   **Alcance:** Estudiantes con >85% de avance curricular (Tramo Final).
*   **Problema:** Fenómeno donde el alumno, tras cursar casi toda la carrera, tarda entre 2 y 3 años adicionales en recibirse o abandona temporalmente por desmotivación, ataques de pánico o prioridades laborales.
*   **Acción:** Relevamiento de inactividad de finales y falta de re-inscripción para activar acompañamiento emocional o académico.

## 3. Alcance del Proyecto
El sistema se define como una plataforma de **trazabilidad, alerta y gestión de tutorías**, que servirá tanto de tablero de comando para la gestión académica como de interfaz de comunicación y autogestión para el estudiante.

## 4. Estrategia de Recolección y Relevamiento
La integridad del sistema depende de la calidad y periodicidad de los datos ingresados. Se establecen diversos canales para la captura de información.

### 4.1. Fuentes de Información e Indicadores Clave
Se deben relevar datos que la literatura académica y la experiencia previa del Departamento identifican como predictores:
*   **Datos de Base (Unica vez):** Nivel educativo de la madre (indicador crítico de éxito académico), tipo de secundario (público/privado), rendimiento en el secundario y lugar de origen.
*   **Datos Dinámicos (Cuatrimestrales):** Situación laboral (horas de trabajo), personas a cargo, situación habitacional (alquiler) y percepción cualitativa del rendimiento propio.
*   **Reportes de Cátedra:** Específicamente para primer año, se solicitarán las notas de parciales a los docentes para actuar en tiempo real sin esperar al cierre de actas en Guaraní.
3.  **Registros de Tutoría:** Información generada durante las entrevistas entre tutores y alumnos (fuente cualitativa rica en detalles).
4.  **Campus Virtual (Moodle):** Fuente de validación de identidad y plataforma de acceso unificada.

### 4.2. Fases de Carga de Datos
*   **Carga Histórica Inicial:** Todo alumno que ingrese al sistema por primera vez deberá completar su historial académico completo (materias aprobadas, años de cursada, etc.) para establecer su "línea base".
*   **Actualización Periódica:** Cada cuatrimestre se solicitará la actualización de datos dinámicos y, fundamentalmente, el resultado de **exámenes finales rendidos de cualquier período**, para capturar el estado real del avance (dato que el alumno tiene "a flor de piel").
*   **Validación por "Hitos":** Se vincula la obligatoriedad de carga a la aprobación de los "Talleres Transversales" (desde 2° hasta 5° año inclusive). El sistema debe informar el estado de completitud de la encuesta como requisito administrativo.

### 4.3. Calidad y Validación del Dato
Dado el carácter voluntario, el sistema implementará:
*   **Detección de Outliers:** Alarmas automáticas ante datos incoherentes (ej. materias aprobadas que superan la capacidad lógica de un cuatrimestre).
*   **Validación Cruzada:** Contraste parcial con la información conocida por los docentes y la gestión (ej. si el alumno declara desaprobada una materia donde el docente reportó aprobación).
*   **Incentivo por Transparencia:** Comunicación clara al alumno de que la fidelidad de los datos mejora la calidad de la tutoría y ayuda que recibirá.

## 5. Especificación Funcional del Sistema
El sistema debe trascender la simple recolección y convertirse en una herramienta de análisis y acción.

### 5.1. Gestión de Roles y Permisos
Se definen tres niveles de acceso jerárquicos:
1.  **Administrador Máster (Gestión Académica):** Control total, gestión de usuarios, configuración global del sistema y acceso a tableros de resultados globales.
2.  **Tutor:** Visualización de registros de alumnos asignados, carga de minutas de entrevistas, gestión de estados de criticidad y seguimiento individual.
3.  **Estudiante:** Carga de encuestas, acceso a su tablero personal ("Mi Perfil Académico") y canal para envío de solicitudes de ayuda o consultas.

### 5.2. Motor de Indicadores y Semáforos (Parametrización)
Un requerimiento **crítico** es que el sistema no tenga criterios de riesgo rígidos ("hardcoded").
*   **Lógica de Desfase:** El sistema debe detectar no solo la cantidad de materias, sino el desfase entre cuatrimestres y años (ej. alumnos cursando simultáneamente materias de 2°, 3° y 4° año).
*   **Sucesión de Eventos:** Alerta automática ante el recursado múltiple de una misma materia o la reprobación consecutiva de exámenes finales.

### 5.3. Gestión de Tutorías y Comunicación
*   **Pool de Tutores:** El sistema gestionará un conjunto de tutores (no necesariamente uno por asignatura) que actuarán sobre el universo de alumnos con criticidad detectada.
*   **Interfaz de Mensajería/Alertas:** Envío de correos o notificaciones integradas para citar a alumnos detectados en situación crítica.

### 5.4. Visualización y Dashboards
*   **Vista Estudiante:** Comparativa gráfica de su avance respecto al "plan teórico" y respecto al "promedio de su cohorte". Debe ser motivacional, no punitiva.
*   **Vista Gestión:** Tablero (estilo Power BI embebido) con indicadores agregados por materia, docente, o situación socio-económica para toma de decisiones estratégicas.

## 6. Marco Técnico e Infraestructura
Dada la restricción presupuestaria y la necesidad de integración, se establecen las siguientes pautas:

### 6.1. Ecosistema Moodle
El sistema debe ser compatible o estar embebido en el Campus Virtual (Moodle). Se deben aprovechar las APIs de Moodle o sus mecanismos de plugin para:
*   **Single Sign-On (SSO):** El alumno no debe crear un usuario nuevo; debe ingresar con sus credenciales del campus.
*   **Interfaz Unificada:** La visualización de datos debe sentirse como parte de la experiencia del campus.

### 6.2. Mantenibilidad y Costo
*   **Tecnologías Abiertas:** Se priorizará el uso de herramientas de código abierto (Open Source).
*   **Simplicidad Técnica:** Se deben evitar soluciones que requieran un mantenimiento informático complejo o licencias costosas (foco en la sostenibilidad a largo plazo).

## 7. Marco Legal y Seguridad
El manejo de información sobre el rendimiento académico, situación económica y familiar del estudiante se considera **datos sensibles**.
*   **Ley 25.326 (Protección de Datos Personales):** El desarrollo debe cumplir con la normativa argentina, garantizando que los datos se usen solo para los fines declarados (tutoría).
*   **Privacidad por Diseño:** Solo los tutores asignados y la gestión central pueden ver datos identificables. El resto de las visualizaciones deben ser anonimizadas o agregadas estadísticamente.

## 8. Metodología de Trabajo y Entregables
El proyecto se ejecutará bajo un esquema de **Metodologías Ágiles** coordinado por el Departamento.

### 8.1. Planificación por Sprints
*   **Ciclos de 2 semanas:** Reuniones de avance (Sprints) para validar la dirección del desarrollo.
*   **Validación Temprana:** Se priorizará la creación de un prototipo funcional ("Prueba de Escritorio") con datos reales o simulados antes de avanzar en estética.

### 8.2. Entregables Finales
1.  **Informe Técnico Detallado:** Memoria del proceso de desarrollo y licitación de requerimientos.
2.  **Producto Funcionando:** Un prototipo con lógica real que supere la maqueta estática (referencia: "Chocolate Dubai", un producto cuya calidad genere deseo de uso inmediato).
3.  **Plan de Procesos y Roles:** Manual de cómo la organización debe usar la herramienta (capacitación y flujo de trabajo).

## 9. Requerimientos de Investigación y Benchmarking
El equipo de desarrollo (Consultora) tiene la obligación de profundizar en el dominio del problema antes de finalizar el diseño:
*   **Investigación de Deserción:** Análisis de métricas estándar en el sistema universitario argentino para no "preguntar lo que ya se sabe".
*   **Exploración de Moodle:** Salto cualitativo del rol "estudiante" al rol "administrador/docente" para entender las capacidades reales de integración.
*   **Benchmarking:** Búsqueda de sistemas similares en otras facultades para extraer mejores prácticas y evitar errores comunes.

## 10. Logística de Implementación y Pruebas
*   **Barra de Calidad (No MVP trivial):** El cliente establece que una solución tipo "Google Forms + Power BI" es el piso mínimo aceptable solo para un usuario básico. Como ingenieros, se exige un producto que integre lógica propia y una interfaz profesional que supere dicha simplicidad.
*   **Prueba de Escritorio con Datos Reales:** El Departamento NO proveerá una base de datos inicial...
*   **Sesgo de Muestra:** Se debe documentar y mitigar el sesgo de la muestra si solo se utilizan estudiantes de informática, reconociendo que no son representativos de la totalidad de perfiles de la facultad.
*   **Visión Organizacional:** En las instancias de avance, la Consultora debe presentar una descripción de la estructura del Departamento de Ingeniería Industrial tal como la percibe. Esto sirve para alinear la mirada del técnico con la realidad del cliente.
*   **Potencial de IA:** Se deja abierta la posibilidad (como deseo del cliente) de integrar herramientas de procesamiento de lenguaje natural para detectar patrones en las respuestas cualitativas extensas (reemplazando el análisis manual de Excel).

---
**Fin del Documento**
