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