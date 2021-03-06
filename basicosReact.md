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

## Crear un componente

Para crear un compñonente nuievop se recomienda crear dentro del sirectorio src un directorio llamado componentes de esta manera
src/componentes y otro para los css src/css donde despues seran importados y exportados segun sea el caso.

Se recomienda que un compionete se le llame con la primera letra mayuscula por ejemplo "PrimerComponente.js"

PrimerComponente.js

``` JavaScript
import React from 'react';

class PrimerComponente extends React.Component{
    render(){
        return <p>Hola mundo</p>
    }
}

export default PrimerComponente;
```

index.js

``` JavaScript
import React from 'react';
import ReactDOM from 'react-dom';
import PrimerComponente from 'componentes/PrimerComponente';
import registerServiceWorker from './registerServiceWorker'

ReactDOM.render(<PrimerComponete />,document.getElementById('root'));
registerServiceWorker();
```

## Tipos de componentes

* Te permite separar tu codigo.
* Son como funciones en JavaScript
* Puedes pasarle datos por medio de lago llamado props

### Class Component

``` JavaScript
class PrimerComponente extends React.Component{
    render(){
        return <p>Hola mundo</p>
    }
}
```

### Functional Component

``` JavaScript
const App = (props) => (
    <p>Hola mundo</p>
);
```

#### Ventajas

* La cantidad de codigo es menos y es mas facil de leer
* Facil de probar
* No puedes usar this

#### Desventajas

* No puedes usar los metodos del ciclo de vida
* No tiene State
* No puedes usar refs
* No puedes usar formularios

## Componentes dentro de componentes

Los componentes pueden integrarse a componentes princiales ode mayor rango por ejemplo.

index.js

``` JavaScript
import React from 'react';
import ReactDOM from 'react-dom';
import App from 'componentes/App';
import registerServiceWorker from './registerServiceWorker'

ReactDOM.render(<App />,document.getElementById('root'));
registerServiceWorker();
```

App.js

``` JavaScript
import React from 'react';
import Header from './Header';
import Productos from './Productos';
import Footer from './Footer';

class App extends React.Component{
    render(){
        return (
            <div>
                <Header />
                <Productos />
                <Footer />
            </div>
        )
    }
}

export default PrimerComponente;
```

Header.js

``` JavaScript
const Header = () => (
    return (
        <header>
            <h1>Bienvenido a la tienda virtual</h1>
        </header>
    );
);

export default Header;
```

Productos.js

``` JavaScript
import React from 'react';

class Productos extends React.Component{
    render(){
        return (
            <div>
                <ul>
                    <li>Computadoras</li>
                    <li>Servidores</li>
                    <li>Gateways</li>
                </ul>
            </div>
        )
    }
}

export default PrimerComponente;
```

``` JavaScript
const Footer = () => (
    return (
        <footer>
            <p>Todos los derechos reservados &copy;</p>
        </footer>
    );
);

export default Footer;
```

## Propr o propiedades en react

Los cambios, como por ejemplo los cambios que pueden generar un llamado AJAx generalmente se guardan en el state o en los props.

La forma en que los datos se comunican entre los props deben de ser de padre a hijos, como lo muestra el siguiente ejemplo.

App.js

``` JavaScript
import React from 'react';
import Header from './Header';
import Productos from './Productos';
import Footer from './Footer';

class App extends React.Component{
    render(){
        const productos = [
            {nombre:"Libro", precio:200},
            {nombre:"Disco de musica", precio:100},
            {nombre:"Instrumento musical", precio:800}
        ];
        return (
            <div>
                <Header titulo = "Nuestra tienda virtual"/>
                <Productos productos={productos}/>
                <Footer />
            </div>
        )
    }
}

export default PrimerComponente;
```

Header.js

``` JavaScript
const Header = (props) => (
    return (
        <header>
            <h1>Bienvenido a {props.titulo}</h1>
        </header>
    );
);

export default Header;
```

Productos.js

``` JavaScript
import React from 'react';
import Producto from 'Producto';

class Productos extends React.Component{
    render(){
        return (
            <div>
                <h2>Listado de productos</h2>
                {Object.keys(this.props.productos).map(key=>(
                    <Producto 
                        key={key}
                        producto = {this.props.productos[key]}
                    />
                ))}
            </div>
        )
    }
}

export default Productos;
```

**Nota: Los datos que son repetitivos con en este caso los son los productos, se repite siempre un producto, la estrategia correcta seria crear un componente para imprimir cada porducto en un componente nuevo**

Producto.js

``` JavaScript
import React from 'react';

class Producto extends React.Component{
    render(){
        const {nombre, precio} = this.props.producto;
        return (
            <div>
                <h2>{nombre}<h2>
                <p>precio: {precio}<p>
            </div>
        )
    }
}

export default Producto;
```

## State y metodos de ciclo de vida

El state es el que se encarga de administra los cambios en los datos en la aplicacion y se encarga de cambiarlos en cada uno de los componentes y en el html

App.js

``` JavaScript
import React from 'react';
import Header from './Header';
import Productos from './Productos';
import Footer from './Footer';

class App extends React.Component{
     state  = {[]};

     componentDidMount(){
         this.setState({
            productos:[
                {nombre:"Libro", precio:200},
                {nombre:"Disco de musica", precio:100},
                {nombre:"Instrumento musical", precio:800}
            ]
         });
     }

    render(){
        return (
            <div>
                <Header titulo = "Nuestra tienda virtual"/>
                <Productos productos={productos}/>
                <Footer />
            </div>
        )
    }
}

export default PrimerComponente;
```