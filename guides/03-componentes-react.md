# Componentes React

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

Nuestra **App** es en esencia un componente React.

Los componentes react son básicamente funciones javascript con algunas
particularidades principales:

- Se definen usando la forma _TitelCased_ en la cual cada palabra comienza con
  mayúscula. Por ejemplo `MyComponent` o `MuSuperComponent`.
- Solo aceptan un único parametro usualmente llamado _props_. Este parámetro es
  un objeto javascript que puede contener propiedades arbitrarias aunque siempre
  contiene una propiedad llamada `children`. Veremos el uso de `children` más
  abajo.
- Siempre deben retornar algo. Usualmente retornan **elemenos** react en
  sintaxis JSX (sintaxis similar al HTML), pero también pueden retornar `null`
  por ejemplo.

Definamos nuestro primer componente. Un componente llamado _Title_ que renderiza
un elemento `<h1>` y usémoslo en nuestra **App**:

```jsx
import React from 'react';
import ReactDOM from 'react-dom';

// nuevo componente Title
function Title() {
  return <h1>Hola!</h1>;
}

function App() {
  // Uso del componente Title
  return <Title />;
}

ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);
```

Todo muy lindo pero nuestro componente Title siempre imprime el mismo título y
por lo tanto no es flexible ni reusable. Hagamos que nuestro componente acepte
una _prop_ que llamaremos `value` así podemos especificár el título:

```jsx
// ahora nuestro componente usa el objeto `props`
// y una propiedad definida dentro que se llama `value`
function Title(props) {
  return <h1>{props.value}</h1>;
}

function App() {
  // Uso del componente Title con el valor "Hola Mundo!"
  return <Title value="Hola Mundo!" />;
}
```

Genial. Ahora podemos utilizar el componente Title varias veces con diferentes
títulos".

```jsx
function App() {
  // Uso del componente Title con el valor "Hola Mundo!"
  return (
    <>
      <Title value="Hola Mundo!" />
      <Title value="Hello World!" />
    </>
  );
}
```

**Cosas a notar**

- Si prestamos atención, vemos que el último ejemplo usa algo como unas
  etiquetas html sin nombre `<>` y `</>`. Estas etiquetas se llaman _Fragments_
  y se usan en los casos de que nuestro componente retorne mas de un elemento.
  Esto es porque un componente react solo puede retornar un único elemento
  _padre_. También podríamos solucionar el problema encerrando todo con un
  `<div>` por ejemplo, pero no siempre es algo que queremos hacer ya que agrega
  contenido innecesario en nuestro html. Las etiquetas _Fragment_ por el
  contrario no agregan nada al resultado final.
- También vemos en el componente `<Title/>` que se usan llaves (`{}`) para
  encerrar los valores javascript que queremos renderizar. Este proceso se suele
  llamar _interpolar_. Es el proceso de tomar las variables o propiedades
  encerradas entre llaves y transformarlas en _strings_ (texto) utilizando los
  valores que estas variables o propiedades contienen.

## Uso de la propiedad "children"

Dijimos más arriba que los componentes react aceptan un único parámetro, que
este parámetro es un objeto y que este objeto siempre contiene una propiedad
llamada `children` la usemos o no. Para qué sirve la propiedad children?

En HTML estamos acostumbrados a construir el árbol HTML encerrando etiquetas
dentro de otras etiquetas. Ejemplo:

```html
<body>
  <div id="container">
    <h1>Hola!</h1>
  </div>
</body>
```

En ReactJS podemos hacer lo miso usando la propiedad `children`. Supongamos que
no nos convence el hecho de tener que pasar la propiedad `value` a nuestro
componente Title como venimos haciendo:

```jsx
<Title value="Hola Mundo!" />
```

Sino que queremos usar un enfoque más parecido al html:

```jsx
<Title>Hola Mundo!</Title>
```

Podemos editar nuestro componente `Title` para que use la propiedad `children`
en vez de `value` y lograr eso:

```jsx
function Title(props) {
  // en vez de usar `props.value` usamos `props.children`
  return <h1>{props.children}</h1>;
}
```

Ahora nuestro componente Title parece bastante más natural y podemos hacer de
cuenta que es un elemento HTML más:

```jsx
function App() {
  return (
    <Title>
      Hola <i>Mundo</i>!
    </Title>
  );
}
```

Es normal tener un componente que usa otros componentes de esta manera:

```jsx
function App() {
  return (
    <ArticleContainer>
      <Title>
        Hola <i>Mundo</i>!
      </Title>
      <Paragraph>
        Párrafo de mi articulo
        <EnNegrita>
          <DeColorRojo>importante</DeColorRojo>
        </EnNegrita>!
      </Paragraph>
    </ArticleContainer>
  );
}
```

## Tarea Sugerida

Cómo definirías los componentes React del ejemplo anterior
`<ArticleContainer>, <Title>, <Paragraph>, <EnNegrita>, <DeColorRojo>`?
**Ayuda:** Podés usar el siguiente esqueleto:

```jsx
import React from 'react';
import ReactDOM from 'react-dom';

function ArticleContainer(/* definir props */) {
  // definir return
}

function Title(/* definir props */) {
  // definir return
}

function Paragraph(/* definir props */) {
  // definir return
}

function EnNegrita(/* definir props */) {
  // definir return
}

function DeColorRojo(/* definir props */) {
  // definir return
}

function App() {
  return (
    <ArticleContainer>
      <Title>
        Hola <i>Mundo</i>!
      </Title>
      <Paragraph>
        Párrafo de mi articulo
        <EnNegrita>
          <DeColorRojo>importante</DeColorRojo>
        </EnNegrita>!
      </Paragraph>
    </ArticleContainer>
  );
}

ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);
```

### Siguiente

- [Módulos Javascript](04-modulos-javascript.md).
