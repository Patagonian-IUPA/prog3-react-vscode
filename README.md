# Guía para empezar con ReactJS y VSCode rápido

## Software requerido

### NodeJS

Tenemos que instalar **NodeJS** si no está instalado aun. La instalación es muy
sencilla. Fijate acá: https://nodejs.org/es/.

### Extensiones VSCode (Opcionales)

Estas extensiones para vscode son todas **opcionales** pero muy útiles que
podemos instalar.

- `dbaeumer.vscode-eslint`: extensión que reconoce los errores más comunes en
  javascript (y también ReactJS) y nos subraya el código con un interlineado
  amarillo o rojo a medida que codeamos.
- `esbenp.prettier-vscode` extensión que se encarga de _autoformatear_ el código
  usando reglas de estilo estándarres cada vez que usamos la combinación de
  teclas `ctrl+shift+f`.

## Crear una app react

Seguimos los mismos pasos que están en la guiá oficial:
https://create-react-app.dev/docs/getting-started

1. Decidir el nombre de la app (el nombre es lo que determina el nombre del
   directorio donde va a vivir el código fuente). Por ejemplo
   `reemplazar_esto_con_el_nombre_de_mi_app`.
2. Abrir un terminal.
3. Usando el comando `cd` _pararce_ en la carpeta en donde usualmente guardamos
   el código ( ejemplo `cd reemplazar_esto_con_la_ruta_a_mis_proyectos`) y una
   vez ahí, correr los siguientes comandos en orden uno por uno:

```
npx create-react-app reemplazar_esto_con_el_nombre_de_mi_app
cd reemplazar_esto_con_el_nombre_de_mi_app
npm start
```

**Tip opcional**: Podés automatizar todo el proceso concatenando todo con `&&`
en una sola linea. Copiar, pegar (reemplazar) y darle _Enter_:

```bash
npx create-react-app reemplazar_esto_con_el_nombre_de_mi_app && cd reemplazar_esto_con_el_nombre_de_mi_app && npm start
```

### Qué fue eso?

- Instalé `create-react-app` en mi sistema.
- Cree una app react dentro de `reemplazar_esto_con_el_nombre_de_mi_app`.
- Inicialicé un proyecto GIT con un único commit con el mensaje
  `Initialize project using Create React App`.
- Instalé las dependencias necesarias.
- Creé un servidor de desarrollo en el puerto `3000` que sirve la aplicación.
- Disparé la compilación necesaria para ReactJS.
- Abrí mi navegador para ver el resultado que se está sirviendo en el puerto
  `3000`.

Ya tenemos una app react corriendo, con todo el entorno de desarrollo y manejado
por GIT. Ahora solo queda abrir VSCode en la carpeta del proyecto. Abrimos un
terminal nuevo o un nuevo tab (el anterior ahora está ocupado) y corremos el
comando `code .` dentro de la carpeta de la app react.

## Iniciar una app ya creada

Ahora que nuestra app ya está creada, la próxima vez que querramos continuar
codeando en nuestra app, no será necesario correr otra vez todos los comandos de
instalación:

```bash
cd reemplazar_esto_con_el_nombre_de_mi_app
npm start
```

Tener en cuenta que el terminal que usamos para iniciar el proyecto quedará
ocupado corriendo el compiladoer de react y observando los cambios en el código
y refrescando el navegador cada vez que hagamos cambios en el código.

## Errores?

Muchas veces vamos a ver los error directamente en el navegador y después de
corregirlos, todo vuelve a la normalidad. Pero puede que también haya ocasiones
en las que notamos que nuestros cambios no se están viendo reflejados en en
navegador ni tampoco vemos mensajes de error. En esos casos, es muy provable que
podamos ver un error en el terminal que está corriendo el compiladoer y no en el
navegador.

Habrá ocasiones en que vamos a necesitar reiniciar la compilación "apagando" el
compilador y corriendo `npm start` otra vez. Por ejemplo:

- El compilador se quedó colgado mostrando un error que en realidad ya no
  existe.
- Por alguna razón el compilador se colgó y ya no re-compila nuestros cambios a
  pesar de que ya arreglamos los errores.

Si después de apagar el compilador y correr `npm start` el error sigue
suscediendo entonces es provable que aun tengamos un error en nuestro código y
que tengamos que identificarlo y resolverlo antes de intentar re-iniciar de
nuevo.

## Y ahora qué hago?

Si te trabaste en algún lado, tenés dudas, consultas, o crees que podemos
mejorar esta guía desde tu punto de vista,
[abrí un nuevo _issue_](https://github.com/Patagonian-IUPA/prog3-react-vscode/issues)
en este repositorio y expresate. Tu inquietud puede ayudar a otros.

## Guiás siguientes

- [Descripción de la estructura de archivos y directorios](guides/01.estructura-de-directorios.md)
- [Limpieza del directorio src](guides/02.limpieza-del-directorio-src.md)
