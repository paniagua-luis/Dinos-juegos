# Parámetros del mapa "Dinosaurios vs Meteoritos"

Valores iniciales para la **HU-17** (parámetros ajustables en un solo lugar).

> **Importante:** son valores de **propuesta para probar y ajustar**. Las unidades (distancia, tiempo, vida) y los límites reales dependen de lo que ofrezca Craftland Studio PC. Los nombres de los parámetros son propuestas de organización, no APIs oficiales.

## Partida

| Parámetro | Valor inicial | Notas |
|---|---|---|
| Preparación | 30 s | Sin daño ni meteoritos |
| Oleadas | 6 | |
| Pausa entre oleadas | 15 s | |
| Jugadores en solitario | 1 | |
| Jugadores en escuadra | 4 a 6 | ⚠️ Verificar el máximo permitido (R3) |

## Oleadas (dificultad progresiva)

| Oleada | Meteoritos | Radio de zona | Cuenta regresiva |
|---|---|---|---|
| 1 | 2 | 8 | 10 s |
| 2 | 3 | 8 | 9 s |
| 3 | 4 | 10 | 8 s |
| 4 | 5 | 10 | 7 s |
| 5 | 6 | 12 | 6 s |
| 6 | 8 | 12 | 5 s |

Ajuste para escuadras: añadir 1 meteorito extra por cada 2 jugadores (a probar).

## Clases de dinosaurio

Multiplicadores sobre el valor base. ⚠️ Verificar que se puedan aplicar por script (R1).

| Clase | Vida | Velocidad | Tamaño |
|---|---|---|---|
| Rápido | 0.8 | 1.3 | 0.9 |
| Tanque | 1.4 | 0.8 | 1.1 |
| Gigante | 1.8 | 0.7 | 1.5 |

## Cooperación

| Parámetro | Valor inicial |
|---|---|
| Tiempo de interacción para revivir | 8 s |
| Máximo de revivires por jugador | 2 |
| Vida al revivir | 50 % |
| Jugadores para activar un refugio cooperativo | 2 |
| Protección de un refugio cooperativo | 1 oleada |
| Duración de un refugio temporal | 2 oleadas |
| Aviso antes de perder seguridad | 5 s |

## Depuración

| Parámetro | Valor inicial |
|---|---|
| Modo de pruebas | Desactivado |

## Guía de equilibrio

- Si la oleada 1 elimina a casi todos, sube la cuenta regresiva o baja el radio.
- Si nadie cae hasta la oleada 4, sube los meteoritos o reduce los refugios.
- Prueba en solitario y en escuadra por separado: el equilibrio cambia con el tamaño del equipo.
- Vigila la clase Gigante: más vida pero mayor tamaño, así que es un blanco fácil. Debe sentirse fuerte, no imbatible.

## Registro de pruebas

| Fecha | Cambio | Resultado |
|---|---|---|
| | | |
