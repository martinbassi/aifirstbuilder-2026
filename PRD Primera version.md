# PRD - Murales Urbanos

## 1. Resumen

### Problema

Las frases, grafitis artísticos y murales urbanos suelen ser efímeros. Muchas personas encuentran obras interesantes en la calle, pero no existe una forma simple de documentarlas y descubrir otras cercanas creadas o registradas por la comunidad.

### Solución

Una aplicación móvil donde los usuarios pueden:

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

## No incluido

* Comentarios.
* Likes.
* Moderación avanzada.
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

## RNF-005 Compatibilidad

La aplicación debe funcionar en dispositivos Android 12+ e iOS 16+.

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

# 7. Criterios de Aceptación (Gherkin)

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

## RF-008 Ordenar por cercanía

Feature: Ordenar por distancia

Scenario: Resultados ordenados

Given que existen múltiples murales cercanos

When se muestran los resultados

## Then los murales deben aparecer ordenados de menor a mayor distancia

# 8. Métricas de Éxito

* Al menos 20 murales cargados durante la demostración.
* Tiempo promedio de registro menor a 30 segundos.
* Al menos 80% de las búsquedas muestran resultados en menos de 3 segundos.

---

# 9. Riesgos

* Fotografías de baja calidad.
* Ubicaciones incorrectas.
* Contenido inapropiado cargado por usuarios.

---

# 10. Futuras Versiones

* Comentarios.
* Favoritos.
* Moderación comunitaria.
* Reconocimiento automático de texto mediante IA.
* Búsqueda por palabras contenidas en los murales.
* Ranking de murales populares.
