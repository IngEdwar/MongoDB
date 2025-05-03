# MongoDB
Caso de uso: Almacenamiento de datos de una red social
Descripción del caso de uso:
Supongamos que estamos creando una red social donde los usuarios pueden crear perfiles, compartir publicaciones, hacer comentarios, agregar amigos y seguir a otros usuarios. Dado que los datos que se van a manejar tienen una estructura flexible (los usuarios pueden tener diferentes tipos de contenido y características personalizadas) y no necesariamente siguen un esquema rígido, una base de datos NoSQL como MongoDB es apropiada. MongoDB nos permitirá gestionar de manera eficiente los datos semi-estructurados y realizar consultas rápidas sobre grandes volúmenes de datos.
Diseño del esquema en MongoDB:
MongoDB se basa en colecciones y documentos. En este caso, podemos tener varias colecciones para organizar los datos, como: usuarios, publicaciones, comentarios, amigos, y seguimientos.
1. Colección de usuarios: usuarios
Esta colección almacena la información básica de cada usuario.
Campos:
•	_id: Identificador único del usuario.
•	nombre: Nombre completo del usuario.
•	correo: Correo electrónico único.
•	fecha_nacimiento: Fecha de nacimiento del usuario.
•	ubicacion: Ubicación geográfica.
•	biografia: Descripción o biografía del usuario.
•	amigos: Lista de identificadores de amigos (referencias a otros documentos en la colección usuarios).
•	seguidores: Lista de identificadores de usuarios que siguen a este usuario.
•	seguido_por: Lista de identificadores de usuarios que este usuario sigue.
2. Colección de publicaciones: publicaciones
Esta colección almacena las publicaciones de los usuarios.
Campos:
•	_id: Identificador único de la publicación.
•	usuario_id: Referencia al documento del usuario que realiza la publicación.
•	contenido: Texto de la publicación.
•	fecha_publicacion: Fecha y hora de la publicación.
•	likes: Número de "me gusta" recibidos.
•	comentarios: Lista de objetos que representan comentarios sobre la publicación, con el usuario_id, contenido del comentario, y la fecha_comentario.
•	etiquetas: Etiquetas asociadas a la publicación (por ejemplo, hashtags).
3. Colección de comentarios: comentarios
Aunque los comentarios están incrustados dentro de las publicaciones, podríamos tener una colección separada para gestionar de manera más eficiente los comentarios, especialmente si hay una gran cantidad.
Campos:
•	_id: Identificador único del comentario.
•	publicacion_id: Referencia a la publicación a la que pertenece el comentario.
•	usuario_id: Referencia al usuario que realiza el comentario.
•	contenido: Texto del comentario.
•	fecha_comentario: Fecha y hora del comentario.
4. Colección de amigos: amigos
Podemos almacenar una relación de amistad entre dos usuarios. Esta colección tendría dos campos principales, pero podrían expandirse según sea necesario.
Campos:
•	_id: Identificador único de la relación.
•	usuario1_id: Referencia a un usuario.
•	usuario2_id: Referencia al otro usuario.
•	fecha_amigos: Fecha en que se convirtió en amistad.
5. Colección de seguimientos: seguimientos
Esta colección almacena las relaciones de seguimiento entre usuarios.
Campos:
•	_id: Identificador único del seguimiento.
•	seguidor_id: Referencia al usuario que sigue.
•	seguido_id: Referencia al usuario que está siendo seguido.
•	fecha_seguimiento: Fecha del seguimiento.
