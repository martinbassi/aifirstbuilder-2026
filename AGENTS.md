# AGENTS.md

## Propósito
PWA para documentar y descubrir murales urbanos geolocalizados.
Los usuarios suben fotos con ubicación; otros las exploran en un mapa o listado.

## Stack
- Frontend: Angular 21 · npm · ng-zorro (less) · responsive
- Backend: .NET Core 10 · CQRS · FluentValidation · MediatR 12.5.0 · Mapster · EFcore
- Base de datos: SQL Server 2025 localhost
- Almacenamiento de imágenes: Azure Storage (azurite)
- Mapas: Leaflet
- Validación NSFW: NsfwSpy.NET y Azure AI Foundry

## Convenciones de código
- Todo el código (nombres de variables, clases, métodos, etc.) y los endpoints de la API deben escribirse en inglés, independientemente del idioma de la documentación (PRD, AGENTS.md).
- La aplicación debe soportar i18n en español, inglés y portugués.

## Cómo correr
```bash
# Instalar
dotnet restore && npm install

# Desarrollo
dotnet watch run      # backend
npm start             # frontend

# Tests
dotnet test           # .NET
npm test              # Angular / Vitest
```
Requerido: definir `ANTHROPIC_API_KEY` (y demás API keys) en `.env` antes de iniciar.

## Qué NO hacer
- No exponer murales `pendiente` en búsquedas ni en el mapa (RF-013).
- No omitir validación NSFW antes de publicar (RF-015).
- No aceptar imágenes > 10 MB en ningún endpoint (RNF-003).
- No agregar features fuera del PRD; comentarios, likes y perfiles quedan excluidos del MVP.
