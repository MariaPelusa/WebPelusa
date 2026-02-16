# Diagrama UML - Aplicación de Colaboración para Artistas

## Descripción General

Este documento describe el diseño de una aplicación web para facilitar la colaboración entre artistas. La aplicación permite a los artistas registrarse, crear perfiles públicos, comunicarse entre sí, localizar otros artistas geográficamente, y colaborar en proyectos mediante un tablón de anuncios.

## Funcionalidades Principales

### 1. Registro y Gestión de Usuarios

**Entidades Involucradas:**
- `Usuario`: Maneja la autenticación y acceso al sistema
- `Artista`: Información específica del perfil profesional

**Características:**
- Registro de nuevos usuarios artistas
- Inicio y cierre de sesión
- Gestión de credenciales
- Actualización de datos personales

### 2. Perfil Público

**Entidades Involucradas:**
- `PerfilPublico`: Información visible públicamente
- `Imagen`: Galería de trabajos del artista

**Características:**
- Creación y edición de perfil público
- Galería de imágenes con portfolio de trabajos
- Información sobre habilidades y especialidades
- Estadísticas de visitas al perfil
- Subida, actualización y eliminación de imágenes

### 3. Mensajería Privada

**Entidades Involucradas:**
- `Conversacion`: Agrupa mensajes entre artistas
- `MensajePrivado`: Mensaje individual

**Características:**
- Iniciar conversaciones con otros artistas
- Enviar y recibir mensajes privados
- Historial de conversaciones
- Notificaciones de mensajes nuevos
- Marcar mensajes como leídos

### 4. Localización de Artistas

**Entidades Involucradas:**
- `Ubicacion`: Localización geográfica del artista
- `Mapa`: Sistema de visualización de ubicaciones

**Características:**
- Registro de ubicación del artista
- Visualización en mapa de artistas cercanos
- Búsqueda por radio de distancia
- Filtrado por especialidad
- Control de privacidad de ubicación (mostrar/ocultar)

### 5. Tablón de Anuncios

**Entidades Involucradas:**
- `TablonanAnuncios`: Gestiona la publicación de proyectos
- `Proyecto`: Anuncio de proyecto colaborativo
- `Solicitud`: Aplicación de un artista a un proyecto

**Características:**
- Publicación de proyectos que requieren colaboración
- Descripción de requisitos y plazas disponibles
- Sistema de estados del proyecto (borrador, publicado, en proceso, etc.)
- Envío de solicitudes por parte de artistas interesados
- Gestión de solicitudes (aceptar, rechazar, revisar)
- Seguimiento del estado de las solicitudes

### 6. Sistema de Notificaciones

**Entidades Involucradas:**
- `Notificacion`: Alertas para el usuario

**Características:**
- Notificaciones de mensajes nuevos
- Alertas sobre solicitudes recibidas o actualizadas
- Notificaciones de nuevos proyectos relevantes
- Historial de notificaciones

## Diagrama de Clases

El diagrama completo en formato PlantUML está disponible en:
`docs/uml/artist-collaboration-app.puml`

Para visualizar el diagrama, puedes usar:
- [PlantUML Online Editor](https://www.plantuml.com/plantuml/uml/)
- Extensiones de PlantUML para VS Code, IntelliJ, etc.
- Generar imagen con PlantUML CLI

### Comando para generar imagen (si tienes PlantUML instalado):

```bash
plantuml docs/uml/artist-collaboration-app.puml
```

## Entidades Principales

### Usuario
Clase base que maneja la autenticación y gestión de cuentas. Cada usuario tiene credenciales únicas y puede ser asociado a un perfil de artista.

### Artista
Representa el perfil profesional del usuario. Contiene información como nombre, biografía, especialidad, y datos de contacto.

### PerfilPublico
Perfil visible públicamente que otros artistas pueden visualizar. Incluye una galería de imágenes y estadísticas de visitas.

### Imagen
Representa cada trabajo artístico subido a la galería. Incluye metadatos como título, descripción, dimensiones y formato.

### MensajePrivado y Conversacion
Sistema de mensajería que permite la comunicación directa entre artistas. Las conversaciones agrupan múltiples mensajes entre los mismos participantes.

### Ubicacion y Mapa
Sistema de geolocalización que permite a los artistas ser encontrados geográficamente. Los artistas pueden controlar la visibilidad de su ubicación.

### TablonanAnuncios y Proyecto
Sistema para publicar y gestionar proyectos colaborativos. Los artistas pueden publicar proyectos y otros pueden aplicar mediante solicitudes.

### Solicitud
Representa la aplicación de un artista a un proyecto específico. Incluye un mensaje de presentación y pasa por diferentes estados (pendiente, aceptada, rechazada).

### Notificacion
Sistema de alertas para mantener a los artistas informados sobre eventos relevantes (mensajes nuevos, solicitudes, proyectos).

## Relaciones entre Entidades

### Relaciones 1:1
- Usuario ↔ Artista: Cada usuario es un artista
- Artista ↔ PerfilPublico: Cada artista tiene un perfil público
- Artista ↔ Ubicacion: Cada artista puede tener una ubicación

### Relaciones 1:N
- PerfilPublico → Imagenes: Un perfil contiene múltiples imágenes
- Conversacion → MensajePrivados: Una conversación contiene múltiples mensajes
- TablonanAnuncios → Proyectos: El tablón contiene múltiples proyectos
- Proyecto → Solicitudes: Un proyecto recibe múltiples solicitudes
- Artista → Notificaciones: Un artista recibe múltiples notificaciones

### Relaciones N:M
- Artista ↔ Conversacion: Varios artistas participan en múltiples conversaciones
- Proyecto ↔ Artista (seleccionados): Un proyecto puede tener múltiples artistas seleccionados

## Enumeraciones

### EstadoProyecto
- **BORRADOR**: Proyecto en creación, no visible públicamente
- **PUBLICADO**: Proyecto visible y aceptando solicitudes
- **EN_PROCESO**: Proyecto con artistas seleccionados y en ejecución
- **CERRADO**: Proyecto que ya no acepta solicitudes
- **COMPLETADO**: Proyecto finalizado exitosamente
- **CANCELADO**: Proyecto cancelado antes de completarse

### EstadoSolicitud
- **PENDIENTE**: Solicitud enviada, esperando revisión
- **REVISADA**: Solicitud vista por el creador del proyecto
- **ACEPTADA**: Solicitud aceptada, artista seleccionado
- **RECHAZADA**: Solicitud rechazada
- **RETIRADA**: Solicitud retirada por el solicitante

### TipoNotificacion
- **MENSAJE_NUEVO**: Nueva notificación de mensaje privado
- **SOLICITUD_RECIBIDA**: Nueva solicitud recibida en un proyecto
- **SOLICITUD_ACEPTADA**: Tu solicitud fue aceptada
- **SOLICITUD_RECHAZADA**: Tu solicitud fue rechazada
- **NUEVO_PROYECTO**: Nuevo proyecto publicado relevante
- **PROYECTO_ACTUALIZADO**: Actualización en un proyecto de interés

## Extensibilidad

El diseño permite futuras extensiones como:

1. **Sistema de Valoraciones**: Añadir reviews y ratings entre artistas
2. **Categorías de Arte**: Clasificación más detallada de especialidades
3. **Sistema de Pago**: Integración de pagos para proyectos
4. **Chat en Tiempo Real**: Mensajería instantánea con WebSockets
5. **Calendario**: Sistema de disponibilidad para proyectos
6. **Portfolios Temáticos**: Múltiples portfolios por artista
7. **Grupos de Artistas**: Colectivos y asociaciones
8. **Eventos y Exposiciones**: Sistema para organizar eventos artísticos

## Consideraciones Técnicas

### Seguridad
- Autenticación robusta con encriptación de contraseñas
- Control de acceso basado en roles
- Validación de datos en cliente y servidor
- Protección contra inyección SQL y XSS
- Rate limiting en mensajería y solicitudes

### Privacidad
- Control de visibilidad de ubicación
- Configuración de privacidad del perfil
- Gestión de datos personales según GDPR
- Opción de eliminar cuenta con todos los datos

### Rendimiento
- Paginación en listados de proyectos y mensajes
- Caché de perfiles públicos
- Optimización de consultas de búsqueda en mapa
- Compresión y optimización de imágenes

### Escalabilidad
- Arquitectura modular para facilitar microservicios
- Base de datos relacional con índices optimizados
- Sistema de notificaciones asíncrono
- CDN para servir imágenes del portfolio

## Tecnologías Sugeridas

### Backend
- **Framework**: Spring Boot (Java), Django (Python), o Express.js (Node.js)
- **Base de Datos**: PostgreSQL con extensión PostGIS para geolocalización
- **Autenticación**: JWT o OAuth 2.0
- **API**: RESTful o GraphQL

### Frontend
- **Framework**: React, Vue.js, o Angular
- **Mapas**: Leaflet.js o Google Maps API
- **UI Components**: Material-UI, Ant Design, o Bootstrap

### Infraestructura
- **Almacenamiento de Imágenes**: AWS S3, Cloudinary, o similar
- **Notificaciones**: Firebase Cloud Messaging o servicio similar
- **Despliegue**: Docker + Kubernetes o servicios cloud (AWS, Azure, GCP)

## Conclusión

Este diseño proporciona una base sólida para desarrollar una aplicación completa de colaboración artística. El modelo de clases está diseñado para ser escalable, mantenible y seguro, cubriendo todas las funcionalidades solicitadas en los requisitos.
