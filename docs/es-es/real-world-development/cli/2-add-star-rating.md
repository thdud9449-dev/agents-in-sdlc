---
title: "Lección 2 - Añadir valoraciones por estrellas: una mejora rápida"
description: "Usa Copilot CLI para hacer un cambio pequeño en las tarjetas de juegos, revísalo en un navegador reenviado y combínalo como tu primera pull request."
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

Ahora que ya has instalado Copilot CLI y has probado una conversación, es el momento de hacer tu primer cambio en el proyecto. Mantendremos el alcance pequeño: los juegos ya tienen una valoración por estrellas en sus datos, pero las tarjetas de los juegos en la página principal todavía no la muestran. Pedirás al agente que la muestre, revisarás el cambio y lo combinarás como tu primera pull request.

En esta lección, aprenderás a:

- iniciar una conversación enfocada de Copilot en una rama de funcionalidad.
- pedir al agente que haga un cambio pequeño en el proyecto.
- revisar el cambio con `/diff`.
- ejecutar la aplicación para confirmar el cambio en un navegador reenviado.
- abrir y fusionar tu primera pull request.

## Escenario

Cada juego de Tailspin Toys puede tener una valoración por estrellas, y ya aparece en la página de detalles del juego. Las tarjetas de los juegos en la página de inicio, sin embargo, solo muestran el título, la categoría, el editor y la descripción. Como ejercicio inicial, pedirás al agente que muestre la valoración existente en cada tarjeta: un cambio pequeño y autocontenido, perfecto para tu primera sesión.

## Anatomía de una conversación

Una **conversación** es el lugar donde trabajas con Copilot CLI en una tarea. A diferencia de la aplicación Copilot, una conversación normal de CLI usa el repositorio y la rama de Git actualmente activados en tu terminal, en lugar de crear un árbol de trabajo dedicado. Las conversaciones guardadas te permiten volver a la misma discusión más tarde, mientras que los archivos y la rama siguen siendo estado normal de Git en disco.

Dentro de una conversación verás tres cosas: tus indicaciones y las respuestas del agente, la actividad de las herramientas del agente mientras explora y edita archivos, y los cambios que puedes inspeccionar con `/diff`.

## Inicia una conversación y solicita el cambio

Vamos a iniciar una conversación nueva para empezar a implementar la funcionalidad.

1. Vuelve a tu Codespace.
2. Si la terminal no está abierta desde antes, pulsa <kbd>Control</kbd>+<kbd>\`</kbd> (Mac) o <kbd>Ctrl</kbd>+<kbd>\`</kbd> (Windows/Linux).
3. Si aún no está abierta, inicia Copilot con este comando:

   ```bash
   copilot --yolo
   ```

4. Asegúrate de que se inicia una nueva sesión usando el comando con barra `/new` y pulsando <kbd>Enter</kbd>.
5. Usa la siguiente indicación para solicitar el cambio:

   ```plaintext
   Show each game's starRating out of 5 in the game cards on the list page. If the rating is null, show "No rating yet". Keep the card layout as it is, add tests, and run the relevant checks.
   ```

Copilot explora el proyecto, localiza los archivos usados para mostrar los detalles del juego y crea el código necesario. ¡Ya has añadido una nueva funcionalidad con Copilot CLI!

## Revisa el diff

Todos los cambios generados por IA merecen una revisión antes de fusionarse, aunque sean pequeños. Exploremos los cambios aquí mismo en Copilot CLI.

1. Escribe `/diff` e inspecciona cada archivo modificado.
2. Confirma que la tarjeta del juego muestra la valoración numérica cuando existe y `No rating yet` cuando `starRating` es `null`.
3. Confirma que las pruebas cubren ambos casos.
4. Revisa los resultados de las comprobaciones que Copilot ejecutó y pídele que corrija cualquier fallo.
5. Cuando termine la revisión, pulsa <kbd>Esc</kbd> para salir de la vista de diff.

> [!NOTE]
> Como Copilot, como todas las herramientas generativas de IA, es probabilístico y no determinista; el código exacto puede variar. Revisa el comportamiento en lugar de esperar una sola implementación exacta.

## Comprueba los cambios

Claro que no basta con leer el código y asumir que funciona. Pidamos a Copilot que inicie nuestro sitio web para examinar la interfaz de usuario actualizada en el navegador reenviado por Codespaces.

1. Pide a Copilot que inicie la aplicación:

   ```plaintext
   Start the app so I can inspect the star-rating change in my browser. Tell me the URL and leave the server running.
   ```

2. Cuando Codespaces informe de que el puerto `4321` está disponible, selecciona **Open in Browser**.
3. Confirma que las tarjetas de los juegos muestran sus valoraciones sobre cinco.
4. Vuelve a Copilot y pídele que detenga el servidor que ha iniciado:

   ```plaintext
   Stop the development server you started.
   ```

## Abre y combina tu primera pull request

¡Ahora ya has creado la funcionalidad! Es el momento de crear una pull request (PR) para fusionar el nuevo código en el proyecto.

1. Pide al agente predeterminado que confirme el cambio:

   ```plaintext
   Commit the reviewed star-rating changes with an appropriate commit message.
   ```

2. Escribe `/pr create`. Copilot CLI empuja el commit actual cuando crea la PR y muestra la URL de la PR.
3. Abre la PR manteniendo pulsado <kbd>Command</kbd> (Mac) o <kbd>Ctrl</kbd> (Windows/Linux) y seleccionando la URL mostrada por Copilot CLI.
4. Revisa los archivos modificados y las comprobaciones.
5. Cuando estés listo, selecciona **Merge pull request** y confirma la combinación.
6. Vuelve a tu Codespace y sal de Copilot CLI con `/exit`.
7. Actualiza tu `main` local:

   ```bash
   git checkout main
   git pull
   ```

## Resumen y siguientes pasos

¡Enhorabuena! Has publicado tu primer cambio usando GitHub Copilot CLI. En concreto, has:

- iniciado una conversación enfocada de Copilot en una rama de funcionalidad.
- pedido al agente que hiciera un pequeño cambio en las tarjetas de juegos.
- revisado el cambio con `/diff`.
- ejecutado la aplicación para confirmar la valoración por estrellas en un navegador reenviado.
- abierto y fusionado tu primera pull request.

A continuación, [iniciarás desde la incidencia de filtrado y usarás los modos Plan y Autopilot][next-lesson] para crear una funcionalidad más larga.

## Recursos

- [Acerca de GitHub Copilot CLI][about-copilot-cli]
- [Referencia de comandos de Copilot CLI][cli-reference]

[previous-lesson]: ../1-install-copilot-cli/
[next-lesson]: ../3-agent-modes/
[about-copilot-cli]: https://docs.github.com/copilot/concepts/agents/about-copilot-cli
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
