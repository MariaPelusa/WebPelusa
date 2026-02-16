# Entregables - Diagrama UML de Aplicación de Colaboración Artística

## 📦 Resumen de lo Entregado

Se ha creado una documentación UML completa para una aplicación de colaboración entre artistas que cumple con todos los requisitos especificados:

### ✅ Requisitos Cumplidos

1. **Registro de usuarios (artistas)** ✓
   - Clase `Usuario` para autenticación
   - Clase `Artista` para perfil profesional

2. **Perfil público con galería de imágenes** ✓
   - Clase `PerfilPublico` con información visible
   - Clase `Imagen` para gestionar la galería de trabajos

3. **Mensajería privada entre artistas** ✓
   - Clase `Conversacion` para hilos de mensajes
   - Clase `MensajePrivado` para comunicación directa

4. **Localización de artistas mediante mapa** ✓
   - Clase `Ubicacion` para posición geográfica
   - Clase `Mapa` para búsqueda y visualización

5. **Tablón de anuncios para proyectos colaborativos** ✓
   - Clase `TablonanAnuncios` para gestionar publicaciones
   - Clase `Proyecto` para proyectos que requieren múltiples personas
   - Clase `Solicitud` para que artistas puedan aplicar

## 📁 Estructura de Archivos Creados

```
docs/uml/
├── INDEX.md                          # Índice con descripción de todos los diagramas
├── README.md                         # Documentación técnica completa
├── artist-collaboration-app.puml     # Diagrama de clases principal (PlantUML)
├── diagram-mermaid.md                # Diagrama de clases en formato Mermaid
├── use-cases.puml                    # Diagrama de casos de uso
├── sequence-apply-project.puml       # Secuencia: aplicar a proyecto
└── sequence-messaging.puml           # Secuencia: mensajería entre artistas
```

## 🎯 Diagramas Creados

### 1. Diagrama de Clases (2 versiones)
- **PlantUML** (`artist-collaboration-app.puml`): Versión completa y detallada
- **Mermaid** (`diagram-mermaid.md`): Versión que se renderiza en GitHub

**Contiene:**
- 13 clases principales
- 3 enumeraciones (Estados de proyecto, solicitud, y tipos de notificación)
- Relaciones completas (1:1, 1:N, N:M)
- Métodos y atributos de cada clase
- Notas explicativas

### 2. Diagrama de Casos de Uso
**Archivo:** `use-cases.puml`

**Incluye:**
- 30 casos de uso organizados en 7 paquetes
- 3 actores (Artista, Sistema de Notificaciones, Servicio de Mapas)
- Relaciones include/extend
- Notas explicativas

### 3. Diagramas de Secuencia (2)

**a) Aplicación a Proyecto** (`sequence-apply-project.puml`)
- Búsqueda de proyectos
- Envío de solicitud
- Revisión y aceptación/rechazo
- Sistema de notificaciones

**b) Mensajería** (`sequence-messaging.puml`)
- Búsqueda de artista
- Inicio de conversación
- Envío y lectura de mensajes
- Respuestas

## 📖 Documentación

### README.md Principal
Incluye:
- Descripción detallada de cada funcionalidad
- Explicación de todas las entidades
- Relaciones entre entidades
- Enumeraciones y sus valores
- Consideraciones técnicas:
  - Seguridad
  - Privacidad
  - Rendimiento
  - Escalabilidad
- Tecnologías sugeridas (Backend, Frontend, Infraestructura)
- Posibles extensiones futuras

### INDEX.md
Índice completo con:
- Descripción de cada diagrama
- Instrucciones para visualizar
- Principios de diseño aplicados
- Patrones de diseño utilizados
- Versionado

## 🛠️ Cómo Usar los Diagramas

### Visualización Online (Más fácil)
1. Ir a [PlantUML Online Editor](https://www.plantuml.com/plantuml/uml/)
2. Copiar contenido de archivo `.puml`
3. Pegar en el editor - se renderiza automáticamente

### En GitHub
- El archivo `diagram-mermaid.md` se visualiza directamente en GitHub
- Ver: https://github.com/MariaPelusa/WebPelusa/blob/[branch]/docs/uml/diagram-mermaid.md

### En VS Code
1. Instalar extensión "PlantUML"
2. Abrir archivo `.puml`
3. Presionar `Alt+D` para vista previa

### Generar Imágenes
```bash
# Si tienes PlantUML instalado
plantuml docs/uml/*.puml
```

## 🔑 Características Principales del Diseño

### Modularidad
Cada funcionalidad está claramente separada en su propio conjunto de clases

### Escalabilidad
- Diseño preparado para soportar miles de usuarios
- Paginación en listados
- Índices de base de datos considerados

### Seguridad
- Autenticación y autorización
- Control de privacidad de ubicación
- Encriptación de contraseñas
- Validación de datos

### Extensibilidad
El diseño permite añadir fácilmente:
- Sistema de valoraciones
- Categorías avanzadas
- Pagos integrados
- Chat en tiempo real
- Calendarios
- Eventos y exposiciones

## 📊 Estadísticas del Diseño

- **Clases:** 13
- **Enumeraciones:** 3
- **Casos de Uso:** 30
- **Diagramas de Secuencia:** 2
- **Relaciones:** ~25
- **Métodos definidos:** ~60
- **Atributos definidos:** ~70

## ✨ Calidad de la Documentación

- ✅ Diagramas en múltiples formatos (PlantUML y Mermaid)
- ✅ Documentación técnica exhaustiva
- ✅ Ejemplos de flujos de trabajo
- ✅ Consideraciones de implementación
- ✅ Recomendaciones de tecnología
- ✅ Guías de visualización
- ✅ Índice organizado

## 🎓 Uso Académico/Profesional

Esta documentación es adecuada para:
- Presentaciones de diseño de software
- Documentación técnica de proyectos
- Planificación de desarrollo
- Comunicación con stakeholders
- Base para implementación
- Enseñanza de diseño orientado a objetos

## 📝 Próximos Pasos Sugeridos

1. **Validación:** Revisar con stakeholders
2. **Refinamiento:** Ajustar según feedback
3. **Implementación:** Usar como guía para desarrollo
4. **Testing:** Crear casos de prueba basados en diagramas
5. **Iteración:** Actualizar según evolución del proyecto

## 🔗 Referencias

- Documentación principal: `docs/uml/README.md`
- Índice de diagramas: `docs/uml/INDEX.md`
- README del proyecto: `README.md`

---

**Fecha de creación:** 16 de febrero de 2026
**Versión:** 1.0
**Estado:** Completado ✅
