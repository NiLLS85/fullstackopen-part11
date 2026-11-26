# Full Stack Open, parte 11: CI/CD con GitHub Actions

Ejercicios de la parte 11 (integración y despliegue continuos) del curso [Full Stack Open](https://fullstackopen.com/) de la Universidad de Helsinki.

El proyecto de ejemplo es la Pokédex del curso: un frontend en React (Webpack) y un pequeño servidor Express que sirve la versión de producción. Sobre él se monta un pipeline de GitHub Actions.

## Workflows

- `.github/workflows/hello.yml`: workflow de prueba (ejercicios 3 y 4).
- `.github/workflows/pipeline.yml`: pipeline de despliegue con lint, build, tests unitarios (Jest) y tests end-to-end (Playwright).

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
