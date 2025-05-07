# Tecnologías Utilizadas

Este documento detalla las tecnologías y herramientas seleccionadas para la implementación del "Tutor Personalizado del Idioma Inglés con Interfaces No Convencionales".

## Frontend

### Framework Principal
- **Next.js 14**: Framework de React que facilita el desarrollo de aplicaciones web con renderizado del lado del servidor (SSR) y generación estática (SSG).
- **React 18**: Biblioteca para construir interfaces de usuario interactivas.

### Estilos y UI
- **TailwindCSS**: Framework de utilidades CSS para estilizado rápido y consistente.
- **Framer Motion**: Biblioteca para animaciones fluidas en React.
- **ThreeJS**: Biblioteca para renderizar y animar el avatar 3D.

### Interfaces No Convencionales
- **MediaPipe**: Biblioteca de Google para tracking facial y detección de gestos.
- **WebSpeech API**: API nativa para reconocimiento y síntesis de voz.
- **Howler.js**: Biblioteca de audio para efectos sonoros y feedback auditivo.

## Backend

### Infraestructura
- **Vercel**: Plataforma serverless para hosting y despliegue.
- **NodeJS**: Entorno de ejecución para JavaScript del lado del servidor.

### Autenticación
- **NextAuth.js**: Solución de autenticación para aplicaciones Next.js que facilita múltiples proveedores.

### Base de Datos
- **MongoDB Atlas**: Base de datos NoSQL en la nube para almacenamiento de datos de usuario y progreso.
- **Prisma**: ORM (Object-Relational Mapping) para interactuar con la base de datos.

## IA y Procesamiento de Lenguaje

### Modelos de Lenguaje
- **OpenAI API (GPT-4)**: Para la generación de escenarios de conversación y análisis contextual.
- **Hugging Face Transformers**: Para modelos más específicos de análisis de lenguaje.

### Procesamiento de Audio
- **Azure Speech Services**: Para análisis fonético avanzado y síntesis de voz de alta calidad.
- **TensorFlow.js**: Para implementar modelos de IA en el navegador para análisis en tiempo real.

## Herramientas de Desarrollo

### Control de Versiones
- **Git**: Sistema de control de versiones.
- **GitHub**: Plataforma de alojamiento de repositorios y colaboración.

### Calidad del Código
- **TypeScript**: Superset de JavaScript que añade tipado estático.
- **ESLint**: Herramienta para identificar y reportar patrones en código JavaScript.
- **Prettier**: Formateador de código para mantener un estilo consistente.

### Testing
- **Jest**: Framework de testing para JavaScript.
- **Cypress**: Herramienta de testing end-to-end.
- **React Testing Library**: Utilidades para testear componentes React.

## Monitorización y Análisis

### Rendimiento
- **Vercel Analytics**: Para análisis de rendimiento y comportamiento del usuario.
- **Sentry**: Para monitorización de errores en tiempo real.

### Analíticas de Aprendizaje
- **XAPI (Experience API)**: Especificación para recolectar datos sobre experiencias de aprendizaje.
- **Learning Locker**: LRS (Learning Record Store) para almacenar y analizar datos XAPI.

## Integraciones y APIs Externas

### Servicios en la Nube
- **AWS S3**: Para almacenamiento de archivos (audios grabados, recursos multimedia).
- **Cloudinary**: Para optimización y transformación de imágenes.

### Gestión de Contenidos
- **Contentful**: CMS headless para gestionar contenido didáctico estructurado.

### Procesamiento de Pagos
- **Stripe**: Para gestión de pagos y subscripciones.

## Despliegue y CI/CD

### Integración Continua
- **GitHub Actions**: Para automatización del pipeline de CI/CD.

### Contenedores y Orquestación
- **Docker**: Para entornos de desarrollo consistentes.
- **Docker Compose**: Para orquestar servicios en entorno de desarrollo.

## Consideraciones de Accesibilidad

- **React-axe**: Para evaluar la accesibilidad de componentes React.
- **ARIA**: Implementación de atributos ARIA para mejorar la accesibilidad.
- **Conformidad WCAG 2.1 AA**: Como estándar mínimo para accesibilidad web.
