## Info Inicial

**Objetivo Puntual (Nuestro Objetivo)**: Recoleccion y organizacion de la informacion para que el departamento de ing. Industrial pueda armar una solucion al problema.

**Objetivo Final:** Reducir y consolidar informacion.

El medio debe ser un sistema que ordene y catalogue info para poder armar una solucion al problema.

1. Desercion tardia: Cuando un estudiante abandona cerca del final de la carrera
2. Desercion temprana: Cuando un estudiante abandona al principio de la carrera, principalmente dado por las materias iniciales, Analisis I, fisica, etc.
3. La informacion esta fragmentada
4. Al tener tantas fuentes diferentes el departamento no tiene un plan claro, "tiene mucha info desordenada"

***

## Principio para ordenar y formular preguntas

Formato deseado de preguntas -> Markdown y preguntas ordenadas segun el orden
`E -> P -> S`, preguntas que desencadenen de otras preguntas añadirlas con flechas estilo:

`E`: Entrada, lo que primero debemos saber

`P`: Proceso, el proceso, metodo o algoritmo para reunir la informacion

`S`: Salida, como mostrar los datos, metricas, etc.

**Ejemplo:**

(no considerar lo que se menciona aqui, tema irrelevante, solo considerar organizacion en ASCII)
```
├── stores/
│   ├── plan.svelte.ts              → User FREE/PRO plan, expiration
│   ├── tabs.svelte.ts              → Open tabs state in RAM
│   ├── modules.svelte.ts           → Available modules by plan
│   ├── session.svelte.ts           → Volatile data: user, token, configModified (cleared on app close)
│   └── user-preferences.svelte.ts → Central server preferences: theme, language, notifications
│
├── types/                     → index.ts, plan.ts, tab.ts, session.ts, config.ts
│
├── tests/
│   ├── setup.ts               → Vitest global setup
│   ├── mocks/
│   │   └── tauri.mock.ts      → Mock for window.__TAURI__ / invoke()
│   └── integration/           → sales-flow.test.ts, auth-flow.test.ts
│
```

***

## Preguntas Desordenadas

1. Medios para obtener info?, campus, encuestas, etc.
2. Cual es el objetivo del departamento?
3. Suposiciones Iniciales del problema?

4. Metricas que requiere como resultado final para tomar una decision
5. Datos que necesita para generar esa metrica

6.  Conocer que es tardio y que es temprano especificamente
7. Como quieren ver los datos finales
8. Cuales son los porcentajes esperados?, en otras palabras que porcentajes debemos calcular
9. Como le presento la informacion final, esto desencadena otras muchas preguntas con la respuesta inicial a esta pregunta, en formato tabla?, formato especifico?
10. Origen de los datos, en que formatos estan los datos?, hay info repetida?, los datos estan fragmentados?
11. Confiabilidad de los datos, estan encriptados?
12. Que datos son relevantes realmente?
13. Alcance del proyecto, es solo para este departamento?, es solo para esta facultad, la metodologia desarrollada seguira siendo usada en el futuro o en el tiempo (dato sabido: si, seguira siendo usada en el tiempo)
14. Quienes se van a encargar de recolectar los datos?
15. Se puede hacer todo en automatico esta recoleccion?, algo sera manual (por ej entrevistas), (recoleccion de datos de/en un sistema podria ser auto)
16. Encuestas, como hacerlas?, quien completa las encuestas?, ya se hizo una encuesta en el pasado?
17. Hay info historica ya disponible que se puede utilizar?
18. Tiempos: Para cuando lo quieren listo? (Maximo tiempo es el final de cuatrimestre, dato ya sabido) 
19. Que presupuesto?
20. Reescricciones, Que reestricciones tenemos o tienen?, asi como desde que año tenemos que considerar los datos?
21. El sistema es solo para ahora o se utilizara en el futuro?

22. Expandiendo la cuestion de los medios, existe alguna funcion, alguna pagina o alguna seccion de la misma donde se pueda obtener los datos?, que accesos o permisos se requieren para acceder a esta info?

***

## Preguntas Organizadas (E → P → S)

Preguntas consolidadas (se eliminaron duplicados), encadenadas donde una requiere la respuesta de la anterior, y organizadas según Entrada → Proceso → Salida.

### E — Entrada

```
├── 1. ¿Cuál es el objetivo del departamento?
├── 2. ¿Suposiciones iniciales del problema?
├── 3. ¿Existe un modelo o definición formal de "deserción" que el departamento
│      ya utilice, o necesitamos definir uno desde cero?
│   └── 3.1. ¿Qué se considera deserción tardía y qué deserción temprana
│            específicamente?
├── 4. Alcance: ¿Es solo para este departamento?, ¿solo para esta facultad?,
│      ¿la metodología/sistema seguirá siendo usada en el futuro?
├── 5. ¿Qué restricciones tenemos?, ¿desde qué año debemos considerar los datos?
├── 6. ¿Para cuándo lo quieren listo?
├── 7. ¿Qué presupuesto hay disponible?
├── 8. Origen de los datos: ¿en qué formatos están?, ¿hay info repetida?,
│      ¿los datos están fragmentados?
│   ├── 8.1. ¿Cuál es la confiabilidad de los datos?, ¿están encriptados?
│   ├── 8.2. ¿Qué datos son relevantes realmente?
│   └── 8.3. ¿Hay información histórica ya disponible que se pueda utilizar?
├── 9. ¿Qué variables sociodemográficas del estudiante se consideran relevantes
│      (edad, género, localidad, situación laboral, etc.)?
├── 10. ¿Se cuenta con datos de rendimiento académico (notas, materias recursadas,
│       promedio) vinculados a cada alumno?
│   ├── 10.1. ¿Desde qué fecha se tienen estos datos?
│   └── 10.2. ¿Existe alguna fecha o política de eliminación de datos?
└── 11. ¿Se requiere anonimizar los datos de los estudiantes antes de procesarlos?
```

### P — Proceso

```
├── 1. ¿Qué medios existen para obtener la información (campus, encuestas, etc.)?,
│      ¿existe alguna función, página o sección del sistema donde se puedan
│      obtener los datos?, ¿qué accesos o permisos se requieren?
│   ├── 1.1. ¿Quiénes se van a encargar de recolectar los datos?
│   │   └── 1.1.1. ¿Se puede hacer todo de forma automática o algo será
│   │              manual (ej: entrevistas)?
│   └── 1.2. Encuestas: ¿cómo hacerlas?, ¿quién las completa?,
│            ¿ya se hizo alguna en el pasado?
├── 2. ¿Quién será el punto de contacto principal en el departamento para
│      validar avances y resultados intermedios?
├── 3. ¿Con qué frecuencia se desea actualizar los datos
│      (mensual, cuatrimestral, anual)?
│
│   ── Consideración ──
└── ⚠ Definir cómo manejar los casos de reincorporaciones (estudiantes que
    abandonan y luego vuelven). ¿Se cuenta como deserción o no?
```

### S — Salida

```
├── 1. ¿Qué métricas requiere como resultado final para tomar una decisión?
│   ├── 1.1. ¿Qué datos necesita para generar esas métricas?
│   └── 1.2. ¿Cuáles son los porcentajes esperados / que debemos calcular?
├── 2. ¿Cómo quieren ver los datos finales?
│      (formato tabla, gráficos, formato específico, etc.)
└── 3. ¿Se requiere segmentación en los resultados
│      (por carrera, por cohorte, por materia)?
    └── 3.1. ¿Se necesita identificar las materias o momentos específicos
             donde ocurre más deserción, o solo tasas generales?
```
