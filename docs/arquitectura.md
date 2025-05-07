# Arquitectura del Sistema

## Descripción General

La arquitectura de "Tutor Personalizado del Idioma Inglés" está diseñada como una aplicación de arquitectura serverless que combina varios microservicios especializados para ofrecer una experiencia de usuario fluida y adaptativa.

## Diagrama de Arquitectura

```
+------------------------------+
|        Cliente (Frontend)    |
|   React/Next.js + TailwindCSS|
+---------------+--------------+
                |
+---------------v--------------+
|       API Gateway           |
|      (Next.js API Routes)    |
+---+----------+----------+----+
    |          |          |
+---v---+  +---v---+  +---v---+
|Servicio|  |Servicio|  |Servicio|
|  Auth  |  |  LLM   |  | Speech |
+-------+  +---+---+  +---+---+
               |          |
           +---v----------v---+
           |    Bases de Datos |
           |    (MongoDB Atlas) |
           +------------------+
```

## Componentes Principales

### 1. Cliente (Frontend)
- **Tecnologías**: React.js, Next.js, TailwindCSS
- **Responsabilidades**:
  - Interfaz de usuario adaptativa
  - Comunicación con la API
  - Renderizado del avatar
  - Visualización de progreso
  - Captura de audio en tiempo real

### 2. API Gateway
- **Tecnologías**: Next.js API Routes
- **Responsabilidades**:
  - Enrutamiento de solicitudes
  - Autenticación y autorización
  - Balanceo de carga
  - Limitación de tasas de peticiones

### 3. Servicio de Autenticación
- **Tecnologías**: NextAuth.js
- **Responsabilidades**:
  - Autenticación multi-proveedor (Google, GitHub, etc.)
  - Gestión de sesiones
  - Autorización basada en roles (estudiantes, docentes)

### 4. Servicio de LLM (Modelos de Lenguaje)
- **Tecnologías**: OpenAI API, Hugging Face
- **Responsabilidades**:
  - Generación de escenarios de conversación
  - Evaluación de respuestas del usuario
  - Re-fraseo contextual
  - Creación de contenido didáctico adaptativo

### 5. Servicio de Reconocimiento y Síntesis de Voz
- **Tecnologías**: WebSpeech API, Azure Speech Services
- **Responsabilidades**:
  - Transcripción de voz a texto en tiempo real
  - Análisis fonético y detección de errores de pronunciación
  - Síntesis de voz natural para el avatar

### 6. Base de Datos
- **Tecnologías**: MongoDB Atlas
- **Responsabilidades**:
  - Almacenamiento de perfiles de usuario
  - Registro de progreso y métricas de aprendizaje
  - Historial de conversaciones y evaluaciones
  - Contenido didáctico estructurado

## Comunicación entre Componentes

- **API RESTful**: Para operaciones CRUD estándar
- **WebSockets**: Para comunicación en tiempo real durante sesiones de conversación
- **GraphQL** (opcional): Para consultas complejas de datos de progreso y análisis

## Seguridad

1. **JWT (JSON Web Tokens)**: Para autenticación segura
2. **HTTPS/TLS**: Para cifrado de comunicaciones
3. **Sanitización de Entradas**: Para prevenir inyecciones y XSS
4. **Cifrado de Datos Sensibles**: Para protección de información personal

## Escalabilidad

- Arquitectura serverless para escalar automáticamente según la demanda
- Caché distribuida para optimizar el rendimiento
- Servicios independientes que permiten escalar componentes específicos

## Consideraciones Técnicas

1. **Latencia**: Optimización crítica para mantener la latencia de transcripción por debajo de 400ms
2. **Procesamiento de Audio**: Implementación de algoritmos eficientes para análisis fonético en tiempo real
3. **Dependencias de Terceros**: Plan de contingencia para interrupciones en servicios de IA externos

## Monitorización y Logging

- Instrumentación de aplicación con Sentry para seguimiento de errores
- Métricas de rendimiento con Prometheus
- Logging centralizado con ELK Stack (Elasticsearch, Logstash, Kibana)
