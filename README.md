# Instalación y configuracion de Jest + React Testing Library
## En proyectos de React + Vite

1. Instalaciones:
```
yarn add --dev jest babel-jest @babel/preset-env @babel/preset-react 
yarn add --dev @testing-library/react @types/jest jest-environment-jsdom

```

2. Opcional: Si usamos Fetch API en el proyecto:
```
yarn add --dev whatwg-fetch

```

3. Actualizar los scripts del __package.json__
```
"scripts: {
  ...
  "test": "jest --watchAll"

```

4. Crear la configuración de babel __babel.config.cjs__
```
module.exports = {
  presets: [
    [ "@babel/preset-env", { targets: { esmodules: true, node: "current" } } ],
    [ "@babel/preset-react", { runtime: 'automatic' } ],
  ],
};

```

5. Opcional, pero eventualmente necesario, crear Jest config y setup:

__jest.config.js__
```
export default {
    testEnvironment: 'jest-environment-jsdom',
    setupFiles: ['./jest.setup.js']
  }

```

__jest.setup.js__
```
// En caso de necesitar la implementación del FetchAPI
import 'whatwg-fetch'; // <-- yarn add whatwg-fetch

```

