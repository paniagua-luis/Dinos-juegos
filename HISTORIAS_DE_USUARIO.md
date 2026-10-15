# Mapa "Dinosaurios vs Meteoritos" — Historias de usuario

Proyecto de mapa para **Free Fire (Craftland Studio PC)**. Un grupo de dinosaurios debe cooperar para sobrevivir a una lluvia de meteoritos, en modo solitario o en escuadras de 4 a 6 jugadores.

## Leyenda

- ⚠️ **Por verificar:** depende de las funciones, eventos o límites que ofrezcan las librerías oficiales de Craftland Studio PC. Se confirma antes de programar.
- **Prioridad:** Alta / Media / Baja.
- Los nombres de scripts, variables y funciones que aparezcan en este documento son **propuestas de organización**, no APIs oficiales.

## Decisiones del proyecto

- Plataforma: Craftland Studio PC, scripts de código (`.fcg`).
- Modos: solitario y escuadra de 4 a 6 jugadores.
- Skins/ropa: se usarán o modificarán los recursos que el editor permita. ⚠️ No se asume que se puedan importar modelos nuevos.

## Riesgos y puntos por verificar

| # | Punto | Impacto | Estado |
|---|-------|---------|--------|
| R1 | Cambiar tamaño, velocidad o vida del personaje por script | Clases de dinosaurio (HU-07) | Pendiente |
| R2 | Opciones de apariencia/ropa disponibles por script | Apariencia prehistórica (HU-08) | Pendiente |
| R3 | Número máximo de jugadores y de equipos | Escuadras de 4 a 6 (HU-09) | Pendiente |
| R4 | Crear objetos en tiempo de ejecución y su límite de recursos del mapa | Meteoritos (HU-04) | Pendiente |
| R5 | Daño por zona, eliminación y reaparición/revivir | HU-04, HU-10 | Pendiente |
| R6 | Interfaz (HUD) personalizada para avisos, cuenta regresiva y marcador | HU-02, HU-03, HU-11, HU-16 | Pendiente |

---

## Fase 1 — Ciclo básico de meteoritos (MVP)

### HU-01 · Aparición en la isla
**Prioridad:** Alta
**Como** jugador, **quiero** aparecer en un punto seguro de la isla al empezar, **para** comenzar la partida sin riesgo inmediato.

**Criterios de aceptación**
- Dado que empieza la partida, cuando todos los jugadores están listos, entonces cada jugador aparece en un punto de aparición válido de la isla.
- Los jugadores no reciben daño durante la fase de preparación.
- La partida no inicia el primer aviso hasta terminar la preparación.

### HU-02 · Aviso de zona de impacto
**Prioridad:** Alta
**Como** jugador, **quiero** ver una advertencia con la zona afectada, **para** saber a dónde correr.

**Criterios de aceptación**
- Antes de cada impacto se muestra un aviso visible para todos (mensaje, marca o efecto en el mapa). ⚠️ R6
- La zona avisada coincide con la zona donde cae el meteorito.
- El aviso desaparece tras el impacto.

### HU-03 · Cuenta regresiva
**Prioridad:** Alta
**Como** jugador, **quiero** una cuenta regresiva antes del impacto, **para** tener tiempo de buscar refugio.

**Criterios de aceptación**
- La cuenta regresiva empieza en el valor configurado y baja hasta cero.
- Se muestra a todos los jugadores. ⚠️ R6
- El impacto ocurre exactamente al llegar a cero.

### HU-04 · Impacto del meteorito
**Prioridad:** Alta
**Como** jugador, **quiero** que el impacto dañe o elimine a quien esté en la zona, **para** que el peligro sea real.

**Criterios de aceptación**
- Un jugador dentro de la zona al impactar recibe el efecto definido (daño o eliminación). ⚠️ R5
- Un jugador dentro de un refugio válido o fuera de la zona no recibe el efecto.
- El impacto muestra un efecto visual o de sonido. ⚠️ R4
- Los objetos creados para el meteorito no superan el límite de recursos del mapa. ⚠️ R4

### HU-05 · Comprobación de supervivientes
**Prioridad:** Alta
**Como** sistema, **quiero** revisar quién sobrevivió tras cada impacto, **para** decidir si continúa la oleada o termina la partida.

**Criterios de aceptación**
- Tras cada impacto se actualiza el número de jugadores vivos.
- Si quedan jugadores vivos y quedan oleadas, se pasa a la siguiente oleada.
- Si no queda ningún jugador vivo, la partida termina en derrota.

### HU-06 · Condición de victoria
**Prioridad:** Alta
**Como** jugador, **quiero** ganar al sobrevivir todas las oleadas, **para** tener un objetivo claro.

**Criterios de aceptación**
- Al terminar la última oleada con al menos un jugador vivo, se declara la victoria.
- Se muestra un mensaje de resultado (victoria o derrota). ⚠️ R6
- La partida se cierra o reinicia según la configuración del modo.

---

## Fase 2 — Dinosaurios y equipos

### HU-07 · Clases de dinosaurio
**Prioridad:** Media
**Como** jugador, **quiero** elegir una clase (rápido, tanque, gigante), **para** jugar con un estilo distinto. ⚠️ R1

**Criterios de aceptación**
- Antes de empezar, el jugador puede elegir una clase de una lista.
- Cada clase aplica sus propios valores de tamaño, velocidad y vida (configurables).
- Si el jugador no elige, se le asigna una clase por defecto.
- Las clases están equilibradas: ninguna es la mejor en todo.

### HU-08 · Apariencia prehistórica
**Prioridad:** Media
**Como** jugador, **quiero** una apariencia de dinosaurio, **para** sentirme parte del tema. ⚠️ R2

**Criterios de aceptación**
- Cada clase usa un conjunto de ropa o recursos disponibles en el editor con temática de dinosaurio.
- Si una opción de apariencia no está permitida, se documenta la alternativa usada.

### HU-09 · Modo solitario o escuadra
**Prioridad:** Media
**Como** jugador, **quiero** jugar solo o en escuadra de 4 a 6, **para** elegir cómo sobrevivir. ⚠️ R3

**Criterios de aceptación**
- Existen ambos modos configurables.
- En escuadra, el tamaño del equipo está entre 4 y 6, o el máximo que permita el editor (se documenta).
- Los equipos se forman antes de empezar y no cambian durante la partida.

### HU-10 · Revivir a un compañero
**Prioridad:** Media
**Como** compañero, **quiero** revivir a un aliado caído, **para** que la cooperación importe. ⚠️ R5

**Criterios de aceptación**
- Un aliado caído puede ser revivido por un compañero vivo en un tiempo máximo configurable.
- Revivir requiere una acción y un tiempo de interacción (por ejemplo, permanecer cerca unos segundos).
- Un jugador revivido reaparece con vida parcial y no puede ser revivido indefinidamente (límite configurable).

### HU-11 · Marcador de supervivientes del equipo
**Prioridad:** Media
**Como** equipo, **quiero** ver cuántos compañeros siguen vivos, **para** coordinarnos. ⚠️ R6

**Criterios de aceptación**
- El número de vivos se muestra y se actualiza tras cada baja o revivir.

### HU-12 · Victoria por equipo
**Prioridad:** Media
**Como** equipo, **quiero** ganar si sobrevive al menos uno, **para** que cada vida cuente.

**Criterios de aceptación**
- El equipo gana si al terminar la última oleada queda al menos un miembro vivo.
- El equipo pierde si todos sus miembros caen.

---

## Fase 3 — Dificultad y cooperación avanzada

### HU-13 · Dificultad progresiva
**Prioridad:** Media
**Como** jugador, **quiero** que cada oleada sea más difícil, **para** que el reto crezca.

**Criterios de aceptación**
- Cada oleada aumenta al menos un parámetro (cantidad de meteoritos, tamaño de zona o rapidez).
- Los incrementos se definen en la configuración, sin tocar el código.

### HU-14 · Refugios cooperativos
**Prioridad:** Media
**Como** equipo, **quiero** construir o activar refugios entre varios, **para** trabajar juntos de verdad. ⚠️ R4

**Criterios de aceptación**
- Un refugio se activa cuando una cantidad mínima de jugadores cumple la condición (por ejemplo, estar a su lado).
- Un refugio activo protege a los jugadores dentro de su área.

### HU-15 · Refugios que dejan de ser seguros
**Prioridad:** Baja
**Como** jugador, **quiero** que algunos refugios pierdan seguridad con el tiempo, **para** no confiarme. ⚠️ R4

**Criterios de aceptación**
- Un refugio marcado como temporal deja de proteger tras el tiempo configurado.
- Se avisa visualmente antes de que deje de ser seguro.

### HU-16 · Resultados al final
**Prioridad:** Baja
**Como** jugador, **quiero** ver mis resultados al terminar, **para** saber cómo me fue. ⚠️ R6

**Criterios de aceptación**
- Se muestra al menos: oleadas superadas y supervivientes del equipo.

---

## Historias del creador

### HU-17 · Parámetros ajustables en un solo lugar
**Prioridad:** Alta
**Como** creador, **quiero** configurar tiempos, tamaño de zona y número de oleadas en un único lugar, **para** equilibrar el juego sin reescribir código.

**Criterios de aceptación**
- Existe un único archivo o sección de parámetros.
- Cambiar un parámetro modifica el comportamiento sin editar la lógica.

### HU-18 · Modo de pruebas
**Prioridad:** Media
**Como** creador, **quiero** mensajes de depuración y un modo de pruebas, **para** encontrar errores rápido.

**Criterios de aceptación**
- Se puede activar o desactivar el modo de pruebas con un parámetro.
- En modo de pruebas se muestran los eventos principales (inicio de oleada, aviso, impacto, resultado).

### HU-19 · Respeto del límite de recursos
**Prioridad:** Alta
**Como** creador, **quiero** que el mapa respete el límite de recursos, **para** poder publicarlo. ⚠️ R4

**Criterios de aceptación**
- El mapa no supera el límite de recursos permitido por el editor.
- Los objetos temporales (meteoritos, efectos) se eliminan tras usarse.

---

## Definición de "terminado" (para cada historia)

- Cumple todos sus criterios de aceptación.
- Probada en partida solitaria y en escuadra (cuando aplique).
- Sus parámetros están en la configuración, no escritos dentro de la lógica.
- Documentado qué se verificó en R1–R6 y cuál fue el resultado.

## Hoja de ruta

| Fase | Contenido | Historias |
|------|-----------|-----------|
| 1 | Ciclo básico de meteoritos | HU-01 a HU-06, HU-17, HU-19 |
| 2 | Dinosaurios y equipos | HU-07 a HU-12 |
| 3 | Dificultad y cooperación | HU-13 a HU-16, HU-18 |
