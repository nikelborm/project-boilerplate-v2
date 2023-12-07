# project boilerplate

### Analyzing the Bundle Size

This section has moved here: [https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size](https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size)

### Making a Progressive Web App

This section has moved here: [https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app](https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app)

### Advanced Configuration

This section has moved here: [https://facebook.github.io/create-react-app/docs/advanced-configuration](https://facebook.github.io/create-react-app/docs/advanced-configuration)

### Deployment

This section has moved here: [https://facebook.github.io/create-react-app/docs/deployment](https://facebook.github.io/create-react-app/docs/deployment)

### `yarn build` fails to minify

This section has moved here: [https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify](https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify)

<!-- ///////////////////////////////////////////////////////////////////////// -->

<!-- TODO: нахуярить плашечек с сайта https://badgen.net/help#generators или других плашечек -->
<!--
![commit](https://badgen.net/github/last-commit/darraghoriordan/eslint-plugin-nestjs-typed/main)
![npm](https://img.shields.io/npm/v/@darraghor/eslint-plugin-nestjs-typed.svg?color=red)
![npm-tag](https://badgen.net/github/tag/darraghoriordan/eslint-plugin-nestjs-typed)
![size](https://badgen.net/bundlephobia/minzip/@darraghor/eslint-plugin-nestjs-typed?color=cyan)
![types](https://badgen.net/npm/types/@darraghor/eslint-plugin-nestjs-typed?color=blue)


<p align="center">
  <a href="https://nestjs.com/" target="blank"><img src="https://github.com/nestjs/docs.nestjs.com/blob/master/src/assets/logo-small.svg" height="100" alt="Nest logo" /></a>
  <a href="https://typeorm.io/" target="blank"><img src="https://avatars.githubusercontent.com/u/20165699" height="100" alt="TypeORM logo" /></a>
  <a href="https://www.postgresql.org/" target="blank"><img src="https://www.postgresql.org/media/img/about/press/elephant.png" height="100" alt="PostgreSQL logo" /></a>
  <a href="https://jestjs.io/" target="blank"><img src="https://github.com/facebook/jest/blob/main/website/static/img/jest.png" height="100" alt="Jest logo" /></a>
  <a href="https://prettier.io/" target="blank"><img src="https://github.com/prettier/prettier/blob/main/website/static/icon.png" height="100" alt="Prettier logo" /></a>
  <a href="https://eslint.org/" target="blank"><img src="https://github.com/eslint/website/blob/master/assets/img/logo.svg" height="100" alt="ESLint logo" /></a>
</p>

<p align="center">
  <a href="https://docs.docker.com/" target="blank"><img src="https://www.docker.com/wp-content/uploads/2022/03/Moby-logo.png" height="60" alt="Docker logo" /></a>
  <a href="https://github.com/features/actions" target="blank"><img src="https://avatars.githubusercontent.com/u/44036562" height="60" alt="GitHub Actions logo" /></a>
  <a href="https://circleci.com/" target="blank"><img src="https://www.vectorlogo.zone/logos/circleci/circleci-icon.svg" height="60" alt="CircleCI logo" /></a>
</p>

# Nest - Boilerplate

[![GitHub CI](https://github.com/smarlhens/nest-boilerplate/workflows/CI/badge.svg)](https://github.com/smarlhens/nest-boilerplate/actions?query=workflow%3ACI)
[![CircleCI](https://circleci.com/gh/smarlhens/nest-boilerplate.svg?style=svg)](https://circleci.com/gh/smarlhens/nest-boilerplate)
[![Commitizen friendly](https://img.shields.io/badge/commitizen-friendly-brightgreen.svg)](http://commitizen.github.io/cz-cli/)
[![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg)](https://github.com/prettier/prettier)
[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow.svg)](https://conventionalcommits.org)

-->




## Requirements and initialization

If you don't have vs code, search for commands in `./project.code-workspace`

1. Install docker, docker-compose, buildx
2. Install node.js 16 with nvm. [NVM GitHub](https://github.com/nvm-sh/nvm)
3. Install yarn with `npm i -g yarn`
4. Call task in VS code: `Create new docker builder` (call only once when pulling project)
5. Call task in VS code: `Use docker builder` (call only once when pulling project)
6. Call task in VS code: `Install yarn dependencies` (call only once when pulling project)

## Development

If you plan to develop and use own fs

1. Call task in VS code for better typing support: `Mount types/shared in native fs`.
2. Call task in VS code: `Up dev`

If you want to develop inside a container

1. Call command in VS code: `Dev containers: Reopen in container`

## How to run psql

1. Call task in VS code: `psql dev`

## Endpoint to execute mock

<http://localhost/api/mock/execute?mockScriptName=mockUserAndAdminAccessScope>

## Useful Docker commands

1. If you want to check that all containers are up :

   ```bash
   docker-compose ps
   ```

1. Other Docker commands :

   ```bash
   # Start Docker
   docker-compose start

   # Restart Docker
   docker-compose restart

   # Stop Docker
   docker-compose stop

   # Delete all containers
   docker rm $(docker ps -aq)

   # Delete all images
   docker rmi $(docker images -q)
   ```

1. How to get a Docker container's IP address from the host ?

   ```bash
   docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' <container>
   docker inspect $(docker ps -f name=<service> -q) | grep IPAddress
   ```

## TODO

- [ ] password recovery|reset
- [ ] connect testing libraries
- [ ] Move yarn dependencies one level higher
- [ ] Merge typescript, prettier and eslint configs and place it in project root directory
- [ ] write script for getting sql from all migrations into one .sql file which then will be fed to dbml documentation generator
- [ ] add healthcheck
- [ ] wrap mock into transaction
- [ ] add removing expired tokens from whitelisted store
- [ ] update customFetch in frontend to use latest version made in tda project
- [ ] cache requests to db for user with joined all access scopes (don't forget to invalidate cache when updating user or access scopes)
- [ ] move some logic of redis commands from js to lua right into redis itself

<!--
lua redis example:
local rank = redis.call('zrank', KEYS[1], ARGV[1]);
local min = math.max(rank - ARGV[2], 0);
local max = rank + ARGV[2];
local ldb = redis.call('zrange', KEYS[1], min, max);
return {rank+1, ldb}; -->
