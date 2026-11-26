# Full Stack Open, parte 11: CI/CD con GitHub Actions

Ejercicios de la parte 11 (integración y despliegue continuos) del curso [Full Stack Open](https://fullstackopen.com/) de la Universidad de Helsinki.

El proyecto de ejemplo es la Pokédex del curso: un frontend en React (Webpack) y un pequeño servidor Express que sirve la versión de producción. Sobre él se monta un pipeline de GitHub Actions.

Aplicación desplegada en Render: https://fs-pokedex-nills.onrender.com (la instancia gratuita tarda unos segundos en despertar).

## Enlaces

- Pokédex desplegada: https://fs-pokedex-nills.onrender.com
- Aplicación propia con su pipeline de CI/CD (ejercicios 21 y 22, agenda telefónica): https://github.com/NiLLS85/fullstackopen-part11-phonebook

## Workflows

- `.github/workflows/hello.yml`: workflow de prueba (ejercicios 3 y 4).
- `.github/workflows/pipeline.yml`: pipeline de despliegue repartido en jobs. `lint`, `unit_tests` (Jest) y `build` van en paralelo; `e2e_tests` (Playwright) usa el build guardado como artefacto; `deploy` avisa a Render y `tag_release` crea la etiqueta de versión.
- `.github/workflows/health-check.yml`: comprobación diaria de que la aplicación publicada responde en `/health`. También se puede lanzar a mano desde la pestaña Actions, incluso con otra URL para simular una caída.

## Cómo se trabaja

Los cambios no se suben directamente a `main`: se hacen en una rama y entran con un pull request. El pipeline se ejecuta en cada pull request (al abrirlo y con cada commit nuevo) y otra vez al fusionarlo en `main`.

Cada fusión en `main` que pasa el pipeline se despliega en Render y recibe una etiqueta de versión (`0.0.1`, `0.0.2`...). Si algún commit del cambio lleva `#skip` en el mensaje, no se despliega ni se etiqueta.

## Comandos

Instalar las dependencias con `npm install` y después:

- `npm start`: servidor de desarrollo de Webpack.
- `npm test`: tests unitarios con Jest.
- `npm run test:e2e`: tests end-to-end con Playwright (arranca el servidor de producción solo, hace falta `npm run build` antes).
- `npm run eslint`: lint del código.
- `npm run build`: build de producción.
- `npm run start-prod`: servidor de producción en el puerto 5001.

## Uso de IA

Estos ejercicios se hicieron con ayuda de un asistente de IA (Claude, de Anthropic), bajo mi dirección. El asistente escribió la mayor parte de la configuración y del código, y lo comprobó con el pipeline de GitHub Actions.
