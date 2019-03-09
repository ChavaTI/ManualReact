# Basicos de ReactJS

## Create-recat-app

 Es una herramienta que facilita lña creaciones de aplicaciones de ReactJS
 ya que configura automaticamente babel y webpack
requiere NodeJS o Yarn

### Webpack

Es un bulder (paquete) de modulos para aplicaciones JavaScreipt modernas, webpack
procesa toda la aplicacion y mapea todas las dependecians de un modulo , con esto crea uno o vario paquetes o bundlers, poidras tener un servidor Live Reload

## Babel

Sireve para la configuracion de  codigo viejo con el nuevo codigo, si tienes modulos escritop en una version antigua de JavaScript,Babel lo convierte a codigo moderno

Para instalar create-react-app solo falta con escribir el comando

``create-react-app NombreDelPropyecto``

y para iniciar el proyecto, ya dentro dl directorio podemos ejecutar el proyecto con 

``npm start``

## React sin JSX

Es un tipo de lenguaje donde puedes mesclar javaScript con html

``` JavaScript

const titulo = React.createElement(
    'h1',
    {id:'titulo', className:'encabezado'},
    'Hola Mundo'
)

ReactDOM.render(titulo,document.getElementById('root'));
```

En el caso en el que se exporte e importe una clase mseria de la siguiente manera

App.js

``` JavaScript
import React, { Component } from 'react';
import './App.css'

class App extends React.Component {
    render(){
        return(
           React.createElement(
            'h1',
            {id:'titulo', className:'encabezado'},
            'Hola Mundo'
            )
        );
    }
}

export default App;
```

index.js

``` JavaScript
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';

ReactDOM.render(<App/>, document.ElementById('root'));
```

## React  con JSX

JSX es una extencion de JavaScript donde conbvinas codigo html con codigo javaScript, en nuestro ejemplo seria asi

App.js

``` JavaScript
import React, { Component } from 'react';
import './App.css'

class App extends React.Component {
    render(){
        const nombre = 'Salvador';
        return(
           <div>
                <p>Hola mundo</p>
                <p>Lo que esta entre llaves es codigo de javascript {console.log("Hola mundo");}</p>
                <p>Tambien puedes usar variables fuera del return por ejemplo:</p>
                <p>Hola {nombre}</p>
           </div>
        );
    }
}

export default App;
```

