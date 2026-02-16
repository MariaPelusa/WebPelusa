# Índice de Diagramas UML - Aplicación de Colaboración Artística

## 📋 Contenido

Este directorio contiene todos los diagramas UML para el diseño de la aplicación de colaboración entre artistas.

## 📊 Diagramas Disponibles

### 1. Diagrama de Clases Principal
**Archivo:** `artist-collaboration-app.puml`

El diagrama de clases completo que muestra todas las entidades del sistema, sus atributos, métodos y relaciones.

**Entidades principales:**
- Usuario y Artista
- PerfilPublico e Imagen
- Conversacion y MensajePrivado
- Ubicacion y Mapa
- TablonanAnuncios, Proyecto y Solicitud
- Notificacion

**Formato:** PlantUML

**Visualizar:**
- Copiar el contenido en [PlantUML Online](https://www.plantuml.com/plantuml/uml/)
- Usar extensión de PlantUML en VS Code
- Generar imagen: `plantuml artist-collaboration-app.puml`

---

### 2. Diagrama de Clases en Mermaid
**Archivo:** `diagram-mermaid.md`

El mismo diagrama de clases en formato Mermaid, que se renderiza automáticamente en GitHub.

**Ventajas:**
- Se visualiza directamente en GitHub
- Incluye descripciones de flujos principales
- Sintaxis más simple

**Ver:** Abre el archivo en GitHub para ver el diagrama renderizado

---

### 3. Diagrama de Casos de Uso
**Archivo:** `use-cases.puml`

Muestra todas las funcionalidades del sistema desde la perspectiva del usuario (artista).

**Casos de uso incluidos:**
- Gestión de Usuario (registro, login, perfil)
- Perfil Público (crear, editar, gestionar galería)
- Mensajería (conversaciones, mensajes)
- Geolocalización (búsqueda de artistas en mapa)
- Tablón de Proyectos (publicar, buscar, gestionar)
- Solicitudes (enviar, revisar, aceptar/rechazar)
- Notificaciones

**Actores:**
- Artista
- Sistema de Notificaciones
- Servicio de Mapas

**Formato:** PlantUML

---

### 4. Diagrama de Secuencia - Aplicación a Proyecto
**Archivo:** `sequence-apply-project.puml`

Muestra el flujo completo de un artista aplicando a un proyecto colaborativo.

**Flujo:**
1. Búsqueda de proyectos
2. Visualización de detalles
3. Envío de solicitud
4. Notificación al creador
5. Revisión de solicitud
6. Aceptación o rechazo
7. Notificación al solicitante

**Formato:** PlantUML

---

### 5. Diagrama de Secuencia - Mensajería
**Archivo:** `sequence-messaging.puml`

Muestra la interacción completa entre dos artistas comunicándose.

**Flujo:**
1. Búsqueda de artista (por mapa y especialidad)
2. Visualización de perfil público
3. Inicio de conversación
4. Envío de mensaje
5. Notificación
6. Lectura de mensaje
7. Respuesta

**Formato:** PlantUML

---

## 🛠️ Cómo Visualizar los Diagramas

### Opción 1: PlantUML Online (Más fácil)
1. Abre [PlantUML Online Editor](https://www.plantuml.com/plantuml/uml/)
2. Copia el contenido de cualquier archivo `.puml`
3. Pega en el editor
4. El diagrama se renderiza automáticamente

### Opción 2: VS Code
1. Instala la extensión "PlantUML"
2. Abre cualquier archivo `.puml`
3. Presiona `Alt+D` para ver la vista previa

### Opción 3: Generar Imágenes
Si tienes PlantUML instalado localmente:

```bash
# Instalar PlantUML (requiere Java)
brew install plantuml  # macOS
apt-get install plantuml  # Linux

# Generar todas las imágenes
plantuml docs/uml/*.puml

# Generar un diagrama específico
plantuml docs/uml/artist-collaboration-app.puml
```

### Opción 4: Mermaid en GitHub
El archivo `diagram-mermaid.md` se visualiza automáticamente al abrirlo en GitHub.

---

## 📚 Documentación Adicional

**Archivo:** `README.md`

Documentación completa que incluye:
- Descripción general del sistema
- Funcionalidades principales detalladas
- Descripción de cada entidad
- Relaciones entre entidades
- Enumeraciones y sus valores
- Consideraciones técnicas (seguridad, privacidad, rendimiento)
- Tecnologías sugeridas
- Extensibilidad futura

---

## 🎯 Resumen del Sistema

La aplicación de colaboración artística permite:

1. **Registro y Perfiles**: Artistas crean cuentas y perfiles públicos con galerías de imágenes
2. **Mensajería**: Comunicación privada entre artistas
3. **Geolocalización**: Búsqueda de artistas por ubicación y especialidad en mapa
4. **Proyectos Colaborativos**: Tablón donde publicar proyectos que requieren múltiples artistas
5. **Sistema de Solicitudes**: Artistas aplican a proyectos y reciben notificaciones
6. **Notificaciones**: Sistema de alertas para mantener informados a los usuarios

---

## 📝 Notas de Diseño

### Principios Aplicados
- **Modularidad**: Cada funcionalidad está claramente separada
- **Escalabilidad**: Diseño preparado para crecimiento
- **Seguridad**: Consideraciones de privacidad y control de acceso
- **Usabilidad**: Flujos intuitivos para el usuario

### Patrones de Diseño Utilizados
- **MVC**: Separación de modelo, vista y controlador
- **Repository Pattern**: Para acceso a datos
- **Observer Pattern**: Sistema de notificaciones
- **Strategy Pattern**: Filtros de búsqueda en mapa y proyectos

### Consideraciones de Implementación
- Base de datos relacional (PostgreSQL recomendado)
- API RESTful para comunicación frontend-backend
- Autenticación JWT
- Almacenamiento en cloud para imágenes
- WebSockets para mensajería en tiempo real (opcional)

---

## 🔄 Versionado

**Versión actual:** 1.0
**Fecha:** Febrero 2026
**Autor:** Documentación técnica para WebPelusa

### Historial de Cambios
- v1.0 (2026-02-16): Versión inicial completa con todos los diagramas

---

## 📧 Contacto

Para preguntas o sugerencias sobre el diseño, contactar al equipo de desarrollo.

---

## 📄 Licencia

Este diseño es parte del proyecto WebPelusa.
