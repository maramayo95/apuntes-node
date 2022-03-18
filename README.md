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

### ATAJOS DE TERMINAL

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





