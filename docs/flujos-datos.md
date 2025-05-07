# Flujos de Datos

Este documento describe los principales flujos de datos en el "Tutor Personalizado del Idioma Inglés con Interfaces No Convencionales", mostrando cómo la información se transmite entre los diferentes componentes del sistema.

## 1. Flujo de Autenticación y Configuración Inicial

```mermaid
sequenceDiagram
    participant Usuario
    participant Frontend
    participant Auth
    participant API
    participant DB
    
    Usuario->>Frontend: Accede a la aplicación
    Frontend->>Auth: Solicita autenticación
    Auth->>Usuario: Presenta opciones de login
    Usuario->>Auth: Proporciona credenciales
    Auth->>API: Valida credenciales
    API->>DB: Verifica/Crea usuario
    DB->>API: Retorna perfil
    API->>Frontend: Sesión autenticada
    Frontend->>Usuario: Solicita test inicial (si es nuevo)
    Usuario->>Frontend: Completa test de nivel MCER
    Frontend->>API: Envía resultados del test
    API->>DB: Almacena nivel y preferencias
    DB->>API: Confirma almacenamiento
    API->>Frontend: Carga dashboard personalizado
```

## 2. Flujo de Práctica de Conversación

```mermaid
sequenceDiagram
    participant Usuario
    participant Frontend
    participant API
    participant LLM
    participant Speech
    participant DB
    
    Usuario->>Frontend: Selecciona escenario
    Frontend->>API: Solicita generación de escenario
    API->>LLM: Solicita contexto/diálogo inicial
    LLM->>API: Retorna contexto generado
    API->>Frontend: Presenta escenario y avatar
    Frontend->>Usuario: Avatar inicia conversación (audio)
    
    loop Interacción de Conversación
        Usuario->>Frontend: Habla (micrófono)
        Frontend->>Speech: Envía audio para transcripción
        Speech->>Frontend: Retorna texto y análisis fonético
        Frontend->>API: Envía respuesta del usuario
        API->>LLM: Solicita análisis/respuesta
        LLM->>API: Retorna análisis y siguiente respuesta
        API->>Speech: Solicita síntesis de voz
        Speech->>API: Retorna audio sintetizado
        API->>Frontend: Envía respuesta y retroalimentación
        Frontend->>Usuario: Avatar responde y muestra feedback
    end
    
    Usuario->>Frontend: Finaliza conversación
    Frontend->>API: Envía métricas y registro
    API->>DB: Almacena progreso y análisis
    DB->>API: Confirma almacenamiento
    API->>Frontend: Muestra resumen y logros
```

## 3. Flujo de Adaptabilidad e Inferencia

```mermaid
flowchart TD
    A[Usuario Interactúa] --> B[Recolección de Datos]
    B --> C[Almacenamiento en DB]
    C --> D[Procesamiento de Patrones]
    D --> E{Toma de Decisiones}
    E --> F[Ajuste de Interfaz]
    E --> G[Personalización de Contenido]
    E --> H[Recomendaciones]
    F --> I[Aplicación de Cambios]
    G --> I
    H --> I
    I --> J[Nueva Experiencia]
    J --> A
```

## 4. Flujo de Análisis Fonético en Tiempo Real

```mermaid
sequenceDiagram
    participant Usuario
    participant Frontend
    participant WebSpeech
    participant API
    participant SpeechService
    
    Usuario->>Frontend: Habla al micrófono
    Frontend->>WebSpeech: Captura audio en chunks
    WebSpeech->>Frontend: Streaming de audio
    
    loop Análisis Continuo
        Frontend->>API: Envía fragmento de audio
        API->>SpeechService: Solicita análisis fonético
        SpeechService->>API: Retorna análisis en tiempo real
        API->>Frontend: Envía resultados
        Frontend->>Usuario: Visualiza feedback
    end
    
    Frontend->>API: Envía audio completo
    API->>SpeechService: Solicita análisis completo
    SpeechService->>API: Retorna análisis detallado
    API->>Frontend: Envía evaluación final
    Frontend->>Usuario: Muestra resumen y puntuación
```

## 5. Flujo de Datos para Modo Docente

```mermaid
sequenceDiagram
    participant Docente
    participant Frontend
    participant API
    participant DB
    participant LLM
    
    Docente->>Frontend: Accede al modo docente
    Frontend->>API: Solicita datos de estudiantes
    API->>DB: Consulta grupos y progreso
    DB->>API: Retorna datos
    API->>Frontend: Muestra dashboard docente
    
    Docente->>Frontend: Crea nuevo contenido
    Frontend->>API: Envía parámetros de contenido
    API->>LLM: Solicita generación de contenido
    LLM->>API: Retorna contenido adaptado al MCER
    API->>DB: Almacena nuevo contenido
    DB->>API: Confirma almacenamiento
    API->>Frontend: Muestra vista previa
    
    Docente->>Frontend: Asigna contenido a estudiantes
    Frontend->>API: Envía asignaciones
    API->>DB: Actualiza tareas de estudiantes
    DB->>API: Confirma actualización
    API->>Frontend: Muestra confirmación
```

## 6. Flujo de Interacción entre Usuarios

```mermaid
sequenceDiagram
    participant Usuario1
    participant Frontend1
    participant API
    participant DB
    participant Frontend2
    participant Usuario2
    
    Usuario1->>Frontend1: Inicia práctica colaborativa
    Frontend1->>API: Busca compañeros disponibles
    API->>DB: Consulta usuarios compatibles
    DB->>API: Retorna coincidencias
    API->>Frontend1: Muestra usuarios disponibles
    Usuario1->>Frontend1: Selecciona a Usuario2
    Frontend1->>API: Envía invitación
    API->>Frontend2: Notifica invitación
    Frontend2->>Usuario2: Muestra invitación
    Usuario2->>Frontend2: Acepta invitación
    Frontend2->>API: Confirma aceptación
    API->>DB: Crea sesión colaborativa
    API->>LLM: Solicita escenario para práctica
    LLM->>API: Retorna escenario generado
    API->>Frontend1: Inicia sesión
    API->>Frontend2: Inicia sesión
    
    loop Práctica Colaborativa
        Usuario1->>Frontend1: Habla/Responde
        Frontend1->>API: Transmite audio/texto
        API->>Frontend2: Reenvía audio/texto
        Frontend2->>Usuario2: Reproduce audio/muestra texto
        Usuario2->>Frontend2: Habla/Responde
        Frontend2->>API: Transmite audio/texto
        API->>Frontend1: Reenvía audio/texto
        Frontend1->>Usuario1: Reproduce audio/muestra texto
    end
    
    Usuario1->>Frontend1: Finaliza sesión
    Frontend1->>API: Notifica fin de sesión
    API->>DB: Registra interacción y métricas
    API->>Frontend1: Muestra resumen
    API->>Frontend2: Muestra resumen
```

## 7. Flujo de Procesamiento y Almacenamiento de Datos

```mermaid
flowchart TD
    A[Datos de Interacción] --> B[Preprocesamiento]
    B --> C[Normalización]
    C --> D[Clasificación]
    D --> E{Tipo de Dato}
    E --> F[Métricas de Aprendizaje]
    E --> G[Patrones de Uso]
    E --> H[Contenido Generado]
    F --> I[Base de Datos de Progreso]
    G --> J[Base de Datos de Comportamiento]
    H --> K[Base de Datos de Contenido]
    I --> L[Análisis y Reportes]
    J --> M[Modelo Predictivo]
    K --> N[Sistema de Recomendación]
    L --> O[Dashboard de Usuario]
    M --> P[Adaptación de Interfaz]
    N --> Q[Sugerencias Personalizadas]
```

## Consideraciones de Seguridad y Privacidad

- **Datos Sensibles**: Las transmisiones de audio y datos personales se cifran en tránsito y en reposo.
- **Anonimización**: Los datos utilizados para entrenamiento y mejora se anonimizan previamente.
- **Retención**: Política clara sobre períodos de retención de datos de conversación y audio.
- **Consentimiento**: Sistema de opt-in para grabación y uso de interacciones con fines de mejora.
