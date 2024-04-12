# Busquedas condicionales

# Operadores de comparación 
 | Operador | Descripción |
 | -- | -- |
 | $eq | igual |
 | $gt | mayor que |
 | $gte | mayor o igual |
 | $in | buscar un elemento en un array |
 | $lt | menor que |
 | $lte | menor o igual |
 | $ne | todos los elementos que no sean iguales |
 | $nin | ninguno de los valores del array |    

_Selecciona todos los documentos de una coleccion_


```m
db.Libros.find()
db.Libros.find({})
```


_Seleccionar todos los documnetos de la coleccion libros donde la editorial sea biblio_

```m
 db.libros.find({editorial: 'Biblio'})
```

_Seleccionar todos los documentos de la coleccion libros donde el precio sea igual a 25_

```m
 db.libros.find({precio: 25})
```

## Busquedas con operadores logicos

**Sintaxis**

```
{<columna>:
<operador>:<valor>}, ...
```

_Seleccionar todos aquellos documentos de la coleccion libros donde el precio sea mayor a 25_

```m
db.libros.find({precio: {$gt:25}})
```

_Seleccionar aquellos documentos de la coleccion libros donde el precio sean mayores o iguales a 20_

```m
db.libros.find({precio:{$gte: 20}})
```

_Seleccionar aquellos documentos donde la editorial sea Biblio o Planeta_

```
db.libros.find({editorial: {$in: ['Biblio', 'Planeta']}})
```

# Recuperar una sola fila

_Seleccionar todos aquellos docuemntos que sean biblio o planeta, pero 
mostrando solamenente el primer documento encontrado_

```
db.libros.findOne({editorial: {$in: ['Biblio', 'Planeta']}})
```

```
db.libros.findOne({})
```

# Operadores logicos

| Operador | Descripcion |
      | -- | -- |
| $and | Operador AND. Devuelve los documentos que cumple todas las condiciones |
| $or | Operador OR. Devuelve los documentos que cumplen alguna condicion |
| $not | Operador NOT. Invierte el resultado de una condicion |
| $nor | Devuelve los documentos que no cumplen las condiciones |
| $exist | Devuelve los documentos que tengan un campo completo |
| $type | Selecciona los documentos si un campo pertenece a un tipo especifico |

## Operador AND 

**Sintaxis** 

```
db.coleccion.find.({condicion1, condicion2})
```

```
db.coleccion.find.({$and: [condicion1, condicion2]})
```
_Seleccionar todos aquellos libros que valgan mas de 25 y cuya cantidad sea inferior a 15_

```
db.libros.find({precio: {$gt: 25}, cantidad: {$lt: 15}})
```

```
db.libros.find({and: [{precio: {$gte: 25}}, {cantadad: {$lt: 15}}, {editorial:{$eq: 'Biblio'}}]})
```

## Operador OR 

**Sintaxis** 

```
db.coleccion.find.({$or: [condicion1, condicion2]})
```

```m
 db.libros.find({$or: [{precio: {$gte: 25}},{cantidad: {$lt: 15}}]})
```


### OR y AND conbinadas

_Seleccionar los documentos de la editorial Biblio con precio mayor a 40 o libros de la editorial planeta con precio mayor a 30_

```
db.libros.find(
   {
       $or:[
         {$and:[{editorial:'Biblio'},{precio:{$gt:40}}]},
         {$and:[{editorial:'Planeta'},{precio:{$gt:30}}]}
         
         ]})
```