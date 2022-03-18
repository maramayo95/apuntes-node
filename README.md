# apuntes-node
Un repositorio el cual uno puede acceder a la documentación básica para back

# NPM
Las dependencias tienen dos formas de instarse (global o local). En la forma global todos los programas que desarrollemos en Node Js tendrán esa librería. 

```
npm install -g nombre-de-la libreria
````

De forma local se puede elegir que librería usar acorde a cada proyecto 

```
npm install  nombre-de-la libreria
````

##
## Crear archivos en formato JSON

Para crear un archivo de formato JSON que contenga la lista de dependencias se puede realizar mediante éste código.

```
npm init -y
```
### Versionado 
Es importante tener en cuenta en los versionados la función que cumple cada numero.

* El primero corresponde a actualizaciones grandes/significativas con respecto al funcionamiento del programa

* El segundo corresponde a actualizaciones pequeñas que agregan funciones nuevas o cambian algún detalle

* El último numero corresponde a la corrección de Patches (bugs)
```
1.0.0 (La nomenclatura inicial suele ser ésta)
```
### Actualizaciones

* Para realizar una actualización de patches o actualización menor se utiliza el caracter " ^ " (Circunflejo). 
* Para realizar todas las actualizaciónes se utiliza " * " 

# ATAJOS DE TERMINAL

* Para crear un nuevo archivo se suele utilizar este codigo

```
New-item nombreDelArchivo.formato
```

*  Para crear una nueva carpeta se suele usar el siguiente código

```
mkdir nombreDelDirectorio
```

* Para ir a un directorio específico se utiliza

```
cd nombreDelDirectorio
```

* Para ir atras se utliliza 

```
cd ..
```


# Servidores Web 

### Instalar Nodemon 

```
 npm i -g nodemon 
```

Para la ejecución de node conviene modificar el package.json en la sección scripts

```
"dev": "nodemon ./index.js",
```

Lo que nos permitirá luego poder ejecutar nodemon desde la terminal de la siguiente forma

```
 npm run nodemon
```

### Instalar Express

Para poder instalar express se requiere el siguiente codigo el cual se deberá ingresar en la terminal

```
 npm install express --save
```

### Uso del módulo

*Express nos permite definir, para cada tipo de petición HTTP que llegue a una determinada URL , qué acciones debe tomar, mediante la definicion de un callback para ecada caso que consideremos necesario incluir en nuestra API*

* Su ejecución se realiza de la siguiente forma : 

```
 const express = require('express')
 const app = express()
```

### Conexión del servidor

```
const PORT = 8080

const server = app.listen(port, ()=> {
    console.log(`Listening to request on http://localhost:${port}`)
})

```

De ésta forma al declarar el console.log() con string interpolation nos permite acceder desde la terminal al enlace donde esta levantado el servidor. 


### Manejo de errores en el servidor 
```
server.on("error", error => console.log('Error en el servidor'))

```




### API RESTful

GET / POST / PUT / DELETE => *Se suelen establecer estos tipos de peticiones a través del protocolo HTTP (Protocolo de transferencia de HiperTexto) el cual se usa para intercambiar datos a traves de internet*

*Se las denomina aplicaciones RESTful , a aplicaciones que operan en forma de servicios web, respondiendo consultas a otros sistemas a través de internet. *





**HTTP : Códigos de Estado  **

* 1xx (Informativo) : La petición fue recibida y continua su proceso
* 2xx (Éxito) : Petición realizada con éxtio
* 3xx (Redirección) : Mas acciones son requeridas para realizar la petición
* 4xx(Error del cliente) : La petición tiene errores y no puede ser procesada
* 5xx (Error del servidor) : El servidor falló al intentar la petición


![codigos-estado](https://user-images.githubusercontent.com/84943598/159064689-0a0a4041-4855-4040-942e-ab12b8077f2e.jpg)

# Tipos de peticiones (GET , POST, PUT , DELETE)

*Cuando se usan estas peticiones se suele trabajar con JSON (Javascript Object Notation) por ende se debe ejecutar éste código antes de hacer cualquier tipo de petición.

```
app.use(express.json())
app.use(express.urlencoded({ extended: true}))

```

## Configuración petición GET 

La forma por la cual obtenemos información desde el servidor es mediante las peticiones de tipo GET. 

Su sintaxis es la siguiente: 

```
app.get("/", (req,res)=> {
    res.send( {mensaje : 'hola mundo} ) 
})

```

* req = request (petición)
* res = response (respuesta)

*Las peticiones GET devuelven un objeto como resultado*

### Parametros en Get

*Los parámetros se manejan del a siguiente forma *

* Se agregan al final con un  ? 
* Se enumeran pares de 'clave=valor'
* Se separan mediante un &
* Para recibirlos se encuentran en el objeto 'query' dentro de la petición req (el primer parámetro de los dos)

###### Ejemplo de GET con identificador
```
app.get("/api/mensajes/:id", (req,res)=> {
    res.send( 'Get recibido'  ) 
    
    // se opera con req.params.id
    
    // res.json(recursoBuscado) 
})

```

*Para acceder al parametro dinamico que ofrece la url se hace de la siguiente forma *

```
req.params.id
```

*Se utiliza este comando para devolver en json el resultado del get
```
res.json()
```

## Configuración en Petición Post 

*El método POST se suele utilizar para enviar datos desde un cliente hacia un servidor. Por ejemplo para crear n nuevo registro.*

*Para poder acceder al cuerpo del mensaje se hace a través del  campo 'body '

* Aqui veremos un ejemplo claro con un form hecho en HTML 

*Desde el front:* 
```
<form action="/formulario" method="post">
    <input type="text" name="nombre" placeholder="nombre" />
    <input type="text" name="apellido" placeholder="apellido" />
    <button type="submit">Enviar</button>
</form>

```

*Desde el back:*

```
app.post("/formulario", (req, res) => {
    const {title, price, year} = req.body ; // undefined
    res.send(variables);
});

```

*Se puede utilizar la desestructuración para poder operar con los distintos inputs que ofrece el body y almacenarlos a cada uno en una variable para luego poder operar con ellos* 


## Petición Put

*Se utiliza Put para actualizar un registro con uno nuevo

```
app.put('/api/:company', function(res,req) {
   const actualizarProducto = 
   recurso con id == (req.params.id,req.body)
    res.send(producto)
}
```

*En este caso la petición PUT llama a éste método traido de una Class que hace ésta ejecución


## Peticion DELETE

*Esta peticion sirve para eliminar un recurso. El cual debe ser identificado mediante la req.params que tenga la url (id)*

```
app.delete('/api/:company', function(res,req) {
   const actualizarProducto = 
   recurso con id == (req.params.id,req.body)
    
    //Se debe validar si el producto existe para ser eliminado 
     if(producto){
           res.send(`Se elimino ${req.params.id} `)
       } else {
           res.status(404).send({error: 'No existe el producto que estas buscando'})
       }
    
}
```



