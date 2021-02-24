# practica-rest

## Parcial 2Videos
[Enunciado](https://docs.google.com/document/d/e/2PACX-1vTrjR1_gXCWCVU7Z2kxrERMH-QCBFjrCEZuDhsACxUXrqh6MryXGkcsPJn78f-jJ_6c92WwNdliq5wg/pub?urp=gmail_link&gxids=7628)

### Perfil de usuario

* Consultar perfil de usuario
```http
get /usuario/
```
* Editar usuario
```http
put /usuario/
BODY:
{
"nombre" : "nuevoNombre",
"apellido" : "nuevoApellido",
"email" : "nuevoEmail"
}
```
No hace falta utilizar un ID,  ya que el usuario se maneja a nivel sesión.

### Reproductor de videos

* Visualizar un video
```http
get /videos/:idVideo
```
* Buscar otros videos
```http
get /videos?titulo=unTitulo
```
Es la solución más simplista que se me ocurre ya que cuando buscamos un video, en realidad aplicamos un filtro un poco más amplio que el titulo.

* Iniciar la reproducción (lo que actualiza el contador de reproducciones)
```http
post /videos/:id/reproducciones
```
* Dar me gusta/deshacer me gusta
```http
post videos/:id/like

delete videos/:id/like
```
Aprovecho la misma ruta, cambiando solo el verbo.

### Editor de listas de reproducción

* Cambiar el nombre de la lista
```http
patch /reproductores/:id
BODY:
{
"nombre" : "nuevoNombre"
}
```

* Eliminar videos de la lista
```http
delete /reproductores/:idReproductor/videos/:idVideo
```

## Parcial 2Canciones
[Enunciado](https://docs.google.com/document/d/e/2PACX-1vQU0uBJt3OzNjQ45wUOSz1lx8RNKAdgnmGFGqVNjTxjTqXtywa4bLIdnN_1XGEBAdUjAJ9dqX86kf4w/pub?urp=gmail_link&gxids=7628)


### Perfil de usuario
Mismo sistema que para 2videos

* Consultar usuario
```http
get /usuario/
```

* Editar usuario
```http
put /usuario/
BODY:
{
"nombre" : "nuevoNombre",
"apellido" : "nuevoApellido",
"mail" : "nuevoMail"
}
```

### Reproductor de canciones

* Visualizar una canción
```http
get /canciones/:id
```
* Buscar otras canciones
```http
get /canciones?titulo=xyz
```
* Iniciar reproducción
```http
post /canciones/:id/reproducciones
```
* Dar me gusta/deshacer me gusta
```http
post /canciones/:id/like
delete /canciones/:id/like
```

### Listas de reproducción

* Visualizar un reproductor en específico
```http
get /reproductores/:id
```

* Cambiar nombre de la lista
```http
patch /reproductores/:id
BODY:
{
"nombre" : "nombreNuevo"
}
```

* Eliminar una canción
```http
delete /reproductores/:idReproductor/canciones/:idCanciones
```

## Parcial Aviones

### Listado de vuelos

* Busqueda de una fecha determinada o rango
```http
get /vuelos?fechaDesde=unaFecha&fechaHasta=otraFecha
```
Para que sea una fecha específica, unaFecha debe ser igual a otraFecha.

* Entrar al detalle de un vuelo
```http
get /vuelos/:id
```

### Detalle de un vuelo

* Agregar/quitar de favoritos.
Vale aclarar que cada usuario tiene una única lista de favoritos.
```http
post /favoritos/
BODY:
{
"idVuelo" : "unID"
}

delete /favoritos/:idVuelo
```

* Agregar/quitar de carrito de compras.
Lo mismo que con la lista de favoritos, todo usuario tiene un solo carrito de compras.
```http
post /carrito/
BODY:
{
"vueloID" : "unID",
"nroAsiento" : "nroAsiento",
---- más info relevante de un vuelo.
}

delete /carrito/:idItem
```
Mi intención no es guardar un vuelo en el carrito, sino un item. Así no solo tengo en cuenta el vuelo, sino también el asiento que quiero ocupar (puede ser turista/primera clase también). Así, al borrarlo luego no utilizo un id de vuelo, sino un id de item.
