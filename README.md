# 4_event_booking

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup
[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Customize configuration
See [Vite Configuration Reference](https://vite.dev/config/).

## Project Setup
```sh
npm install
```

### Start JSON Server
If your project uses [JSON Server](https://github.com/typicode/json-server) for a mock backend, start it with:
```sh
npm run server
```
This command runs:
```sh
json-server --watch db.json --delay=3000 --port 3001
```
Make sure you have the `json-server` package installed. If not, install it globally or as a dev dependency:
```sh
npm install -g json-server
```
or  
```sh
npm install --save-dev json-server
```
Once the server is running, the API will be available at:
- `http://localhost:3001`

### Compile and Hot-Reload for Development
```sh
npm run dev
```

### Compile and Minify for Production
```sh
npm run build
```

### Lint with [ESLint](https://eslint.org/)
```sh
npm run lint
```
