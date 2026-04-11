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