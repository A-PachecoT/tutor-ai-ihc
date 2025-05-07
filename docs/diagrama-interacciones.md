# Diagrama de Interacciones

Este documento presenta el flujo de navegación e interacción entre las diferentes pantallas y componentes del "Tutor Personalizado del Idioma Inglés con Interfaces No Convencionales".

## Mapa de Navegación Principal

```mermaid
flowchart TD
    A[Página de Inicio] --> B[Login/Registro]
    B --> C{¿Usuario Nuevo?}
    C -->|Sí| D[Test de Nivel MCER]
    C -->|No| E[Dashboard Principal]
    D --> E
    
    E --> F[Práctica de Conversación]
    E --> G[Lecciones Estructuradas]
    E --> H[Análisis de Progreso]
    E --> I[Comunidad]
    E --> J[Configuración]
    
    F --> F1[Selección de Escenario]
    F1 --> F2[Sesión de Conversación]
    F2 --> F3[Resumen y Evaluación]
    F3 --> E
    
    G --> G1[Catálogo de Lecciones]
    G1 --> G2[Contenido de Lección]
    G2 --> G3[Ejercicios Prácticos]
    G3 --> G4[Evaluación de Lección]
    G4 --> G1
    
    H --> H1[Estadísticas Generales]
    H --> H2[Progreso por Habilidades]
    H --> H3[Historial de Actividades]
    
    I --> I1[Tablero de Líderes]
    I --> I2[Práctica con Compañeros]
    I --> I3[Foros de Discusión]
    
    J --> J1[Perfil de Usuario]
    J --> J2[Preferencias de Interfaz]
    J --> J3[Configuración de Avatar]
    J --> J4[Gestión de Suscripción]
    
    %% Modo Docente
    B --> K{¿Es Docente?}
    K -->|Sí| L[Panel Docente]
    L --> L1[Gestión de Estudiantes]
    L --> L2[Creación de Contenido]
    L --> L3[Análisis de Desempeño]
    L --> L4[Gestión de Asignaciones]
```

## Diagrama Detallado de Interacciones en Sesión de Conversación

```mermaid
sequenceDiagram
    actor Usuario
    participant Avatar
    participant Sistema de Voz
    participant Análisis Fonético
    participant LLM
    
    Usuario->>Sistema de Voz: Inicia micrófono
    Sistema de Voz->>Usuario: Confirma activación
    Avatar->>Usuario: Inicia diálogo
    
    loop Ciclo de Conversación
        Usuario->>Sistema de Voz: Habla (input de audio)
        Sistema de Voz->>Análisis Fonético: Procesa audio
        Análisis Fonético->>Usuario: Muestra feedback en tiempo real
        Sistema de Voz->>LLM: Envía transcripción
        LLM->>Avatar: Genera respuesta
        Avatar->>Usuario: Responde verbalmente
        Análisis Fonético->>Usuario: Muestra resumen fonético
        LLM->>Usuario: Ofrece sugerencias contextuales
    end
    
    Usuario->>Avatar: Finaliza conversación
    Avatar->>Usuario: Proporciona resumen
    Sistema->>Usuario: Muestra métricas y logros
```

## Flujo de Adaptación de Interfaz

```mermaid
flowchart TD
    A[Usuario Interactúa] --> B[Sistema recopila datos]
    B --> C[Análisis de comportamiento]
    C --> D{¿Patrones identificados?}
    D -->|No| A
    D -->|Sí| E[Actualización de perfil de usuario]
    E --> F[Ajustes de interfaz]
    
    F --> G[Adaptación visual]
    F --> H[Adaptación de contenido]
    F --> I[Adaptación de dificultad]
    F --> J[Adaptación de feedback]
    
    G --> K[Nueva experiencia adaptada]
    H --> K
    I --> K
    J --> K
    
    K --> A
```

## Interacciones del Sistema de Gamificación

```mermaid
flowchart LR
    A[Acciones del Usuario] --> B{Tipo de Acción}
    B -->|Completar Lección| C[+XP Base]
    B -->|Conversación Exitosa| D[+XP Según Duración]
    B -->|Precisión Fonética| E[+XP Según Score]
    B -->|Racha Diaria| F[+XP Multiplicador]
    
    C --> G[Actualizar Progreso]
    D --> G
    E --> G
    F --> G
    
    G --> H{¿Nivel Completado?}
    H -->|No| I[Actualizar Barra de Progreso]
    H -->|Sí| J[Animar Subida de Nivel]
    
    G --> K{¿Logro Desbloqueado?}
    K -->|Sí| L[Mostrar Notificación]
    L --> M[Actualizar Perfil]
    
    G --> N{¿Entrar en Ranking?}
    N -->|Sí| O[Actualizar Leaderboard]
    
    I --> P[Actualizar UI]
    J --> P
    M --> P
    O --> P
```

## Mapa de Estados de Interfaz Adaptativa

```mermaid
stateDiagram-v2
    [*] --> EstadoInicial
    EstadoInicial --> NivelPrincipiante: Resultado Test Inicial
    EstadoInicial --> NivelIntermedio: Resultado Test Inicial
    EstadoInicial --> NivelAvanzado: Resultado Test Inicial
    
    NivelPrincipiante --> ModoGuiado: Primeros Usos
    ModoGuiado --> ModoAsistido: Mejora Confianza
    ModoAsistido --> ModoIndependiente: Mayor Habilidad
    
    NivelIntermedio --> ModoAsistido: Primeros Usos
    ModoAsistido --> ModoIndependiente: Mejora Competencia
    ModoIndependiente --> ModoExperto: Alta Competencia
    
    NivelAvanzado --> ModoIndependiente: Primeros Usos
    ModoIndependiente --> ModoExperto: Demostración Competencia
    
    ModoGuiado --> EnfoqueGramatical: Análisis Comportamiento
    ModoGuiado --> EnfoqueConversacional: Análisis Comportamiento
    
    ModoAsistido --> EnfoqueGramatical: Análisis Comportamiento
    ModoAsistido --> EnfoqueConversacional: Análisis Comportamiento
    
    ModoIndependiente --> EnfoqueGramatical: Análisis Comportamiento
    ModoIndependiente --> EnfoqueConversacional: Análisis Comportamiento
    
    ModoExperto --> EnfoqueGramatical: Análisis Comportamiento
    ModoExperto --> EnfoqueConversacional: Análisis Comportamiento
    
    EnfoqueGramatical --> EstiloVisual: Preferencia Usuario
    EnfoqueGramatical --> EstiloAuditivo: Preferencia Usuario
    
    EnfoqueConversacional --> EstiloVisual: Preferencia Usuario
    EnfoqueConversacional --> EstiloAuditivo: Preferencia Usuario
```

## Interacciones Modo Docente

```mermaid
flowchart TD
    A[Login Docente] --> B[Panel Principal Docente]
    
    B --> C[Gestión de Estudiantes]
    C --> C1[Añadir Estudiantes]
    C --> C2[Agrupar Estudiantes]
    C --> C3[Ver Perfil Individual]
    
    B --> D[Creación de Contenido]
    D --> D1[Lecciones Predefinidas]
    D --> D2[Asistente IA]
    D --> D3[Editor Manual]
    D1 --> D4[Personalizar Lección]
    D2 --> D4
    D3 --> D4
    D4 --> D5[Publicar Lección]
    
    B --> E[Análisis de Desempeño]
    E --> E1[Vista General Grupo]
    E --> E2[Comparativas]
    E --> E3[Reportes Descargables]
    
    B --> F[Gestión de Asignaciones]
    F --> F1[Crear Asignación]
    F --> F2[Revisar Entregas]
    F --> F3[Calificar Automáticamente]
    F --> F4[Retroalimentación Grupal]
    
    C3 --> G[Perfil Estudiante]
    G --> G1[Progreso Detallado]
    G --> G2[Recomendaciones IA]
    G --> G3[Comunicación Directa]
    G --> G4[Historial de Actividad]
```

## Detalle de Interacciones Multimodales

```mermaid
flowchart TB
    A[Input Usuario] --> B{Tipo de Entrada}
    
    B -->|Voz| C[Procesamiento de Audio]
    C --> C1[Transcripción]
    C --> C2[Análisis Fonético]
    C --> C3[Análisis Emocional]
    
    B -->|Expresión Facial| D[Procesamiento de Imagen]
    D --> D1[Detección Emocional]
    D --> D2[Nivel de Atención]
    
    B -->|Interacción UI| E[Procesamiento de Eventos]
    E --> E1[Tiempo de Respuesta]
    E --> E2[Patrones de Navegación]
    E --> E3[Preferencias Implícitas]
    
    C1 --> F[Motor de Integración]
    C2 --> F
    C3 --> F
    D1 --> F
    D2 --> F
    E1 --> F
    E2 --> F
    E3 --> F
    
    F --> G[Decisión Adaptativa]
    G --> H[Output Sistema]
    
    H --> I{Tipo de Salida}
    I -->|Visual| J[Interfaz Gráfica]
    I -->|Auditiva| K[Respuesta de Voz]
    I -->|Háptica| L[Feedback Táctil]
    
    J --> M[Experiencia Integrada]
    K --> M
    L --> M
```

## Nota sobre Implementación

Los diagramas presentados representan el diseño conceptual del sistema y sus interacciones. La implementación técnica seguirá estos flujos, adaptándose según necesidades específicas de desarrollo y retroalimentación de usuarios durante las fases de prueba.

Durante el desarrollo del MVP, se priorizarán las interacciones marcadas en el primer diagrama de flujo, específicamente las rutas principales de navegación y la funcionalidad core de práctica de conversación.
