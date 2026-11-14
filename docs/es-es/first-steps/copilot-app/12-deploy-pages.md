---
title: "Lección 12 - Publica el sitio con GitHub Pages"
description: "Usa la aplicación GitHub Copilot para configurar un flujo de trabajo de Pages, revisa la pull request y verifica el sitio en vivo."
authors:
  - jamesmontemagno
lastUpdated: 2026-10-12
---

Dale a la Space Quiz un hogar público publicándolo con GitHub Pages. Copilot puede preparar el flujo de trabajo y guiar la implementación, pero tú sigues siendo responsable de revisar los cambios y confirmar que el sitio está activo.

En esta lección aprenderás a:

- pedir a Copilot que configure un despliegue de GitHub Pages.
- revisar el flujo de trabajo y la solicitud de extracción antes de fusionarlos.
- seguir el despliegue y verificar el sitio publicado.

## Escenario

La Space Quiz ya está en un repositorio de GitHub, pero la gente aún necesita una forma sencilla de probarla. Publicar el sitio de un archivo con GitHub Pages lo hace accesible desde una URL pública sin añadir un servidor ni dependencias de tiempo de ejecución.

## Pide a Copilot que prepare el despliegue

> [!WARNING]
> Crear una pull request puede confirmar y enviar código. Revisa la configuración de aprobación y el repositorio de destino antes de enviar este mensaje. Con **Approve all**, no esperes una confirmación separada.

En la sesión de la aplicación Copilot para `space-quiz`, envía este mensaje:

```plaintext
Prepare a GitHub Pages deployment for this repository. Create a GitHub Actions workflow that builds the website if needed and deploys it to GitHub Pages after changes reach the default branch. Add a README describing the app and how to run it locally if one does not already exist. Create a pull request with these changes and report its link and any required Pages settings or permissions. Do not merge, enable auto-merge, change Pages settings, or deploy. Stop and wait for my review.
```

## Revisa el flujo de trabajo y la pull request

1. Confirma que el README solo se añade si el repositorio no tiene ya uno.
2. Revisa los cambios de la pull request, incluido el paso de compilación y despliegue del flujo de trabajo, sus activadores y permisos.
3. Confirma que el flujo de trabajo se despliega desde la rama predeterminada, no desde una pull request sin fusionar.
4. Solicita las correcciones necesarias y revisa el diff actualizado. Espera a que pasen las comprobaciones requeridas de la pull request antes de autorizar la combinación.

## Autoriza la combinación y el despliegue

> [!WARNING]
> El siguiente mensaje autoriza al agente a fusionar la pull request revisada, cambiar la configuración de Pages del repositorio y publicar el sitio. Envíalo solo después de completar tu revisión y confirmar el repositorio y la pull request. La configuración de permisos puede permitir estas acciones sin otra confirmación.

Sustituye `<PR_NUMBER>` por el número de la pull request que has revisado y envía este mensaje separado:

```plaintext
I have reviewed pull request <PR_NUMBER> in this repository and authorize its merge and deployment. Enable GitHub Pages using GitHub Actions, merge that pull request only after required checks pass, and monitor the deployment until it succeeds. Report the final URL of the live website. If you lack permission to enable Pages or merge, tell me exactly what I need to approve or do; do not report success until the site is live.
```

![Diagrama en tres etapas: una pull request de space-quiz combinada; una ejecución correcta de GitHub Actions Deploy website con Build website, Upload artifact y Deploy to Pages; y la Space Quiz en vivo en tuusuario.github.io/space-quiz/.](../../../_images/first-steps-app-pages-deploy.svg)

## Verifica el despliegue

1. Sigue la ejecución de despliegue de GitHub Actions hasta que tenga éxito.
2. Abre la URL indicada y confirma que la Space Quiz se carga.

Si el agente no puede activar Pages o combinar la pull request, sigue las instrucciones concretas que te proporcione. No consideres la tarea completada hasta que el despliegue tenga éxito y el sitio en vivo cargue.

## Resumen y pasos siguientes

Tu Space Quiz ya está disponible como sitio en directo y has verificado el despliegue en lugar de depender de la notificación del agente. Continúa con [Lección 13: repaso y siguientes pasos][next-lesson].

[next-lesson]: ../13-review/
