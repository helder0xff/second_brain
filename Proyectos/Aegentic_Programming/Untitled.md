
1. **Especifica bien la tarea** con:
	- **Objetivo**
	- **Entradas**
	- **Salidas**
	- **Restricciones**
	- Errores que debe escupir
	- No debe
	- Criterios de aceptación
	- **Test** que debe pasar

2. **Contexto persistente** mediante **AGENTS.md**
	- Arquitectura
	- Convenciones
	- Comandosd de build
	- Cómo ejecutar tests
	- Reglas de Git
	- Patrones permitidos
	- Patrones prohibidos
	- Estructura del proyecto
	- Criterios de calidad
3. **Divide y vencerás**
4. **Primero Plan, luego Code**: mira a ver qué plan te propone el agente.
5. **Varias tareas, varias líneas**. Evita frases largas y contínuas. Think agentic.
6. **TDD**, no para todo, pero para lo importante.
	- Escribe los test.
	- Implementa.
	- Valida
7. **No te fies de** que **los test** pasen: double check
8. **Keep it simple**
9. **Git is your friend**... commit frecuntemente.
10. **Agente 1: coder, agente 2: tester**
11. **Common task? -> Skill**
	- code review
	- release
	- driver development
	- test writing
	- tech doc writer
	- ...
12. Recommended Repo Arquitecture: el propio **directory tree es parte del contexto**.  
`repo/`  
`├── [AGENTS.md`  
`├── [README.md`  
`├── docs/`  
`│ ├── architecture/`  
`│ ├── specifications/`  
`│ └── decisions/`  
`├── src/`  
`├── tests/`  
`├── scripts/`  
`└── ...`