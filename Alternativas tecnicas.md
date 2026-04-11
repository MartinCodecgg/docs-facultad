*   **Alternativa A: Formularios Estándar (Google Forms / Excel):** Considerada el "piso mínimo de referencia". Se descarta como producto final por su incapacidad de gestionar lógica compleja, validaciones automáticas y visualización dinámica ("No me bromeen con algo que se hace en 20 minutos").
Demasiado simple para un trabajo final.

*   **Alternativa B: Integración Directa con SIU Guaraní:** Descartada por restricciones de seguridad institucional; el SIU es una base cerrada que no permite consultas externas en tiempo real. Esto obliga a la creación de una **Base de Datos Propia y Proactiva**.

*   **Alternativa C: Maquetas Estáticas (PowerPoint / Figma):** Descartadas como entregable final. El cliente exige un producto funcional y "comprable" que ejecute las acciones de alerta.
Demasiado simple para un trabajo final.

*   **Sistema Web Embebido en Moodle:** Se opta por desarrollar un paquete/programa alojado en el entorno Moodle (LMS/NMS) por ser software libre, garantizar el acceso de todos los alumnos y permitir la centralización de datos en una base de datos departamental gestionable.

La idea estaria en aprender a usar moodle para poder crear el sistema, es software libre, no requiere costo.

El Departamento puede facilitar el **acceso a una instancia de prueba o curso con privilegios elevados** para que la Consultora explore la arquitectura administrativa y las APIs disponibles en Moodle.

Es decir podemos desarrollar el sistema de forma aislada por nuestra cuenta y luego si el proyecto resulta convincente, luego se puede migrar totalmente el sistema al moodle real de la facultad.

**Ventajas**:
1. Costo inicial y a futuro cero, inicial es cero porque podemos diseñar el sistema en red local y en futuro se integraria directamente al campus actual, no requiriendo servidores propios ni algun costo adicional.
2. Se integra completamente en el campus, pasa a ser una extension no un sistema aparte.
3. Su desarrollo no requiere programacion, se diseña manualmente, moviendo elementos, configurando, etc.
4. En cuanto a las bases de datos, se crean sin programarlas, arrastrando y soltando o eligiendo las tablas que vamos a utilizar.
5. Parece ser la opcion mas directa y adaptable al sistema actual de la facultad.

**Desventajas**:
1. Es un sistema que requiere de un aprendizaje previo, muy especifico del sistema. Es aprendisaje especifico que muy probablemente no nos sume tanta experiencia util como programadores como en el caso de diseñar una pagina web.
2. En comparacion a una pagina web programada, las opciones de personalizacion son mas limitadas, estamos mas limitados por lo que el sistema permite.
3. Una pagina web puede verse finalmente mucho mejor que un moodle, mas herramientas, menos limitaciones.
4. Hay que diseñar todo el sistema moodle manualmente desde cero, en comparacion a una pagina web donde podemos decirle a una IA que nos diseñe el frontend, backend, etc y jugamos a copiar y pegar.

Secciones a elaborar en moodl.
Frontend: Desarrollar completamente de forma manual, los paneles, las paginas, paginas para estudiantes, profesores etc.
Backend: El backend es diferente, seria mucho mas facil que diseñar el backend de una pagina web, el cual tenemos que programarlo desde cero. En moodle, el backend es mas bien una configuracion de la base de datos, de las tablas, de las relaciones, de los campos, etc. Es decir, no hay que programar, sino configurar.

**Secciones a desarrollar:**

Mapa Preliminar de Interfaces (Estructura de Pantallas)
Basado en los requerimientos funcionales, el sistema debe contemplar al menos los siguientes módulos de visualización:
1.  **Dashboard de Gestión Estratégica:** Pantalla principal para el Director con métricas globales, alertas de cátedra y reportes de investigación.
2.  **Módulo de Supervisión de Tutorías:** Interfaz para el Administrador para monitorear el desempeño del pool de tutores.
3.  **Consola de Seguimiento Individual (Tutor):** Pantalla de gestión de casos asignados, historial de entrevistas y semáforos de riesgo.
4.  **Tablero de Autogestión Estudiantil:** Perfil del alumno, visualización comparativa (Plan vs. Cohorte) y barra de progreso.
5.  **Centro de Relevamiento (Encuestas):** Interfaz dinámica de carga periódica (materia por materia) y carga histórica inicial.
6.  **Pestaña de Auxilio Urgente:** Interfaz de acceso rápido para solicitudes de intervención inmediata académica o personal.

Estas 6 paginas en moodle requiere diseño manual.

En una pagina web podemos decirle a una IA que las diseñe, una pagina por prompt.

**Pagina/Sistema Web (Programado):**

Diseñar desde cero la pagina web usando IA.
El frontend es mas delegable completamente a la IA, el backend requiere supervision.

A diferencia de moodle, la pagina web si tiene un costo debido a el hosting, el alojamiento de la base de datos.
Los costes varian respecto de la tecnologia backend que se use para desarrollar la pagina web.

**Esto atenta directamente contra el objetivo de que sea un proyecto de costo cero.**
**Cita Textual:**

>La cita textual exacta donde Morcela menciona la restricción presupuestaria se encuentra en la línea 131 de la transcripción original:

>"Y como nosotros no queremos poner un peso, tiene que ser open... software libre... hay herramientas de NMS... LMS... gestión del aprendizaje."

Más adelante, ante la pregunta técnica de Fernando sobre la mantenibilidad y los costos, Antonio refuerza la idea en la línea 154:

>"Por eso tiene que ser algo lo más automatizado posible... porque no vamos a tener presupuesto para un tipo que esté las 24 horas manteniendo el código."

Estas citas confirman que la elección tecnológica debe priorizar la gratuidad absoluta de licencias y la mínima necesidad de mantenimiento pago.

La distincion fundamental esta entre elegir un backend de PHP vs un Backend de node.js.
El backend de PHP es notoriamente mas barato aunque node.js es mas moderno y mas rapido.
Dado el bajo tragico de estudiantes, PHP parece ser la mejor opcion, sumado al objetivo de diseñar un sistema de bajo costo.

Costos:

1. (BACKEND DE PHP) Don web: 8000 ARS mensuales o 2500 ARS mensuales contratando una suscripcion Anual
2. (BACKEND DE NODE.JS): Supabase u otros, 20usd mensuales o mas.

Entonces

**Ventajas:**
1. 