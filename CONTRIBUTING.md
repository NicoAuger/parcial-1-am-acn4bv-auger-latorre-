# Contribuir al proyecto

## Rama
- Trabajamos directo sobre `main` con commits pequeños y atómicos.

## Mensajes de commit (Conventional Commits)
Usar:
- feat: nueva funcionalidad (usuario ve un cambio)
- fix: corrección de bug
- refactor: cambio interno sin nuevas features
- docs: documentación (README, informe, comentarios)
- style: formato/código (sin lógica)
- test: tests
- build: cambios de build/gradle
- chore: mantenimiento

### Ejemplos
- feat(ui): agrega iconos por categoría en lista
- fix(adapter): corrige NPE al borrar item sin nota
- refactor(main): extrae lógica de totales a método dedicado
- docs(readme): pasos para correr la app en Android Studio

## Guía de commits
- 1 cambio = 1 commit (atómico)
- Mensaje en presente e imperativo
- Máx. 72 caracteres en el título

## Código
- Strings/colores/dimens centralizados
- Nombres en español en UI, inglés en código (clases/métodos/props)
- Validaciones en UI antes de persistir/bindear
