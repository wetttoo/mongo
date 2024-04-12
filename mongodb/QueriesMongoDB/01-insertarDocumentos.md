
## Insertar documentos 



*Inserta un solo documento*
```
db.Alumnos.insertOne(
... {
...  nombre: "Maximiliano"
... });
```
 
 
 _inserción de un documento mas complejo con array_

 ```
 db.Alumnos.insertOne(
... {
...   nombre: "Azul",
...   edad: 22,
...   apellidos: "Cabeza de vaca",
...   aficiones: ["Paracaidismo", "Lectura", "Futbol"]
... })
```

_inserciones de documento con subdocumentos_ 

```
db.Alumnos.insertOne(
... {
...   nombre: "Raul",
...   edad: 67,
...   cv: {
...       "informatica": "Bueno",
...       "Marketing": "Bajo",
...       "Contabilidad": "Medio"
... }
... })
```

_insercion de documento id personalizado_

```
 db.Alumnos.insertOne(
... {
...   _id: 1,
...   "nombre": 'Arcadia'
... })
```

_insertar multiples documentos_

```m
 db.Alumnos.insertMany(
... [
...  {
...   _id:2,
...   nombre: "Diana",
... },
... {
...   _id:3,
...   nombre: "Flor",
...   edad: 43
... },
... {
...  _id:4,
... nombre: "Francisco",
... edad: 34,
... aficion: "El agua",
... desgracia: "Ex"
... }
... ]);
```

---

