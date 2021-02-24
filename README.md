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
"nombre" : "nuevoNombre"
"apellido" : "nuevoApellido"
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
