# Especificación Formal: Sistema de Seguimiento de Trayectorias Estudiantiles
**Departamento de Ingeniería Industrial - Facultad de Ingeniería**
**Versión:** 2.0 (Máximo Detalle)

---

## 1. Introducción y Justificación
El presente documento define los requerimientos para un sistema de trazabilidad de trayectorias. La problemática se centra en dos fenómenos distintos pero interrelacionados:
*   **La Deserción:** El abandono definitivo o temporal de los estudios.
*   **El Alargamiento de la Carrera:** El incremento de la duración real sobre la teórica. La duración se define técnicamente como la **suma de todos los cuatrimestres** que el estudiante permanece en el sistema, incluyendo los periodos de "ida y vuelta".

Se establece la necesidad de una base de datos propia y proactiva alimentada por el **relevamiento voluntario** vinculado al Campus Virtual (Moodle), ante la imposibilidad técnica de operar sobre la base de datos cerrada de la facultad (SIU Guaraní).

## 2. Objetivos Estratégicos y "Momentos" de Intervención
El sistema debe permitir detectar situaciones de criticidad en tres momentos específicos estudiados de la deserción académica:

### 2.1. Deserción Temprana (Primer Nivel)
*   **Alcance:** Estudiantes que cursan el primer y segundo cuatrimestre (Ingreso).
*   **Contexto:** En esta etapa los alumnos no pertenecen estrictamente al departamento (cursan materias comunes de la facultad), lo que dificulta la tutoría departamental directa.
*   **Acción:** Implementación de un sistema de **Alerta Temprana** basado en patrones de criticidad detectados en el rendimiento de estas materias iniciales (Matemática, Física, Química).

### 2.2. Elongación y Retraso Intermedio
*   **Alcance:** Alumnos que han pasado a segundo año (alumnos propios de Industrial).
*   **Problema:** Estudiantes que van "más lento de lo que dice el plan", perdiendo materias cuatrimestre a cuatrimestre.
*   **Acción:** Detección de la ralentización respecto al ritmo teórico para asignar sistemas de tutoría par o profesional.

### 2.3. Deserción Tardía o "Estancamiento del Último Tramo"
*   **Alcance:** Alumnos con más del 85-90% de la carrera cursada.
*   **Problema:** Fenómeno donde el alumno deja de re-inscribirse o tarda entre **2 y 3 años adicionales** en rendir sus últimos compromisos tras haber completado la cursada. Factores críticos detectados:
    *   **Captación Laboral y Desmotivación Económica:** El alumno consigue un empleo con una remuneración que percibe como superior a la que espera obtener tras graduarse, lo que genera una pérdida de sentido sobre el esfuerzo final del título.
    *   **Factores Psicológicos:** Stress extremo o ataques de pánico ante la inminencia de la responsabilidad profesional del ingeniero.
*   **Acción:** Identificación de inactividad prolongada y oferta de canales de retorno guiado o planes de egreso flexibles que faciliten el cierre de la trayectoria.

## 3. Análisis de Alternativas y Factibilidad Técnica
En la fase de definición se han evaluado diversas opciones, estableciendo los siguientes criterios de selección:

*   **Alternativa A: Formularios Estándar (Google Forms / Excel):** Considerada el "piso mínimo de referencia". Se descarta como producto final por su incapacidad de gestionar lógica compleja, validaciones automáticas y visualización dinámica ("No me bromeen con algo que se hace en 20 minutos").
*   **Alternativa B: Integración Directa con SIU Guaraní:** Descartada por restricciones de seguridad institucional; el SIU es una base cerrada que no permite consultas externas en tiempo real. Esto obliga a la creación de una **Base de Datos Propia y Proactiva**.
*   **Alternativa C: Maquetas Estáticas (PowerPoint / Figma):** Descartadas como entregable final. El cliente exige un producto funcional y "comprable" que ejecute las acciones de alerta (referencia: "Dubai Chocolate").
*   **Solución Elegida: Sistema Web Embebido en Moodle:** Se opta por desarrollar un paquete/programa alojado en el entorno Moodle (LMS/NMS) por ser software libre, garantizar el acceso de todos los alumnos y permitir la centralización de datos en una base de datos departamental gestionable.

## 4. Alcance del Proyecto
El sistema se define como una plataforma de **trazabilidad, alerta y gestión de tutorías**, que servirá tanto de tablero de comando para la gestión académica como de interfaz de comunicación y autogestión para el estudiante.

## 4. Estrategia de Recolección y Relevamiento
La integridad del sistema depende de la calidad y periodicidad de los datos ingresados. Se establecen diversos canales para la captura de información.

### 4.1. Taxonomía Exhaustiva de Indicadores
El sistema debe permitir la carga y procesamiento de las siguientes variables, categorizadas según su impacto en la trayectoria:

#### A. Variables de Perfil de Base (Carga Única)
*   **Origen e Institución:** Tipo de secundario (Pública vs. Privada), lugar de procedencia y percepción del desempeño escolar previo.
*   **Indicadores Socio-Educativos:** Nivel educativo de la madre (predictor crítico de éxito académico identificado por el cliente).
*   **Situación Habitacional y Movilidad:** Si el estudiante alquila, lugar de origen y distancia/medios de transporte utilizados.
*   **Entorno Familiar:** Composición familiar y cantidad de personas a cargo.

#### B. Variables Dinámicas y Cualitativas (Carga Periódica)
*   **Laboral:** Status de empleo y carga horaria semanal.
*   **Factores de Riesgo Específicos:** 
    *   **Salud y Emocional:** Problemas de salud, estrés, ataques de pánico (específicamente relevantes en el tramo final).
    *   **Logística y Clima:** Dificultades de traslado, impacto de alertas meteorológicas que impidieron rendir o cursar.
    *   **Académico-Institucionales:** Superposición horaria, problemas con correlatividades por cambios de plan, dificultades con el método de enseñanza de una cátedra.
*   **Percepción de Cátedras:** Evaluación cualitativa de los docentes, comentarios que incomodaron al alumno o falta de claridad en la transmisión de contenidos.

### 4.2. Fases de Relevamiento y Fuentes
*   **Historial Retroactivo:** Al entrar al sistema, el alumno debe reconstruir su historia académica completa (aprobados y desaprobados) para generar una línea de tiempo válida de su trayectoria.
*   **Enfoque en Finales:** La actualización periódica debe incluir **finales rendidos de periodos anteriores**, permitiendo detectar "estancamiento" en materias cursadas hace tiempo.
*   **Incentivo y Obligatoriedad:** El sistema se integra con los **Talleres Transversales (2° a 5° año)**. Completar la encuesta es un requisito administrativo; el sistema debe avisar al docente si el alumno completó el trámite para permitir su aprobación.
*   **Detección Temprana (1° Año):** Se nutre de reportes directos de los docentes de Matemática, Física y Química sobre notas de parciales en tiempo real.

### 4.3. Calidad, Limpieza y Validación Proactiva
Para garantizar la fiabilidad del sistema en un entorno de carga voluntaria, se implementan procesos de auditoría de datos:
*   **Tratamiento de Incidencias Técnicas:** Identificación automática de "huecos" (datos faltantes en periodos específicos), duplicaciones de registros y outliers (ej. alumnos que declaran aprobar más materias de las físicamente posibles en un cuatrimestre).
*   **Gestión de la Veracidad y Validación Cruzada:** El sistema contrastará la información declarada por el alumno con los reportes de los docentes (ej. si el alumno declara desaprobada una materia donde el docente reportó aprobación).
*   **Incentivo por Transparencia:** Comunicación clara al estudiante de que la fidelidad de sus datos es el único camino para recibir una tutoría personalizada de calidad.
*   **Validación Humana:** Ante inconsistencias flagrantes, se activará un protocolo de validación personal o telefónica. Como señaló el cliente: "El estudiante intentará ser fiel si sabe que después tiene que explicar que mintió".
*   **Barra de Calidad:** La solución debe ser una herramienta de ingeniería con lógica de validación, no un simple formulario estático.

## 5. Especificación Funcional: Lógica e Indicadores
El sistema debe procesar la información recolectada mediante un motor de reglas dinámico que permita la toma de decisiones estratégicas.

### 5.1. Gestión de Roles y Niveles de Acceso
Se definen tres roles con permisos diferenciados:
1.  **Administrador Máster (Gestión Académica):** Responsable de configurar los parámetros de criticidad, gestionar usuarios y acceder a reportes globales de impacto (ej. para reformas de plan de estudios).
2.  **Tutor:** Perfil operativo encargado de gestionar su "pool" de alumnos asignados, registrar minutas de entrevistas y dar seguimiento a los compromisos de mejora.
3.  **Estudiante:** Usuario final con permisos exclusivos para carga de encuestas, visualización de su tablero de rendimiento y acceso directo al **"Botón de Auxilio"** (Canal de solicitud de ayuda urgente).

### 5.2. Motor de Indicadores y Semáforos (Reglas de Negocio)
La lógica de asignación de alarmas (semáforos) debe ser **totalmente parametrizable** por el Administrador sin requerir re-programación:
*   **Interferencia Laboral y Afinidad:** Evaluar el cruce entre la carga horaria semanal y el rendimiento académico. No es un dato estático; el sistema debe alertar si el alumno aumenta su carga horaria laboral mientras disminuye su rendimiento de parciales/finales.
*   **Indicador de "Intento vs. Logro":** Diferenciar entre el alumno que rinde 4 y aprueba 4 (lento pero efectivo) vs. el que intenta 6 y reprueba 3 (estado crítico).
*   **Desfase de Cuatrimestres:** Detección de alumnos que cursan materias de años muy distantes entre sí.
*   **Sucesión de Eventos Críticos:** Alarmas por recursado múltiple de una misma materia o la reprobación reiterada (2 o 3 veces) de un examen final (posible indicador de conflicto personal o docente).
*   **Filtros Dinámicos:** Capacidad de agrupar variables (ej. agrupar por educación de la madre o situación laboral) para descubrir nuevos patrones estadísticos.

### 5.3. Gestión de Tutorías e Interfaz de Comunicación
*   **Asignación de Casos:** El sistema asignará alumnos estancados o con patrones de riesgo a tutores específicos.
*   **Memoria de Intervención:** Registro cualitativo de cada entrevista, el cual pasará a integrar la historia académica del alumno para seguimiento futuro.
*   **Canales de Notificación:** Implementación de alertas por correo electrónico o notificaciones integradas en el campus para citar a alumnos en situación crítica.

### 5.4. Visualización y Dashboards (Estilo Power BI)
El sistema debe ofrecer una visualización de datos dinámica e interactiva que permita diferentes niveles de análisis:

*   **Tablero del Estudiante ("Mi Perfil"):**
    *   **Visualización Comparativa:** Gráficos que muestren el avance propio frente al "tiempo teórico" del plan y frente al promedio de su cohorte (año de ingreso).
    *   **Tono Motivacional:** La interfaz debe estar diseñada para incentivar la finalización, no para castigar el retraso (fomentar la empatía con el usuario).
*   **Tablero de Gestión (Directivo/Tutor):**
    *   **Análisis Macro:** Resultados globales de rendimiento por materia, nivel de deserción por año y eficacia de las tutorías.
    *   **Drill-Down (Micro):** Capacidad de entrar en el perfil de un estudiante puntual, ver su trayectoria completa y las observaciones cualitativas de sus tutores.
    *   **Alertas de Cátedra y Contraste de Rendimiento:** Identificación de materias con picos de desaprobados. El sistema debe permitir el **contraste automático** entre la estadística de aprobación (ej. 90% aprobados) y la percepción del alumno (ej. 0% de satisfacción), para detectar cátedras con problemas de clima o métodos pedagógicos deficientes. Esto permitirá al Director del Departamento la **intervención directa con los docentes** responsables (ej. casos donde la tasa de aplazos se duplica).
    *   **Monitoreo de la Gestión de Tutorías:** Tablero de control para que el Director supervise la actividad de los tutores, asegurando que las entrevistas se realicen y se registren en tiempo y forma.
    *   **Exportación para Investigación:** Capacidad de exportar estructuras de datos que sirvan para alimentar las investigaciones académicas del Departamento sobre deserción.
*   **Canal de Solicitud de Ayuda (Botón de Auxilio):** El sistema debe proveer una interfaz directa (pantalla de asistencia) donde el alumno en situación de crisis pueda solicitar intervención inmediata de los tutores, centralizando reclamos y consultas (ej. información sobre el sistema de becas) que usualmente se dispersan en páginas externas.

### 5.5. Mapa Preliminar de Interfaces (Estructura de Pantallas)
Basado en los requerimientos funcionales, el sistema debe contemplar al menos los siguientes módulos de visualización:
1.  **Dashboard de Gestión Estratégica:** Pantalla principal para el Director con métricas globales, alertas de cátedra y reportes de investigación.
2.  **Módulo de Supervisión de Tutorías:** Interfaz para el Administrador para monitorear el desempeño del pool de tutores.
3.  **Consola de Seguimiento Individual (Tutor):** Pantalla de gestión de casos asignados, historial de entrevistas y semáforos de riesgo.
4.  **Tablero de Autogestión Estudiantil:** Perfil del alumno, visualización comparativa (Plan vs. Cohorte) y barra de progreso.
5.  **Centro de Relevamiento (Encuestas):** Interfaz dinámica de carga periódica (materia por materia) y carga histórica inicial.
6.  **Pestaña de Auxilio Urgente:** Interfaz de acceso rápido para solicitudes de intervención inmediata académica o personal.

### 5.6. Requisitos de Interfaz y UX (User Experience)
*   **Optimización del Tiempo:** Las encuestas deben ser breves y de navegación intuitiva para evitar que el estudiante las perciba como un proceso tedioso (riesgo de deserción del propio sistema).
*   **Estética "Premiun":** Siguiendo la premisa del cliente ("Chocolate Dubai"), la interfaz debe ser visualmente atractiva, moderna y profesional, superando cualquier herramienta de recolección de datos convencional.
*   **Embebido en el Campus:** Integración visual total con el entorno Moodle para que el acceso sea fluido y natural.
*   **Canal de Alivio de Conflictos:** El sistema debe actuar como el canal oficial de escucha para evitar que las problemáticas solo se manifiesten en páginas de quejas externas o en el Centro de Estudiantes una vez que la situación es crítica.

## 6. Infraestructura Técnica y Mantenimiento
El sistema debe diseñarse bajo principios de sostenibilidad y bajo costo, aprovechando ecosistemas existentes.

### 6.1. Ecosistema LMS (Moodle)
Dada la gratuidad y apertura de Moodle, el sistema debe integrarse profundamente en este entorno (NMS/LMS):
*   **Identidad y Acceso (SSO):** Uso de las credenciales de campus para evitar la fragmentación de usuarios.
*   **Aprovechamiento de APIs:** Uso de la documentación pública de Moodle para interoperabilidad y posible embebido de encuestas.
*   **Administración:** Distinguir entre la administración docente (gestión de contenidos) y la administración técnica de la plataforma.

### 6.2. Sostenibilidad y Mantenimiento
*   **Mantenimiento Técnico:** Backups, seguridad de la base y actualizaciones de servidor; debe ser lo más automatizado posible para no depender de personal informático exclusivo de tiempo completo.
*   **Mantenimiento Funcional:** El sistema debe ser lo suficientemente flexible para permitir cambios en las encuestas, incorporación de nuevas materias o modificaciones en los planes de estudio sin generar inconsistencias en los datos históricos (evitar que la base "se muera" por cambios administrativos).
*   **Software Libre:** Uso exclusivo de tecnologías open source conforme a la restricción presupuestaria ("no poner un peso"). El departamento no posee presupuesto para licencias.

## 7. Marco Legal y Tratamiento de Información Sensible
El manejo de datos sobre salud, situación económica y rendimiento docente exige cumplimiento estricto:
*   **Ley Nacional 25.326 (Protección de Datos Personales):** Obligación de registrar las bases de datos generadas ante el organismo correspondiente en Argentina.
*   **Identificación vs. Anonimato:** 
    *   **Identificación Proactiva:** A diferencia de sistemas puramente estadísticos, aquí se requiere identificar nominalmente al alumno en riesgo para permitir la intervención directa (llamado a entrevista) por parte del tutor y la gestión central.
    *   **Privacidad por Diseño:** Las visualizaciones estadísticas de los dashboards de gestión deben estar anonimizadas o agregadas para proteger la identidad del alumno fuera del entorno restringido de tutoría.
*   **Seguridad y Control de Acceso:** Implementación de protocolos de cifrado y permisos jerárquicos que garanticen que **solo el personal autorizado** acceda a la información íntima del estudiante.

## 8. Metodología de Trabajo y Entregables
El proyecto se rige por un esquema de consultoría con hitos de validación frecuente.

### 8.1. Planificación de Sprints y Seguimiento
*   **Ritmo Agile:** Sprints de 2 semanas con reuniones de agenda donde cada equipo validará sus ideas antes de consolidarlas.
*   **Validación de Concepto:** Las reuniones servirán para filtrar ideas inviables ("esto ya lo probamos y no funciona") antes de invertir tiempo en desarrollo.

### 8.2. Organización del Equipo y Entregables
El equipo de la Consultora deberá estructurarse bajo los roles definidos administrativamente:
*   **Investigadores/Encuestadores:** Foco en la recolección de datos y benchmarking.
*   **Líder de Gestión (Manager):** Coordinación de sprints y visión organizacional.
*   **Desarrolladores:** Implementación técnica del producto "Dubai Chocolate".

#### Entregables de Producto
1.  **Memoria Técnica y de Requerimientos:** Este documento ampliado y validado.
2.  **Producto Funcional ("Dubai Chocolate"):** Un prototipo que sea "comprable" por su calidad estética y lógica, no una simple maqueta.
3.  **Mapa de Procesos:** Diseño de cómo interactuarán físicamente los roles (Director, Tutor, Docente, Alumno) con el sistema.

## 9. Requerimientos de Investigación (Benchmarking)
La consultora tiene la obligación de profundizar en el dominio del problema mediante:
*   **Investigación de Patrones de Deserción:** Análisis de métricas estándar en el sistema universitario argentino para generar indicadores con base científica.
*   **Benchmarking de Fallos y Errores Previos:** Búsqueda y análisis de sistemas similares que hayan fallado en otras facultades, identificando los motivos de su fracaso para evitar el re-trabajo y la repetición de errores comunes.
*   **Exploración de Entorno (Administrador de Moodle):** Salto cualitativo del rol de estudiante al de administrador/docente para entender las capacidades reales de integración de la plataforma.Pasar del uso básico de Moodle a la comprensión de su arquitectura administrativa.El Departamento facilitará el **acceso a una instancia de prueba o curso con privilegios elevados** para que la Consultora explore la arquitectura administrativa y las APIs disponibles en Moodle.

## 10. Logística de Implementación y Prueba de Escritorio
*   **Barra de Calidad (Ingeniería vs. Herramientas Triviales):** El cliente establece que una solución tipo "Google Forms + Power BI" es un piso mínimo aceptable solo para un usuario básico. Como ingenieros, se exige un producto que integre lógica propia, validaciones automáticas y una interfaz profesional que supere dicha simplicidad de manera manifiesta.
*   **Población de Datos Reales:** Queda estrictamente prohibido el uso de datos hipotéticos o estáticos ("agarrar una guitarra y componer una canción"). El equipo debe recolectar datos reales de sus pares y otros grupos de alumnos para poner a prueba la lógica de semáforos y alertas ante situaciones reales.
*   **Sesgo de Muestra:** Se debe documentar y mitigar el sesgo si solo se utilizan estudiantes de informática, reconociendo que no son representativos de la totalidad de perfiles de la facultad.
*   **Visión Organizacional:** Requisito de presentar una descripción de la estructura del Departamento tal como la percibe la Consultora, para alinear la mirada con la realidad del cliente.
*   **Escalabilidad e IA:** Dejar abierta la infraestructura para el futuro procesamiento de lenguaje natural (IA) sobre los campos cualitativos extensos.

---
**Fin del Documento**
