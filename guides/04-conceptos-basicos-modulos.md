# Conceptos Básicos: Módulos

Saquemos del camino algunos conceptos básicos así estamos todos en sintonía.
Tomemos el ejemplo _limpio_ de nuestra app:

```jsx
import React from 'react';
import ReactDOM from 'react-dom';

function App() {
  return <p>Hola!</p>;
}

ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);
```

## Módulos

Tanto una app React como un componente React seguramente van a usar algún
`import`. Por ejemplo el import para react en sí es requerido:

```jsx
import React from 'react';
```

Por ejemplo si queremos en nuestra `App.jsx` importar un componente que se aloja
en `components/Component.jsx` usaremos.

```jsx
import Component from './components/Component';
```

Cosas a notar:

1. Los imports suelen ser _rutas_ a archivos.
2. En javascript, los archivos son comúnmente llamados _módulos_.
3. Usualmente no se necesita especificar la extención del archivo/modulo.
4. La ruta a módulos de nuestro propio código fuente siempre comienza con un
   punto o dos puntos seguidos. Ejemplos:
   - `'./Componente'` importa un modulo que se encuentra en el mismo nivel de
     directorios que el modulo que lo importa.
   - `'./components/Componente'` importa un modulo que se encuentra dentro de la
     carpeta _components_.
   - `'../Componente'` importa un modulo que se encuentra un nivel más _arriba_
     en la jerarquía de direcotrios.
   - `'../../Componente'` importa un modulo que se encuentra **dos** niveles más
     _arriba_ en la jerarquía de direcotrios.
5. La excepción a la regla **4** son los imports de módulos de terceros (los que
   instalamos usando npm y que se alojan en la carpete `node_modules` del
   proyecto y que se encuentran listados en el archivo `package.json` en el
   campo `devDependencies`). Estas rutas no usan puntos iniciales y no importa
   la jerarquía de directorios. Ejemplos:
   - `'react` importa la librería react.
   - `'react-dom` importa la librería react-dom.

## Definir un Módulo

Un módulo es en esencia un archivo javascript con la particularidad de que
define algunos `exports`. Estos exports se usan para definir qué contenido éste
modulo _expone_ al exterior. Es decir qué cosas estarán disponibles para ser
usadas por otros módulos y que cosas no.

> Un modulo puede declarar uno a más exports, pero nunca `0` exports.

Supongamos que creamos un módulo llamado `Title` en la ruta
`./components/Title.jsx`. El contenido puede ser el siguiente:

```jsx
function Title() {
  return <h1>Mi Título</h1>;
}

export default Title;
```

Ahora para usarlo en nuestra `App.jsx` podemos importarlo como sigue

```jsx
import Title from './components/Title';
```

O incluso podemos usar cualquier otro nombre...

```jsx
import CualquierOtroNombre from './components/Title';
```

Nuestro módulo **Title** expone un único _export_ usando el _keyword_ `default`.
El _keyword_ `default` se usa justamente para definir un export por _default_.
No es obligatorio que un módulo defina un `export default`. Veremos las
alternativas más abajo.

Podríamos también definir un _export default_ en una sola línea como sigue:

```jsx
export default function Title() {
  return <h1>Mi Título</h1>;
}
```

Supongamos que ahora queremos que nuestro módulo `Title` exponga otras cosas
aparte de un título `h1`. Para esto podemos usar los llamados _named exports_.
Ejemplo:

```jsx
export default function Title() {
  return <h1>Mi Título</h1>;
}

export function Title2() {
  return <h2>Mi Título 2</h2>;
}
```

Ahora nuestro módulo expone dos componentes, uno es de tipo _default_ y el otro
de tipo _named_ (este último no usa el keyword _default_). Ahora para usar
nuestro nuevo componente **Title2** podemos importarlo en nuestra App como:

```jsx
import Title, { Title2 } from './components/Title';
```

Los export de tipo _named_ los podemos importar usando los caracteres `{}` antes
de la clausula `from`. En este caso no podemos usar un nombre arbitrario sino
que tenemos que usar el mismo nombre con el que fué exportado. Por eso se los
llama _named exports_.

> Un modulo puede definir más de un modulo de tipo _named_ pero solo uno de tipo
> _default_.

Si nuestro modulo `Title` también definiera otro named export (como `Title3`),
en nuestra app lo podemos importar como:

```jsx
import Title, { Title2, Title3 } from './components/Title';
```

También podríamos no usar el export de tipo _default_:

```jsx
import { Title2, Title3 } from './components/Title';
```

Finalmente también existe la posibilidad de que un módulo exporte un mismo item
usando las dos versiones a la vez, _named_ y _default_:

```jsx
// versión `named`
export function Title() {
  return <h1>Mi Título</h1>;
}

// versión `default`
export default Title;
```

Ahora en nuestra app podemos importar el componente Title de cualquier forma

```jsx
import Title from './components/Title';
```

o...

```jsx
import { Title } from './components/Title';
```
