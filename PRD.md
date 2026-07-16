# PRD-001: Paretto — PWA para documentar y descubrir murales urbanos geolocalizados

## Contexto y Problema

Las frases, grafitis artísticos y murales urbanos suelen ser efímeros. Muchas personas encuentran obras interesantes en la calle, pero no existe una forma simple de documentarlas y descubrir otras cercanas creadas o registradas por la comunidad.

### 1. Solución

Una aplicación web (PWA) donde los usuarios pueden:

* Subir una fotografía de un mural o frase urbana.
* Registrar la ubicación donde fue encontrada.
* Explorar murales cercanos cargados por otros usuarios.
* Visualizar los murales en un mapa.

### 2. Usuarios

* Usuario Explorador: Persona interesada en arte urbano, fotografía o turismo local.
* Usuario Colaborador: Persona que desea registrar y compartir murales encontrados en la ciudad.

### 3. Alcance del MVP

* Registro de murales.
* Foto.
* Geolocalización.
* Mapa de murales cercanos.
* Lista de murales cercanos.
* Visualización de detalle.
* Autenticación de usuarios (usuario/contraseña y Google).
* Manejo de casos límite: permisos de ubicación denegados, imágenes inválidas, fallos de guardado y ausencia de resultados cercanos.
* **Moderación mínima de contenido:**
  * Estado "pendiente" para murales recién subidos, no visibles públicamente hasta ser aprobados o validados.
  * Reporte de murales por parte de los usuarios.
  * Validación automática básica para bloquear contenido NSFW antes de su publicación.

---


## Objetivos

Permitir que una persona capture un mural y que otra persona pueda descubrirlo cerca de su ubicación.

---

## Requerimientos Funcionales

### RF-001 Crear mural

El sistema debe permitir subir una fotografía de un mural.

### RF-002 Registrar ubicación automática

El sistema debe permitir asociar la ubicación GPS actual al mural.

### RF-003 Registrar ubicación manual

El sistema debe permitir ingresar una ubicación manualmente.

### RF-004 Guardar mural

El sistema debe almacenar fotografía, ubicación y fecha de creación.

### RF-005 Buscar murales cercanos

El sistema debe mostrar murales ubicados dentro de un radio configurable alrededor del usuario.

### RF-006 Mostrar mapa

El sistema debe mostrar marcadores de murales sobre un mapa.

### RF-007 Ver detalle de mural

El sistema debe mostrar la fotografía, fecha y ubicación de un mural seleccionado.

### RF-008 Ordenar por cercanía

El sistema debe ordenar los resultados por distancia al usuario.

### RF-009 Detectar denegación de permisos de ubicación

El sistema debe detectar cuándo el usuario no otorga permisos de geolocalización.

### RF-010 Rechazar imagen inválida

El sistema debe rechazar imágenes que superen los 10 MB o tengan un formato no soportado.

### RF-011 Detectar fallo en el guardado

El sistema debe detectar errores ocurridos durante el proceso de guardado del mural (fotografía, ubicación o metadatos).

### RF-012 Informar ausencia de resultados cercanos

El sistema debe informar al usuario cuando no existan murales dentro del radio de búsqueda configurado.

### RF-013 Estado "pendiente" de publicación

El sistema debe marcar todo mural recién creado como "pendiente" y ocultarlo de las búsquedas y el mapa públicos hasta que sea validado por un usuario administrador.

### RF-014 Reportar mural

El sistema debe permitir a cualquier usuario reportar un mural publicado por contenido inapropiado, duplicado o ubicación incorrecta.

### RF-015 Validación automática básica de contenido NSFW

El sistema debe ejecutar una validación automática sobre cada imagen subida y bloquear su publicación si se detecta contenido NSFW.

### RF-016 Ofrecer ingreso manual de ubicación al denegar permisos

El sistema debe ofrecer la opción de ingreso manual de ubicación cuando el usuario deniega los permisos de geolocalización, sin interrumpir el flujo de registro.

### RF-017 Notificar motivo de rechazo de imagen

El sistema debe mostrar al usuario un mensaje indicando el motivo por el cual se rechazó la imagen (tamaño superior a 10 MB o formato no soportado).

### RF-018 Bloquear continuación con imagen inválida

El sistema debe impedir que el usuario continúe el registro del mural mientras la imagen adjunta no sea válida.

### RF-019 Notificar error de guardado

El sistema debe notificar al usuario cuando ocurre un error durante el proceso de guardado del mural.

### RF-020 Preservar datos al fallar el guardado

El sistema debe preservar la fotografía y ubicación ya ingresadas cuando ocurre un error en el guardado.

### RF-021 Sugerir ampliar radio de búsqueda

El sistema debe sugerir al usuario ampliar el radio de búsqueda cuando no existan murales en el radio actual.

### RF-022 Autenticación con usuario y contraseña

El sistema debe permitir al usuario autenticarse con usuario y contraseña.

### RF-023 Autenticación con Google

El sistema debe permitir al usuario autenticarse mediante su cuenta de Google.

### RF-024 Habilitar reintento de guardado

El sistema debe permitir al usuario reintentar el guardado del mural utilizando la fotografía y la ubicación ya ingresadas, sin necesidad de volver a cargarlas.

### RF-025 Aprobar mural pendiente

El sistema debe permitir a un usuario administrador cambiar el estado de un mural de "pendiente" a "publicado" mediante un endpoint directo.

### RF-026 Requerir autenticación para crear mural

El sistema debe requerir que el usuario esté autenticado para acceder a la funcionalidad de creación de murales.

---

## Requerimientos No Funcionales

### RNF-001 Tiempo de carga

La lista de murales cercanos debe mostrarse en menos de 3 segundos para el 95% de las consultas.

### RNF-002 Disponibilidad

La aplicación debe mantener una disponibilidad mensual mínima del 99%.

### RNF-003 Tamaño máximo de imagen

La aplicación debe aceptar imágenes de hasta 10 MB.

### RNF-004 Precisión geográfica

La ubicación registrada debe tener una precisión igual o mejor a 50 metros cuando se utilice GPS.

### RNF-005 Internacionalización

La aplicación debe soportar los idiomas español, inglés y portugués, pero por defecto se usa español.

---

## Criterios de Aceptación

### AC-01 (RF-001): Subida exitosa

**Dado** que el usuario se encuentra en la pantalla de creación de mural / **Cuando** selecciona una fotografía válida / **Entonces** el sistema debe permitir continuar con el registro

---

### AC-02 (RF-002): Uso de GPS

**Dado** que el usuario otorgó permisos de ubicación / **Cuando** crea un mural / **Entonces** el sistema debe asociar la ubicación actual al registro

---

### AC-03 (RF-003): Ingreso manual exitoso

**Dado** que el usuario se encuentra registrando un mural / **Cuando** ingresa manualmente una dirección o coordenadas válidas / **Entonces** el sistema debe asociar esa ubicación al mural

---

### AC-04 (RF-004): Registro exitoso

**Dado** que existe una fotografía válida y una ubicación válida / **Cuando** el usuario presiona "Guardar" / **Entonces** el mural debe almacenarse en la base de datos para quedar disponible en búsquedas posteriores

---

### AC-05 (RF-005): Búsqueda dentro de radio

**Dado** que existen murales registrados y el usuario comparte su ubicación / **Cuando** solicita murales cercanos sin modificar el radio de búsqueda / **Entonces** el sistema debe mostrar únicamente murales ubicados dentro de los 5 kilómetros configurados por defecto

---

### AC-06 (RF-006): Visualización de marcadores

**Dado** que existen murales publicados dentro del área visible del mapa / **Cuando** el usuario abre la vista de mapa / **Entonces** el sistema debe mostrar un marcador por cada mural en su ubicación correspondiente

---

### AC-07 (RF-007): Consulta de detalle

**Dado** que existe un mural publicado / **Cuando** el usuario lo selecciona desde la lista o el mapa / **Entonces** el sistema debe mostrar su fotografía, fecha de creación y ubicación

---

### AC-08 (RF-008): Resultados ordenados

**Dado** que existen múltiples murales cercanos / **Cuando** se muestran los resultados / **Entonces** los murales deben aparecer ordenados de menor a mayor distancia

---

### AC-09 (RF-009): Detección de denegación de permisos

**Dado** que el usuario está creando un mural / **Cuando** rechaza el permiso de geolocalización / **Entonces** el sistema debe detectar la denegación pero no interrumpir el flujo de registro

---

### AC-10 (RF-010): Rechazo de imagen inválida

**Dado** que el usuario intenta subir una imagen / **Cuando** el archivo supera los 10 MB o tiene un formato no soportado / **Entonces** el sistema debe rechazar la imagen

---

### AC-11 (RF-011): Detección de fallo en el guardado

**Dado** que el servicio de almacenamiento no está disponible / **Cuando** el usuario intenta guardar un mural con fotografía y ubicación válidas / **Entonces** el sistema debe detectar el error y no registrar el mural como guardado exitosamente

---

### AC-12 (RF-012): Sin resultados cercanos

**Dado** que el usuario solicita murales cercanos / **Cuando** no existen murales dentro del radio configurado / **Entonces** el sistema debe mostrar un mensaje informando que no se encontraron resultados

---

### AC-13 (RF-013): Estado pendiente

**Dado** que un usuario guarda un nuevo mural / **Cuando** el registro se completa exitosamente / **Entonces** el mural debe quedar en estado "pendiente" y no debe aparecer en el mapa ni en las búsquedas públicas hasta ser validado

---

### AC-14 (RF-014): Reporte exitoso

**Dado** que existe un mural publicado / **Cuando** un usuario lo reporta por contenido inapropiado, duplicado o ubicación incorrecta / **Entonces** el sistema debe registrar el reporte y notificar que el mural será revisado

---

### AC-15 (RF-015): Imagen bloqueada por contenido NSFW

**Dado** que un usuario sube una fotografía / **Cuando** la validación automática detecta contenido NSFW / **Entonces** el sistema debe bloquear la publicación de la imagen y notificar al usuario que el contenido fue rechazado

---

### AC-16 (RF-016): Alternativa manual al denegar permisos

**Dado** que el sistema detectó la denegación de permisos de geolocalización / **Cuando** el usuario continúa con el registro del mural / **Entonces** el sistema debe presentar el campo de ingreso manual de ubicación como alternativa

---

### AC-17 (RF-017): Mensaje de motivo de rechazo

**Dado** que el usuario intentó subir una imagen inválida / **Cuando** el sistema rechaza la imagen / **Entonces** el sistema debe mostrar un mensaje indicando si el motivo fue el tamaño (supera los 10 MB) o el formato no soportado

---

### AC-18 (RF-018): Bloqueo con imagen inválida

**Dado** que el usuario adjuntó una imagen que fue rechazada / **Cuando** intenta avanzar en el registro del mural / **Entonces** el sistema debe impedir continuar hasta que se cargue una imagen válida

---

### AC-19 (RF-019): Notificación de error de guardado

**Dado** que ocurrió un error durante el proceso de guardado del mural / **Cuando** el sistema detecta el fallo / **Entonces** el sistema debe mostrar un mensaje de error visible al usuario

---

### AC-20 (RF-020): Preservación de datos tras error de guardado

**Dado** que el usuario completó fotografía y ubicación válidas / **Cuando** ocurre un error al guardar el mural / **Entonces** el sistema debe mantener la fotografía y la ubicación ingresadas disponibles

---

### AC-21 (RF-021): Sugerencia de ampliar radio

**Dado** que el sistema informó que no existen murales dentro del radio configurado / **Cuando** el usuario visualiza el mensaje de ausencia de resultados / **Entonces** el sistema debe ofrecer la opción de ampliar el radio de búsqueda

---

### AC-22 (RF-022): Login con usuario y contraseña

**Dado** que el usuario tiene una cuenta registrada / **Cuando** ingresa su usuario y contraseña correctos / **Entonces** el sistema debe autenticarlo y permitirle acceder a las funcionalidades de la aplicación

---

### AC-23 (RF-023): Login con Google

**Dado** que el usuario tiene una cuenta de Google / **Cuando** selecciona la opción de iniciar sesión con Google y otorga los permisos requeridos / **Entonces** el sistema debe autenticarlo mediante OAuth 2.0 y permitirle acceder a la aplicación

---

### AC-24 (RF-013): Control de acceso a aprobación de murales

**Dado** que existe un mural en estado "pendiente" / **Cuando** un usuario sin rol de administrador intenta cambiar su estado a "publicado" / **Entonces** el sistema debe rechazar la acción y mantener el mural en estado "pendiente"

---

### AC-25 (RF-024): Reintento sin recargar datos

**Dado** que ocurrió un error de guardado y el usuario retiene fotografía y ubicación válidas / **Cuando** vuelve a presionar "Guardar" / **Entonces** el sistema debe intentar el guardado sin solicitar nuevamente la fotografía ni la ubicación

---

### AC-26 (RF-025): Aprobación de mural por administrador

**Dado** que existe un mural en estado "pendiente" / **Cuando** un usuario administrador lo aprueba mediante un endpoint directo / **Entonces** el sistema debe cambiar su estado a "publicado"

---

### AC-27 (RF-026): Creación bloqueada para usuario no autenticado

**Dado** que el usuario no ha iniciado sesión / **Cuando** intenta acceder a la funcionalidad de creación de mural / **Entonces** el sistema debe redirigirlo al flujo de autenticación

---

## Fuera de Alcance

* Comentarios.
* Likes.
* Moderación humana con equipo dedicado / paneles de moderación avanzados.
* Panel de administración para gestión centralizada de contenido.
* Perfiles sociales.
* Seguimiento de usuarios.
* Gamificación.
* Posibilidad de que el usuario cambie el idioma de la interfaz

## Riesgos y Dependencias

### Fotografías de baja calidad

**Riesgo:** imágenes borrosas, oscuras o poco representativas del mural, que reducen el valor de la plataforma.

**Mitigación:**
* Validación técnica básica al subir la imagen (resolución mínima, nitidez aproximada).
* Feedback inmediato al usuario si la imagen no cumple criterios mínimos, con opción de volver a tomarla o seleccionarla.
* Mostrar recomendaciones (buena luz, encuadre) antes de la captura.

### Ubicaciones incorrectas

**Riesgo:** murales geolocalizados de forma errónea, dificultando su descubrimiento o generando confusión.

**Mitigación:**
* Uso de GPS como opción por defecto (mayor precisión) según RNF-004, con ingreso manual como alternativa (RF-003 / RF-009).
* Confirmación visual en un mapa antes de guardar, para que el usuario valide el pin.
* Posibilidad de reportar ubicación incorrecta como parte del flujo de reportes (RF-014).

### Contenido inapropiado cargado por usuarios

**Riesgo:** imágenes NSFW, ofensivas o que no correspondan a murales/arte urbano.

**Mitigación:**
* Validación automática básica de contenido NSFW antes de publicar (RF-015).
* Estado "pendiente" para todo contenido nuevo hasta su validación (RF-013).
* Sistema de reportes de usuarios para contenido ya publicado (RF-014).
* Definición de criterios claros de contenido aceptable, comunicados al usuario al momento de subir una foto.
