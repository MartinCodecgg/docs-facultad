# Alternativas Técnicas — Análisis y Selección de Plataforma

## 1. Alternativas Descartadas

Las siguientes opciones fueron evaluadas y descartadas en una etapa preliminar por no cumplir con los requisitos mínimos del proyecto.

**Alternativa A — Formularios Estándar (Google Forms / Excel):** Considerada el "piso mínimo de referencia". Se descarta como producto final por su incapacidad de gestionar lógica compleja, validaciones automáticas y visualización dinámica. Es demasiado simple para el alcance del trabajo.

**Alternativa B — Integración Directa con SIU Guaraní:** Descartada por restricciones de seguridad institucional. El SIU es una base cerrada que no permite consultas externas en tiempo real, lo que obliga a la creación de una base de datos propia y proactiva por fuera de ese sistema.

**Alternativa C — Maquetas Estáticas (PowerPoint / Figma):** Descartadas como entregable final. El cliente exige un producto funcional que ejecute las acciones de alerta, no una representación visual estática del sistema.

---

## 2. Restricción Presupuestaria — Contexto Institucional

Antes de analizar las alternativas viables, es necesario establecer la restricción central que condiciona la elección tecnológica: el costo cero.

> "Y como nosotros no queremos poner un peso, tiene que ser open... software libre... hay herramientas de NMS... LMS... gestión del aprendizaje." — Antonio Morcela, línea 131 de la transcripción.

> "Por eso tiene que ser algo lo más automatizado posible... porque no vamos a tener presupuesto para un tipo que esté las 24 horas manteniendo el código." — Antonio Morcela, línea 154 de la transcripción.

Esta restricción impacta directamente en la elección tecnológica y debe ser considerada en cada alternativa. Sin embargo, vale aclarar que la finalidad del proyecto es la resolución del problema planteado, no necesariamente entregar algo directamente implementable por la facultad. En ese sentido, el costo cero es una consideración importante que hay que tener en cuenta y argumentar, pero no es una restricción fija e inamovible. Un sistema en red local no tiene costo en ninguna de las dos alternativas viables, y si el proyecto pasa a producción en el futuro, esa decisión y su financiamiento le corresponden a la institución.

---

## 3. Entregable Esperado

Lo ideal es un sistema listo para producción. Sin embargo, el entregable aceptado y válido es un sistema funcional en red local que demuestre todo el trabajo realizado y que, en lo posible, tenga capacidad de migrarse a producción en el futuro. Ambas alternativas viables contemplan este esquema de desarrollo.

---

## 4. Alternativas Viables

### Alternativa 1 — Sistema desarrollado en Moodle (localhost)

#### ¿En qué consiste?

Desarrollar el sistema íntegramente dentro de Moodle, instalado en una máquina local con acceso de administrador total.

Una ventaja inicial relevante es que Moodle no se construye desde cero. El sistema ya trae resueltos de fábrica el login, el sistema de roles, los perfiles de usuario, la navegación entre páginas y la estructura general del campus. El equipo arranca desde una base funcional y le agrega funcionalidades encima. En una página web, en cambio, todo eso hay que construirlo desde cero: login, manejo de sesiones, navegación, estructura base y todo lo demás. Sin embargo, esta ventaja inicial se va achicando a medida que las funcionalidades complejas del sistema (semáforos, dashboards, historial de tutorías) requieren PHP de todas formas en ambos casos. Moodle es software libre, no requiere licencia ni costo de servidor durante el desarrollo. El sistema se presenta corriendo en red local, y si el proyecto es aprobado, una persona con acceso al servidor institucional puede migrar el sistema al Moodle real de la facultad.

El entorno local requerido es el mismo que usa cualquier proyecto PHP: XAMPP o Laragon (Windows), Apache + MySQL + PHP.

#### Sobre el desarrollo

El documento original afirmaba que Moodle no requiere programación. Esto es parcialmente incorrecto para el alcance de este proyecto. Existe una distinción importante:

Las funcionalidades básicas como encuestas simples, roles y permisos, notificaciones por email y perfiles de usuario son configurables visualmente sin código. Sin embargo, las funcionalidades centrales del sistema, específicamente los semáforos de riesgo parametrizables, los dashboards con drill-down, el historial de tutorías y el contraste automático aprobación vs. percepción, requieren desarrollo en PHP mediante plugins a medida. No son configurables visualmente.

El documento original también afirmaba que las bases de datos se crean arrastrando y soltando. Esto aplica únicamente al módulo "Base de Datos" de Moodle, que sirve para estructuras simples. Las relaciones complejas entre entidades (alumno → tutor → historial → alertas → semáforos) requieren intervención en la base de datos interna de Moodle, que tiene su propio esquema y no es modificable de forma visual.

#### Rol de la IA en este contexto

La IA puede generar el código PHP necesario para los plugins. Sin embargo, la IA tiene considerablemente menos material de entrenamiento sobre la API interna de Moodle que sobre desarrollo web estándar. Los plugins de Moodle tienen convenciones específicas, estructura de archivos propia y funciones internas particulares. En la práctica, el código generado por la IA para Moodle va a requerir más depuración y comprensión del equipo que el código web estándar.

#### Estimación de PHP necesario por pantalla

| Pantalla | PHP necesario |
|---|---|
| Dashboard de Gestión Estratégica | Sí, mucho |
| Módulo de Supervisión de Tutorías | Sí, mucho |
| Consola de Seguimiento Individual (Tutor) | Sí, moderado |
| Tablero de Autogestión Estudiantil | Sí, moderado |
| Centro de Relevamiento (Encuestas) | Poco o nada |
| Pestaña de Auxilio Urgente | Poco o nada |

#### Ventajas

1. **Costo cero sostenido:** Durante el desarrollo no hay ningún costo. Si el proyecto migra al Moodle real de la facultad, tampoco hay costo adicional, ya que el servidor institucional ya existe.
2. **Integración natural con el campus:** Al estar dentro de Moodle, el sistema es una extensión del campus, no un sistema externo. Los alumnos acceden desde el entorno que ya usan.
3. **Autenticación resuelta:** Los alumnos ya tienen usuario y contraseña del campus. No hay que construir un sistema de login desde cero.
4. **Mantenimiento delegado:** Las actualizaciones del servidor y la seguridad del entorno las maneja la facultad, no el equipo.

#### Desventajas

1. **Aprendizaje específico de poco valor profesional:** El conocimiento adquirido sobre el funcionamiento interno de Moodle es difícilmente transferible a otros contextos. No suma como experiencia de programación general.
2. **Diseño de pantallas completamente manual:** Todas las interfaces (paneles, páginas de estudiante, tutor, director, etc.) deben construirse manualmente dentro de Moodle: configurando elemento por elemento, moviendo bloques, ajustando cada sección a mano. No hay forma de delegar esto a una IA. En contraste, en una página web cada pantalla puede generarse con un prompt describiendo lo que se quiere, y la IA entrega el código directamente.
2. **Personalización funcional limitada:** Las restricciones no son solo estéticas. Ciertas lógicas de negocio directamente no son implementables dentro de Moodle sin salir del sistema visual y programar plugins, y aún con plugins hay límites.
3. **La IA ayuda menos:** Generar código para plugins de Moodle es menos confiable con IA que generar código web estándar, lo que implica más trabajo de depuración manual.
4. **Dependencia de la administración institucional para el deploy:** Para migrar al Moodle real, instalar plugins y configurar APIs, se necesita un administrador con acceso al servidor institucional. El ritmo del deploy final no depende solo del equipo.
5. **Riesgo tardío:** Las funcionalidades más complejas (semáforos, dashboards) pueden presentar incompatibilidades con el Moodle real que no son detectables durante el desarrollo en localhost. Este riesgo se descubre tarde.

---

### Alternativa 2 — Página web en red local (PHP + MySQL)

#### ¿En qué consiste?

Desarrollar el sistema como una aplicación web estándar usando PHP y MySQL, corriendo en un servidor local (XAMPP o Laragon). El sistema se presenta en red local exactamente igual que en el caso de Moodle. Si el proyecto es aprobado, se contrata hosting y se migra. El costo de hosting aparece únicamente si el proyecto avanza a producción, no durante el desarrollo ni la presentación.

El stack local es idéntico al de Moodle: XAMPP o Laragon, Apache, MySQL, PHP. Si el equipo ya tiene ese entorno instalado para evaluar Moodle, no hay ningún costo adicional de configuración para arrancar con esta alternativa.

#### Sobre el desarrollo

El frontend es ampliamente delegable a la IA. Cada pantalla puede generarse con un prompt específico describiendo la interfaz deseada. El backend en PHP requiere supervisión del equipo, pero al ser código web estándar la IA lo genera con mucha mayor confiabilidad que en el caso de los plugins de Moodle.

#### Costos si se migra a producción

| Tecnología | Proveedor | Costo aproximado |
|---|---|---|
| PHP + MySQL | DonWeb (mensual) | $8.000 ARS/mes |
| PHP + MySQL | DonWeb (anual) | $2.500 ARS/mes |
| Node.js | Supabase u otros | 20 USD/mes o más |

Dado el tráfico esperado (estudiantes universitarios de un departamento) y el objetivo de bajo costo, PHP es la opción más adecuada si se llega a producción. Node.js queda descartado por costo.

Existen opciones gratuitas como Cloudflare Workers + D1, pero requieren conocimiento técnico específico y no usan PHP clásico, lo que agrega una curva de aprendizaje que no compensa para este proyecto.

#### Ventajas

1. **Crecimiento profesional real:** El equipo adquiere experiencia directamente aplicable en cualquier contexto laboral futuro. Desarrollo web estándar es una habilidad transferible, a diferencia del conocimiento específico de Moodle.
2. **La IA ayuda más y mejor:** El frontend es generado casi completamente por IA (una pantalla por prompt). El backend en PHP estándar también tiene soporte de IA mucho más confiable que los plugins de Moodle.
3. **Personalización total:** No hay límites técnicos impuestos por el sistema. Cualquier lógica de negocio, por compleja que sea, es implementable.
4. **Independencia funcional:** El sistema no depende de las actualizaciones, restricciones o decisiones administrativas del campus de la facultad.
5. **Mayor calidad visual:** Una página web permite interfaces modernas, fluidas y de nivel profesional que superan ampliamente la estética de Moodle. Vale aclarar que esto es lo menos relevante del análisis, pero es una diferencia real.
5. **Sin costo durante el desarrollo y la presentación:** Al correr en red local, el costo de hosting aparece solo si el proyecto pasa a producción, lo cual es una decisión futura y condicionada a la aprobación del proyecto.

#### Desventajas

1. **Costo si pasa a producción:** Es la desventaja central. Si el proyecto es adoptado, hay un costo mensual de hosting y base de datos que la institución debe asumir. Esto contradice la restricción de costo cero expresada por el cliente. Es un costo post-aprobación, pero es real.
2. **Autenticación propia:** A diferencia de Moodle, los alumnos no tienen un usuario preexistente en el sistema. Hay que construir el sistema de login desde cero, o implementar autenticación contra el Moodle de la facultad (OAuth), lo cual agrega complejidad.
3. **Desconexión del ecosistema:** Sin integración adicional, los alumnos acceden por una URL separada al campus. Esto genera fricción en la experiencia de usuario. Una integración vía LTI resolvería esto pero requiere hosting activo, lo que vuelve al problema del costo.
4. **Mantenimiento a cargo del equipo o la institución:** La seguridad y el mantenimiento del servidor no los absorbe la facultad automáticamente. Requiere una persona asignada.

---

## 5. Vinculación entre el Moodle de la Facultad y una Página Web Externa

Independientemente de cuál sea la alternativa elegida para el desarrollo del sistema, es técnicamente posible establecer comunicación bidireccional entre el Moodle institucional y una página web externa. Esto es relevante si en el futuro se quiere que ambos sistemas intercambien datos.

**Del Moodle de la facultad hacia la web:** Moodle puede enviar notificaciones automáticas a la web cada vez que ocurre un evento relevante (un alumno completa una encuesta, registra una actividad, etc.) mediante Webhooks. Existe un plugin gratuito que habilita esta funcionalidad. La web recibe esos datos y los procesa o almacena.

**De la web hacia el Moodle de la facultad:** Moodle expone una API REST oficial. La web puede consultarle datos académicos que ya existen en el campus, como materias inscriptas, progreso en cursos o notas, usando un token de acceso que un administrador genera una sola vez.

En la práctica, la arquitectura más natural sería que la web consulte al Moodle institucional para obtener datos base de los alumnos, y que Moodle notifique a la web cuando ocurran eventos. No es Moodle consultándole a la web en tiempo real, sino una sincronización orientada a eventos.

Esta vinculación no es un requisito del prototipo en red local, pero es un camino viable y documentado para la versión en producción.

---

## 6. Comparativa General

| Criterio | Moodle (localhost) | Web (red local) |
|---|---|---|
| Costo de desarrollo | Cero | Cero |
| Costo si pasa a producción | Cero | ~$2.500 ARS/mes (PHP) |
| PHP necesario | Sí, con restricciones de Moodle | Sí, estándar y más libre |
| Confiabilidad de la IA para el código | Menor | Mayor |
| Integración con el campus | Total | Requiere trabajo adicional |
| Autenticación | Resuelta (campus) | Hay que construirla |
| Personalización | Limitada por Moodle | Total |
| Experiencia profesional adquirida | Baja | Alta |
| Riesgo principal | Tardío (incompatibilidades en deploy) | Temprano (costo en producción) |
| Mantenimiento en producción | A cargo de la facultad | A cargo de la institución o el equipo |

---

## 6. Recomendación Orientativa

Ambas alternativas son válidas como entregable final en red local. La decisión depende de qué prioriza el equipo.

Si la prioridad es el costo cero absoluto también en producción y la integración nativa con el campus, Moodle es la opción adecuada. Hay que asumir que el desarrollo va a requerir PHP de todas formas, que la IA va a ser menos confiable en ese contexto, y que el deploy final depende de un administrador institucional.

Si la prioridad es la calidad del sistema, la experiencia profesional del equipo y la capacidad de implementar cualquier funcionalidad sin restricciones, la página web es la opción más sólida. El costo en producción es el único bloqueante real, y ese problema solo existe si el proyecto es aprobado y adoptado, lo cual es un buen problema para tener.

Un argumento concreto a favor de la web: dado que ambas alternativas requieren PHP de todas formas, la ventaja principal de Moodle (menos programación) se reduce considerablemente para el alcance de este proyecto. En ese escenario, escribir PHP libre en una web propia es más eficiente que escribir PHP dentro de las restricciones del sistema de plugins de Moodle, con menos ayuda de la IA y con riesgo de incompatibilidades en el deploy final.