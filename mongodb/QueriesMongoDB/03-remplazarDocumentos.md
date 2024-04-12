
# Remplazar documentos

```
 db.libros.replaceOne(
 {_id:2},
 {titulo:"De la tierra a la luna"},
 {autor: "Julio Berne"},
 {editorial: "Terra"},
 {precio:100}
 )

```

# Borrar documnetos

_dos metodos_

1. deleteOne
2. deleteMany


**Eliminar todo el documento con un id = 2**

```
db.libros.deleteOne({_id:2})
```


**Eliminar todos los documentos donde la cantidad sea mayor que 150**
```
db.libros.deleteMany({cantidad : {$gt:150}})
```

# Expresiones regulares

**Seleccionar todos los documentos que contengan en el titulo una t**

```m
db.libros.find({titulo: /t/ })
```

**Seleccionar todos los documentos que contengan en el titulo se encuentre la palabra JSON**

```m
db.libros.find({titulo: /JSON/ })
```

**Seleccionar todos los documentos que el titulo terminen con la palabra tos**

```m
 db.libros.find({titulo:/tos$/})
```

**selecionar todos los documentos en donde el titulo termine con una j**

```m
db.libros.find({titulo:/j$/})
```

## Operador $regex

**seleccionar todos los documentos donde el titulo contenga la palabra PARA**
```
db.libros.find({titulo: {$regex: 'para'}})
```

**seleccionar todos los documentos donde el titulo contenga la palabra JSON pero que sea case sensitive**

```m
db.libros.find({titulo: {$regex: /json/, $options: "i"}})
```

**seleccionar todos los documentos de la coleccion libros donde el titulo contenga la palabra tos al final y que sea case sensitive**

```m
db.libros.find({titulo: {$regex: /tos$/, $options: "i"}})
```

## Ver solo ciertas columnas

```
db.libros.find({},{titulo:1, _id: 0})
```

**seleccionar todos los documentos de la editorial planeta pero mostrando solamente el titulo y la editorial**

```
db.libros.find({editorial: 'Planeta'},{_id: 0, titulo:1, editorial: 1})
```

```
db.libros.find({editorial: {$regex: /PLANETA/, $options: "i"}}, {_id: 0, titulo:1, editorial: 1})
```

### Operador exist
_Permite buscar la existencia de una columna_

```
db.libros.find({titulo: {$exists: true }})
```

## Operador Type
_Columnas con enteros_

```
db.libros.find({precio: {$type:1 }}) 
```

```
db.libros.find({precio: {$type:'double' }}) 
```

```
db.libros.find({precio: {$type:16 }}) 
```

```
db.libros.insertOne({titulo: 'Java como programar', editorial: 1, })
```


## Tabla de tipos de datos en mongoDB

| Type | Number | Alias |
| - | - | - |
| Double |1|"double"|
| String |2| "string"|
| Object |3| "object" | 
| Array |4| "array" |
| Binary Data |5| "binData"|
| Undefined |6| "undefined" |
| ObjectId |7| "objectId" |
| Boolean |8| "bool" |
| Date| 9| "date"|
| Null |10| "null" |
| Regular expression|11| "regex"|
| DBPointer |12| "dbPointer"|
| JavaScript|13| "javascript"|
| Symbol | 14| "Symbol"|
| 32-bit integer|16| "int" |
| Timestamp|17| "timestamp" |
| 64-bit integer| 18| "long" |
| Decimal128 | 19| "decimal" |
| Min key |-1| "minKey" |
| Max key |127| "maxKey" |

## Operador $set
_Sirve para cambiar el valor de un campo dentro de una conexion_

```
db.libros.updateOne({titulo: 'Java como programas', {$set: {titulo: 'Java como programar' }}})
```

**Actualizar el valor de la cantidad a 50 y el precio a 10 donde el id sea igual a 9**

```
db.libros.updateOne({_id: 9},{$set:  {cantidad: 50, cantidad: 10}})
```

**Actualizar todos los documentos donde el precio sea mayor a 10 por el precio a 150**

```m
db.libros.updateMany({precio: {$gt: 10}}, {$set: {precio: 150}})
```

## Operador Sort
_permite ordenar_

**Ordenar todos los documentos de forma ascendente por la editorial y mostrar solamente el titulo, precio y editorial**

```
db.libros.find({}, {titulo: 1, precio:1, editorial:1, _id: 0}).sort({editorial:1})
```

_descendente_
```
db.libros.find({}, {titulo: 1, precio:1, editorial:1, _id: 0}).sort({editorial:-1})
```