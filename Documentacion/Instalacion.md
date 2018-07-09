# Preparando entorno para usar PostCSS

## Instalación Básica
### Crear un proyecto con npm
1. Ingresamos a la carpeta de nuestro proyecto y colocamos lo siguiente:
```
npm init
```
2. Rellenar los campos que nos solicita para crear el archivo package.json

### Instalar postcss cli de forma local
```
npm i -D postcss-cli --save
```
### Llamar al cliente
```
npx postcss
```
### Configurar a dónde ser irá nuestro archivo manipulado
1. agregar en dónde esta el css original
2. -o indica que se ingresará el output, path destino
3. -w significa watch, que estará viendo los cambios
```
npx postcss src/css/...path -o dist/css/...path -w

```

## Plugins
[Plugins existentes de PostCSS]: https://www.postcss.parts/

### Autoprefixer
```
npm install --save autoprefixer
```
Para utilizarlo se puede hacer de dos formas
1. agregar -u más el nombre del plugin
```
npx postcss src/css/...path -o dist/css/...path -w -u autoprefixer
```
2. crar un archivo de configuracion

#### Crear archivo de configuración
1. agregar en la raiz del proyecto el archivo postcss.config.js
2. requerir los plugins

```javascript
module.exports = {
	plugins: [
		require('autoprefixer')({
        grid: true
      })
	]
}
```

### CSSNEXT
incluye un plugin por cada instruccion de css4 para que sea compatible

[Ver este post, al parecer ya no existe cssnext]: https://moox.io/blog/deprecating-cssnext/ 

```
npm install postcss-cssnext --save
```
Ahora incluir el plugin

```javascript
module.exports = {
  plugins: [
    require('postcss-cssnext')({
        features: {
          autoprefixer: {
            grid: true,
          }
        }
      })
  ]
}
```