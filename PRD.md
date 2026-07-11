# PRD - Murales Urbanos

## 1. Resumen

### Problema

Las frases, grafitis artísticos y murales urbanos suelen ser efímeros. Muchas personas encuentran obras interesantes en la calle, pero no existe una forma simple de documentarlas y descubrir otras cercanas creadas o registradas por la comunidad.

### Solución

Una aplicación web (PWA) donde los usuarios pueden:

* Subir una fotografía de un mural o frase urbana.
* Registrar la ubicación donde fue encontrada.
* Explorar murales cercanos cargados por otros usuarios.
* Visualizar los murales en un mapa.

### Objetivo del MVP

Permitir que una persona capture un mural y que otra persona pueda descubrirlo cerca de su ubicación.

---

# 2. Usuarios

## Usuario Explorador

Persona interesada en arte urbano, fotografía o turismo local.

## Usuario Colaborador

Persona que desea registrar y compartir murales encontrados en la ciudad.

---

# 3. Alcance del MVP

## Incluido

* Registro de murales.
* Foto.
* Geolocalización.
* Mapa de murales cercanos.
* Lista de murales cercanos.
* Visualización de detalle.
* Manejo de casos límite: permisos de ubicación denegados, imágenes inválidas, fallos de guardado y ausencia de resultados cercanos.
* **Moderación mínima de contenido:**
  * Estado "pendiente" para murales recién subidos, no visibles públicamente hasta ser aprobados o validados.
  * Reporte de murales por parte de los usuarios.
  * Validación automática básica para bloquear contenido NSFW antes de su publicación.

## No incluido

* Comentarios.
* Likes.
* Moderación humana con equipo dedicado / paneles de moderación avanzados.
* Perfiles sociales.
* Seguimiento de usuarios.
* Gamificación.

---

# 4. Requisitos Funcionales (RF)

## RF-001 Crear mural

El sistema debe permitir subir una fotografía de un mural.

## RF-002 Registrar ubicación automática

El sistema debe permitir asociar la ubicación GPS actual al mural.

## RF-003 Registrar ubicación manual

El sistema debe permitir ingresar una ubicación manualmente.

## RF-004 Guardar mural

El sistema debe almacenar fotografía, ubicación y fecha de creación.

## RF-005 Buscar murales cercanos

El sistema debe mostrar murales ubicados dentro de un radio configurable alrededor del usuario.

## RF-006 Mostrar mapa

El sistema debe mostrar marcadores de murales sobre un mapa.

## RF-007 Ver detalle de mural

El sistema debe mostrar la fotografía, fecha y ubicación de un mural seleccionado.

## RF-008 Ordenar por cercanía

El sistema debe ordenar los resultados por distancia al usuario.

## RF-009 Manejo de permisos de ubicación denegados

El sistema debe detectar cuándo el usuario no otorga permisos de geolocalización y ofrecer una alternativa (ingreso manual de ubicación) sin bloquear el flujo.

## RF-010 Manejo de imagen inválida

El sistema debe validar el formato y tamaño del archivo subido y notificar al usuario cuando la imagen no cumple los requisitos, sin permitir continuar el registro hasta corregirla.

## RF-011 Manejo de fallo en el guardado

El sistema debe detectar errores durante el proceso de guardado (fotografía, ubicación o metadatos) y notificar al usuario, permitiéndole reintentar sin perder los datos ya ingresados.

## RF-012 Manejo de búsqueda sin resultados cercanos

El sistema debe informar al usuario cuando no existan murales dentro del radio configurado y sugerir alternativas (ampliar el radio de búsqueda).

## RF-013 Estado "pendiente" de publicación

El sistema debe marcar todo mural recién creado como "pendiente" y ocultarlo de las búsquedas y el mapa públicos hasta que sea validado.

## RF-014 Reportar mural

El sistema debe permitir a cualquier usuario reportar un mural publicado por contenido inapropiado, duplicado o ubicación incorrecta

## RF-015 Validación automática básica de contenido NSFW

El sistema debe ejecutar una validación automática sobre cada imagen subida y bloquear su publicación si se detecta contenido NSFW.

---

# 5. Requisitos No Funcionales (RNF)

## RNF-001 Tiempo de carga

La lista de murales cercanos debe mostrarse en menos de 3 segundos para el 95% de las consultas.

## RNF-002 Disponibilidad

La aplicación debe mantener una disponibilidad mensual mínima del 99%.

## RNF-003 Tamaño máximo de imagen

La aplicación debe aceptar imágenes de hasta 10 MB.

## RNF-004 Precisión geográfica

La ubicación registrada debe tener una precisión igual o mejor a 50 metros cuando se utilice GPS.

---

# 6. Historias de Usuario

## HU-001

Como explorador

Quiero ver murales cercanos

Para descubrir arte urbano en mi zona.

## HU-002

Como colaborador

Quiero subir una fotografía de un mural

Para compartirlo con la comunidad.

## HU-003

Como explorador

Quiero visualizar murales en un mapa

Para encontrarlos fácilmente.

---

# 7. Criterios de Aceptación

## RF-001 Crear mural

Feature: Crear mural

Scenario: Subida exitosa

Given que el usuario se encuentra en la pantalla de creación de mural

When selecciona una fotografía válida

Then el sistema debe permitir continuar con el registro

---

## RF-002 Registrar ubicación automática

Feature: Registrar ubicación automática

Scenario: Uso de GPS

Given que el usuario otorgó permisos de ubicación

When crea un mural

Then el sistema debe asociar la ubicación actual al registro

---

## RF-003 Registrar ubicación manual

Feature: Registrar ubicación manual

Scenario: Ingreso manual exitoso

Given que el usuario se encuentra registrando un mural

When ingresa manualmente una dirección o coordenadas válidas

Then el sistema debe asociar esa ubicación al mural

---

## RF-004 Guardar mural

Feature: Guardar mural

Scenario: Registro exitoso

Given que existe una fotografía válida

And existe una ubicación válida

When el usuario presiona "Guardar"

Then el mural debe almacenarse en la base de datos

And debe quedar disponible para búsquedas posteriores

---

## RF-005 Buscar murales cercanos

Feature: Buscar murales cercanos

Scenario: Búsqueda dentro de radio

Given que existen murales registrados

And el usuario comparte su ubicación

When solicita murales cercanos

Then el sistema debe mostrar únicamente murales ubicados dentro de 5 kilómetros

---

## RF-006 Mostrar mapa

Feature: Mostrar mapa

Scenario: Visualización de marcadores

Given que existen murales publicados dentro del área visible del mapa

When el usuario abre la vista de mapa

Then el sistema debe mostrar un marcador por cada mural en su ubicación correspondiente

---

## RF-007 Ver detalle de mural

Feature: Ver detalle de mural

Scenario: Consulta de detalle

Given que existe un mural publicado

When el usuario lo selecciona desde la lista o el mapa

Then el sistema debe mostrar su fotografía, fecha de creación y ubicación

---

## RF-008 Ordenar por cercanía

Feature: Ordenar por distancia

Scenario: Resultados ordenados

Given que existen múltiples murales cercanos

When se muestran los resultados

Then los murales deben aparecer ordenados de menor a mayor distancia

---

## RF-009 Manejo de permisos de ubicación denegados

Feature: Permisos de ubicación denegados

Scenario: Usuario rechaza el permiso de GPS

Given que el usuario está creando un mural

When rechaza el permiso de geolocalización

Then el sistema debe ofrecer la opción de ingresar la ubicación manualmente

And no debe bloquear la continuación del registro

---

## RF-010 Manejo de imagen inválida

Feature: Imagen inválida

Scenario: Archivo no cumple los requisitos

Given que el usuario intenta subir una imagen

When el archivo supera el tamaño máximo permitido o tiene un formato no soportado

Then el sistema debe rechazar la imagen

And debe mostrar un mensaje indicando el motivo

---

## RF-011 Manejo de fallo en el guardado

Feature: Fallo en el guardado

Scenario: Error durante el almacenamiento

Given que el usuario completó fotografía y ubicación válidas

When ocurre un error al guardar el mural

Then el sistema debe notificar el error al usuario

And debe permitir reintentar sin perder los datos ya ingresados

---

## RF-012 Manejo de búsqueda sin resultados cercanos

Feature: Sin murales cercanos

Scenario: No hay resultados dentro del radio

Given que el usuario solicita murales cercanos

When no existen murales dentro del radio configurado

Then el sistema debe informar que no se encontraron resultados

And debe sugerir ampliar el radio de búsqueda

---

## RF-013 Estado "pendiente" de publicación

Feature: Estado pendiente

Scenario: Mural recién creado

Given que un usuario guarda un nuevo mural

When el registro se completa exitosamente

Then el mural debe quedar en estado "pendiente"

And no debe aparecer en el mapa ni en las búsquedas públicas hasta ser validado

---

## RF-014 Reportar mural

Feature: Reportar mural

Scenario: Reporte exitoso

Given que existe un mural publicado

When un usuario lo reporta por contenido inapropiado, duplicado o ubicación incorrecta

Then el sistema debe registrar el reporte

And debe notificar que el mural será revisado

---

## RF-015 Validación automática básica de contenido NSFW

Feature: Validación automática de contenido

Scenario: Imagen bloqueada por contenido NSFW

Given que un usuario sube una fotografía

When la validación automática detecta contenido NSFW

Then el sistema debe bloquear la publicación de la imagen

And debe notificar al usuario que el contenido fue rechazado

---

# 8. Métricas de Éxito

* Al menos 20 murales cargados durante la demostración.
* Tiempo promedio de registro menor a 30 segundos.
* Al menos 80% de las búsquedas muestran resultados en menos de 3 segundos.

---

# 9. Riesgos y Mitigaciones

## Fotografías de baja calidad

**Riesgo:** imágenes borrosas, oscuras o poco representativas del mural, que reducen el valor de la plataforma.

**Mitigación:**
* Validación técnica básica al subir la imagen (resolución mínima, nitidez aproximada).
* Feedback inmediato al usuario si la imagen no cumple criterios mínimos, con opción de volver a tomarla o seleccionarla.
* Mostrar recomendaciones (buena luz, encuadre) antes de la captura.

## Ubicaciones incorrectas

**Riesgo:** murales geolocalizados de forma errónea, dificultando su descubrimiento o generando confusión.

**Mitigación:**
* Uso de GPS como opción por defecto (mayor precisión) según RNF-004, con ingreso manual como alternativa (RF-003 / RF-009).
* Confirmación visual en un mapa antes de guardar, para que el usuario valide el pin.
* Posibilidad de reportar ubicación incorrecta como parte del flujo de reportes (RF-014).

## Contenido inapropiado cargado por usuarios

**Riesgo:** imágenes NSFW, ofensivas o que no correspondan a murales/arte urbano.

**Mitigación:**
* Validación automática básica de contenido NSFW antes de publicar (RF-015).
* Estado "pendiente" para todo contenido nuevo hasta su validación (RF-013).
* Sistema de reportes de usuarios para contenido ya publicado (RF-014).
* Definición de criterios claros de contenido aceptable, comunicados al usuario al momento de subir una foto.

---

# 10. Futuras Versiones

* Comentarios.
* Favoritos.
* Moderación comunitaria avanzada (paneles, roles de moderador).
* Reconocimiento automático de texto mediante IA.
* Búsqueda por palabras contenidas en los murales.
* Ranking de murales populares.