# Diagrama UML en Mermaid

Este archivo contiene el diagrama UML en formato Mermaid, que se renderiza automáticamente en GitHub.

## Diagrama de Clases

```mermaid
classDiagram
    %% Entidades Principales
    
    class Usuario {
        -Long id
        -String nombreUsuario
        -String email
        -String password
        -DateTime fechaRegistro
        -Boolean activo
        +registrar() Boolean
        +iniciarSesion() Boolean
        +cerrarSesion() void
        +actualizarPerfil() Boolean
        +eliminarCuenta() void
    }
    
    class Artista {
        -Long id
        -String nombre
        -String apellidos
        -String biografia
        -String especialidad
        -String sitioWeb
        -String telefono
        +crearPerfil() Boolean
        +editarPerfil() Boolean
        +visualizarPerfilPublico() PerfilPublico
    }
    
    class PerfilPublico {
        -Long id
        -String titulo
        -String descripcion
        -List~String~ habilidades
        -DateTime fechaCreacion
        -Integer visitas
        +mostrarGaleria() List~Imagen~
        +actualizarInformacion() Boolean
        +obtenerEstadisticas() Map
    }
    
    class Imagen {
        -Long id
        -String titulo
        -String descripcion
        -String url
        -DateTime fechaSubida
        -String dimensiones
        -String formato
        +subir() Boolean
        +eliminar() Boolean
        +actualizar() Boolean
        +obtenerMetadata() Map
    }
    
    class MensajePrivado {
        -Long id
        -String asunto
        -String contenido
        -DateTime fechaEnvio
        -Boolean leido
        +enviar() Boolean
        +marcarComoLeido() void
        +responder() Boolean
        +eliminar() void
    }
    
    class Conversacion {
        -Long id
        -DateTime fechaInicio
        -DateTime ultimaActividad
        -Boolean activa
        +iniciarConversacion() Boolean
        +obtenerMensajes() List~MensajePrivado~
        +cerrarConversacion() void
    }
    
    class Ubicacion {
        -Long id
        -String direccion
        -String ciudad
        -String pais
        -Double latitud
        -Double longitud
        -Boolean visible
        +actualizar() Boolean
        +ocultarUbicacion() void
        +mostrarUbicacion() void
    }
    
    class Mapa {
        -Long id
        -Integer zoom
        -Coordenadas centro
        +buscarArtistas(ubicacion, radio) List~Artista~
        +mostrarArtistasEnMapa() void
        +filtrarPorEspecialidad(especialidad) List~Artista~
    }
    
    class TablonanAnuncios {
        -Long id
        -String nombre
        -String descripcion
        -DateTime fechaCreacion
        +publicarProyecto(proyecto) Boolean
        +buscarProyectos(filtros) List~Proyecto~
        +obtenerProyectosRecientes() List~Proyecto~
    }
    
    class Proyecto {
        -Long id
        -String titulo
        -String descripcion
        -String requisitos
        -Double presupuesto
        -Date fechaInicio
        -Date fechaFin
        -EstadoProyecto estado
        -Integer numeroPlazas
        -Integer plazasDisponibles
        +publicar() Boolean
        +actualizar() Boolean
        +cerrar() void
        +reabrirConvocatoria() Boolean
    }
    
    class Solicitud {
        -Long id
        -DateTime fechaSolicitud
        -String mensaje
        -EstadoSolicitud estado
        -String portfolio
        +enviar() Boolean
        +retirar() void
        +actualizarEstado(estado) void
    }
    
    class Notificacion {
        -Long id
        -TipoNotificacion tipo
        -String mensaje
        -DateTime fechaCreacion
        -Boolean leida
        +enviar() Boolean
        +marcarComoLeida() void
    }
    
    %% Enumeraciones
    
    class EstadoProyecto {
        <<enumeration>>
        BORRADOR
        PUBLICADO
        EN_PROCESO
        CERRADO
        COMPLETADO
        CANCELADO
    }
    
    class EstadoSolicitud {
        <<enumeration>>
        PENDIENTE
        REVISADA
        ACEPTADA
        RECHAZADA
        RETIRADA
    }
    
    class TipoNotificacion {
        <<enumeration>>
        MENSAJE_NUEVO
        SOLICITUD_RECIBIDA
        SOLICITUD_ACEPTADA
        SOLICITUD_RECHAZADA
        NUEVO_PROYECTO
        PROYECTO_ACTUALIZADO
    }
    
    %% Relaciones
    
    Usuario "1" -- "1" Artista : representa
    Artista "1" -- "1" PerfilPublico : tiene
    PerfilPublico "1" -- "0..*" Imagen : contiene
    
    Artista "1" -- "0..*" Conversacion : participa en
    Conversacion "1" *-- "1..*" MensajePrivado : contiene
    MensajePrivado "1" -- "1" Artista : enviado por
    
    Artista "1" -- "0..1" Ubicacion : tiene
    Mapa "1" -- "0..*" Ubicacion : muestra
    
    TablonanAnuncios "1" -- "0..*" Proyecto : contiene
    Proyecto "1" -- "1" Artista : creado por
    Proyecto "1" -- "0..*" Solicitud : recibe
    Solicitud "1" -- "1" Artista : enviada por
    Proyecto "1" -- "0..*" Artista : selecciona
    
    Artista "1" -- "0..*" Notificacion : recibe
    Notificacion "1" -- "0..1" Proyecto : relacionada con
    Notificacion "1" -- "0..1" Solicitud : relacionada con
    Notificacion "1" -- "0..1" MensajePrivado : relacionada con
    
    Proyecto "1" -- "1" EstadoProyecto : tiene estado
    Solicitud "1" -- "1" EstadoSolicitud : tiene estado
    Notificacion "1" -- "1" TipoNotificacion : tiene tipo
```

## Descripción de Componentes

### Módulo de Usuario y Autenticación
- **Usuario**: Gestiona credenciales y autenticación
- **Artista**: Perfil profesional del artista

### Módulo de Perfil Público
- **PerfilPublico**: Información visible del artista
- **Imagen**: Galería de trabajos artísticos

### Módulo de Mensajería
- **Conversacion**: Hilo de mensajes entre artistas
- **MensajePrivado**: Mensajes individuales

### Módulo de Geolocalización
- **Ubicacion**: Localización del artista
- **Mapa**: Visualización de artistas en el mapa

### Módulo de Proyectos
- **TablonanAnuncios**: Gestión del tablón
- **Proyecto**: Anuncio de proyecto colaborativo
- **Solicitud**: Aplicación a un proyecto

### Módulo de Notificaciones
- **Notificacion**: Sistema de alertas

## Flujos Principales

### 1. Registro y Creación de Perfil
```
Usuario → registrar()
Usuario → Artista
Artista → crearPerfil()
Artista → PerfilPublico
PerfilPublico → Imagen (subir trabajos)
```

### 2. Búsqueda de Artistas
```
Usuario → Mapa
Mapa → buscarArtistas()
Mapa → mostrarArtistasEnMapa()
Usuario → selecciona Artista
Usuario → visualiza PerfilPublico
```

### 3. Contacto con Artista
```
Artista → iniciarConversacion(otroArtista)
Conversacion → MensajePrivado (enviar)
Sistema → Notificacion (MENSAJE_NUEVO)
```

### 4. Publicación de Proyecto
```
Artista → TablonanAnuncios
TablonanAnuncios → publicarProyecto()
Proyecto → cambiar estado a PUBLICADO
Sistema → Notificacion (NUEVO_PROYECTO)
```

### 5. Aplicación a Proyecto
```
Artista → Proyecto (ver)
Artista → Solicitud (enviar)
Sistema → Notificacion (SOLICITUD_RECIBIDA)
Creador → revisar Solicitud
Creador → actualizarEstado(ACEPTADA/RECHAZADA)
Sistema → Notificacion (SOLICITUD_ACEPTADA/RECHAZADA)
```
