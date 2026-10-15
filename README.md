# Dinos-juegos

Mapa de **Free Fire (Craftland Studio PC)** donde los dinosaurios deben cooperar para sobrevivir a una lluvia de meteoritos. Es un proyecto para practicar programación mientras se construye un juego, y para documentarlo en video.

## Concepto

- Los jugadores son dinosaurios y deben sobrevivir hasta el final de las oleadas.
- Del cielo caen meteoritos que eliminan a quien esté en la zona de impacto.
- Se puede jugar en **solitario** o en **escuadra de 4 a 6 jugadores**.
- Los equipos trabajan juntos: refugios cooperativos, revivir a compañeros y clases con estilos distintos (rápido, tanque, gigante).
- Apariencia de dinosaurio con los recursos que permita el editor. No se asume que se puedan importar modelos nuevos.

## Estado del proyecto

🚧 **En planificación.** Todavía no hay scripts. Primero se verifican las funciones y límites del editor (ver riesgos R1 a R6 en `HISTORIAS_DE_USUARIO.md`).

## Tecnología

- Craftland Studio PC
- Scripts de código con extensión `.fcg`
- VS Code con el plugin "Free Fire Craftland Code" (opcional)

## Documentación

| Archivo | Contenido |
|---|---|
| [`HISTORIAS_DE_USUARIO.md`](HISTORIAS_DE_USUARIO.md) | 19 historias con criterios de aceptación, riesgos por verificar y hoja de ruta |
| [`PARAMETROS.md`](PARAMETROS.md) | Valores iniciales de oleadas, clases y cooperación, para equilibrar el juego |

## Hoja de ruta

1. **Fase 1:** ciclo básico de meteoritos (aviso, cuenta regresiva, impacto, supervivientes, victoria).
2. **Fase 2:** clases de dinosaurio, equipos y revivir.
3. **Fase 3:** dificultad progresiva y refugios cooperativos.

## Estructura prevista

```
Dinos-juegos/
├── docs/        # Documentación
├── scripts/     # Scripts .fcg
└── README.md
```

## Notas

- Los nombres de scripts y funciones en la documentación son propuestas de organización, no APIs oficiales de Craftland.
- Los valores de `PARAMETROS.md` son iniciales y se ajustarán con pruebas de juego.
- Proyecto no oficial, hecho por un fan. Free Fire y Craftland son marcas de sus respectivos dueños.
