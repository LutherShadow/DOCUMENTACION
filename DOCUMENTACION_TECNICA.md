
# DOCUMENTACIÓN TÉCNICA DEL PROYECTO

**Nombre del Proyecto:** EduApp  
**Fecha de elaboración:** 20 de mayo de 2025  
**Responsable:** Equipo de Desarrollo Oficial EduApp

## 1. PLATAFORMAS Y ACCESOS

La implementación del proyecto EduApp se basa en una arquitectura distribuida que utiliza diversas plataformas cloud especializadas, cada una cumpliendo un rol específico en el ciclo de desarrollo y despliegue. Este enfoque permite mantener un flujo de trabajo ágil y una infraestructura escalable, optimizando tanto el desarrollo como el rendimiento de la aplicación final.

### 1.1 Control de Versiones (GitHub)
- **Repositorio:** https://github.com/SatanaeShadow/eduapp.git
- **Credenciales:**
  - Usuario: [CREDENCIAL PROTEGIDA]
  - Correo asociado: [CREDENCIAL PROTEGIDA]
  - Nota: Las credenciales completas se almacenan en el gestor de contraseñas del equipo

GitHub funciona como el repositorio central para el control de versiones del proyecto, permitiendo la colaboración entre múltiples desarrolladores mediante un sistema de ramificación (branching) organizado. Se ha configurado para trabajar con la integración continua, activando automáticamente los procesos de construcción y despliegue en Netlify cuando se realizan cambios en la rama principal. Este flujo optimiza el ciclo de desarrollo al automatizar tareas repetitivas y garantizar que siempre esté disponible la versión más reciente de la aplicación.

### 1.2 Hosting y Despliegue (Netlify)
- **URL de la aplicación:** https://eduapp-edu.netlify.app/
- **Panel de administración:** https://app.netlify.com/sites/eduapp-edu/
- **Método de acceso:**
  - Login con GitHub (vinculado al usuario principal)
- **Configuración de despliegue:**
  - Despliegue automático desde la rama `main`
  - Comando de construcción: `npm run build`
  - Directorio publicado: `dist`
  - Variables de entorno configuradas desde el panel de Netlify

Netlify proporciona la infraestructura de hosting para la aplicación, ofreciendo una plataforma robusta con capacidades CDN que mejoran significativamente los tiempos de carga desde cualquier ubicación geográfica. El proceso de despliegue está completamente automatizado: cuando se detectan cambios en la rama principal del repositorio, Netlify ejecuta el proceso de construcción definido, verifica que no existan errores y despliega la nueva versión. Adicionalmente, cada pull request genera una URL de vista previa, facilitando la revisión de cambios antes de integrarlos al entorno de producción.

### 1.3 Base de Datos (Supabase)
- **URL del proyecto:** https://mucdwmcxdaosxivkowfq.supabase.co
- **Panel de administración:** https://supabase.com/dashboard/project/mucdwmcxdaosxivkowfq
- **Método de acceso:**
  - Login con GitHub (vinculado al usuario principal)
- **Configuración de la base de datos:**
  - **Tablas principales:**
    - `user_credentials`: Almacena datos de autenticación
    - `user_profiles`: Perfiles de usuario extendidos
    - `institutions`: Información de las instituciones educativas
    - `students`: Registro de estudiantes
    - `attendance_records`: Control de asistencia
    - `pickup_permissions`: Permisos de recogida de estudiantes
    - `notifications`: Sistema de notificaciones internas
  - **Funciones relevantes:**
    - `create_user_with_profile`: Creación de usuarios con perfil asociado
    - `cleanup_orphaned_profiles`: Limpieza de perfiles huérfanos
    - `register_user_without_profile`: Registro de usuarios sin perfil
  - **Políticas de seguridad (RLS):**
    - Implementadas en todas las tablas para segregación de datos por rol
  - **Edge Functions:**
    - `register_user`: Gestión de registro de usuarios
    - `search_institutions`: Búsqueda de instituciones educativas
    - `send-email`: Servicio de envío de correos electrónicos

Supabase constituye el núcleo de la infraestructura de backend del proyecto, proporcionando una base de datos PostgreSQL con capacidades avanzadas y una API RESTful autogenerada. El modelo de datos se ha diseñado siguiendo principios de normalización y optimización de consultas, con especial atención a las relaciones entre entidades principales. Las políticas de seguridad a nivel de fila (Row Level Security) implementan un modelo de acceso granular que garantiza que los usuarios solo puedan ver y modificar la información pertinente a su rol y contexto, evitando posibles filtraciones de datos sensibles o manipulaciones no autorizadas.

El esquema relacional implementa vínculos estratégicos entre las entidades principales: los usuarios (`user_credentials`) se asocian con perfiles extendidos (`user_profiles`) mediante una relación uno a uno, permitiendo separar los datos de autenticación de la información personal. Las instituciones (`institutions`) se vinculan con administradores y docentes, quienes a su vez gestionan estudiantes (`students`). Estos estudiantes generan registros de asistencia (`attendance_records`) y están sujetos a permisos de recogida (`pickup_permissions`) solicitados por los padres. Este diseño facilita consultas eficientes y mantiene la integridad referencial en todos los procesos.

### 1.4 Conversión a APK (WebIntoApp)
- **URL de la plataforma:** https://www.webintoapp.com/
- **Credenciales:**
  - Acceso mediante credenciales almacenadas en el gestor de contraseñas
- **Configuración del APK:**
  - **Nombre del paquete:** com.eduapp.education
  - **Versión actual:** 1.0.0
  - **Icono y splash screen:** Personalizados según la identidad visual de EduApp
  - **Permisos requeridos:**
    - Almacenamiento (para subir documentos y fotos)
    - Cámara (opcional, para escaneado de documentos)
    - Notificaciones (para alertas de asistencia y permisos)
  - **Configuración de PWA:**
    - Service Worker implementado para funcionamiento offline
    - Manifest configurado para instalación como aplicación

La plataforma WebIntoApp se utiliza para convertir nuestra aplicación web en una aplicación Android nativa, proporcionando una experiencia de usuario mejorada en dispositivos móviles con acceso a características nativas del sistema. El proceso de conversión preserva la funcionalidad de la aplicación web mientras añade capacidades específicas de dispositivos móviles como notificaciones push y acceso a la cámara para digitalización de documentos. La aplicación resultante mantiene la coherencia con la versión web pero ofrece una experiencia más integrada con el dispositivo, mejorando significativamente la usabilidad en contextos móviles donde maestros y padres necesitan acceso rápido a la información sin depender de un navegador.

## 2. ESTRUCTURA DEL PROYECTO

EduApp sigue una arquitectura frontend moderna basada en componentes, con separación clara de responsabilidades y una estructura de directorios que facilita el mantenimiento y la escalabilidad del código. El diseño arquitectónico prioriza la reutilización de componentes, la separación de lógica de negocio y presentación, y la optimización del rendimiento mediante técnicas como Code Splitting y lazy loading.

### 2.1 Arquitectura de la Aplicación
- **Framework Frontend:** React + Vite
- **Gestión de Estado:** React Context API + React Query
- **Estilos:** Tailwind CSS + shadcn/ui
- **Autenticación:** Supabase Auth
- **Almacenamiento de archivos:** Supabase Storage

La arquitectura frontend de EduApp se basa en React como biblioteca principal, aprovechando su paradigma declarativo y su eficiente algoritmo de reconciliación (Virtual DOM) para optimizar las actualizaciones del UI. Vite proporciona un entorno de desarrollo ultrarrápido con recarga en caliente (HMR) instantánea y una configuración de construcción optimizada para producción. La combinación de React Context API para el estado global de la aplicación y React Query para la gestión del estado del servidor proporciona un control eficiente del flujo de datos, minimizando las solicitudes redundantes y manteniendo la interfaz sincronizada con el backend.

Para los estilos, se utiliza Tailwind CSS con la biblioteca shadcn/ui, lo que permite un desarrollo visual coherente y rápido mediante clases de utilidad, evitando la sobrecarga de CSS personalizado y facilitando la creación de interfaces consistentes. La autenticación y el almacenamiento de archivos se gestionan a través de Supabase, proporcionando una integración segura y eficiente con el backend.

### 2.2 Estructura de Directorios
```
eduapp/
├── docs/                  # Documentación del proyecto
├── public/                # Archivos estáticos
├── src/
│   ├── components/        # Componentes reutilizables
│   │   ├── admin/         # Componentes específicos para administradores
│   │   ├── auth/          # Componentes de autenticación
│   │   ├── attendance/    # Componentes de control de asistencia
│   │   ├── motor-skills/  # Componentes de desarrollo motriz
│   │   ├── navigation/    # Componentes de navegación
│   │   ├── parent/        # Componentes específicos para padres
│   │   ├── permissions/   # Componentes de gestión de permisos
│   │   ├── profile/       # Componentes de perfil de usuario
│   │   ├── shared/        # Componentes compartidos entre roles
│   │   └── ui/            # Componentes de interfaz básicos
│   ├── hooks/             # Hooks personalizados
│   │   ├── admin/         # Hooks para administradores
│   │   ├── auth/          # Hooks de autenticación
│   │   ├── parent/        # Hooks para padres
│   │   ├── profile/       # Hooks de perfil
│   │   └── teacher/       # Hooks para profesores
│   ├── integrations/      # Integraciones con servicios externos
│   ├── lib/               # Utilidades y funciones compartidas
│   │   └── supabase/      # Cliente y tipos de Supabase
│   ├── pages/             # Páginas principales
│   │   ├── admin/         # Páginas de administrador
│   │   ├── auth/          # Páginas de autenticación
│   │   ├── parent/        # Páginas para padres
│   │   └── teacher/       # Páginas para profesores
│   ├── styles/            # Estilos globales y utilidades
│   ├── types/             # Definiciones de tipos TypeScript
│   ├── App.tsx            # Componente principal
│   └── main.tsx           # Punto de entrada
├── supabase/              # Configuración de Supabase
│   ├── functions/         # Edge Functions
│   └── migrations/        # Migraciones de base de datos
└── [Archivos de configuración]
```

La estructura de directorios de EduApp sigue el principio de "separación de preocupaciones" (separation of concerns), organizando el código por funcionalidad y rol de usuario. Los componentes reutilizables se encuentran en el directorio `components`, categorizado por su función específica dentro de la aplicación. Los hooks personalizados, que encapsulan la lógica de negocio y el estado, se agrupan en `hooks`, nuevamente segmentados según su propósito. Las páginas, que representan rutas completas de la aplicación, se organizan en el directorio `pages`.

Esta estructura facilita no solo la navegación y mantenimiento del código, sino también la implementación de características como Code Splitting, permitiendo cargar bajo demanda solo las partes de la aplicación que el usuario necesita según su rol y contexto de uso. Además, la separación clara entre componentes de UI, lógica de negocio e integración con servicios externos permite un desarrollo más modular y testeable.

### 2.3 Páginas Web (Rutas)
- **Públicas:**
  - `/` → Página de inicio y login
  - `/register` → Registro de usuarios
  - `/recover-password` → Recuperación de contraseñas
- **Admin:**
  - `/admin/dashboard` → Panel principal de administrador
  - `/admin/users` → Gestión de usuarios
  - `/admin/profile` → Perfil de administrador
  - `/admin/settings` → Configuraciones generales
- **Profesor:**
  - `/teacher/dashboard` → Panel principal de profesor
  - `/teacher/attendance` → Control de asistencia
  - `/teacher/motor-skills` → Evaluación de desarrollo motriz
  - `/teacher/motor-skills/create-form` → Creación de formularios
  - `/teacher/motor-skills/form/:id` → Detalle de formulario
  - `/teacher/permissions` → Gestión de permisos de recogida
  - `/teacher/profile` → Perfil de profesor
- **Padre/Tutor:**
  - `/parent/dashboard` → Panel principal de padre
  - `/parent/attendance` → Visualización de asistencia
  - `/parent/development` → Reportes de desarrollo
  - `/parent/permissions` → Solicitud de permisos de recogida
  - `/parent/profile` → Perfil de padre

El sistema de enrutamiento de EduApp implementa una estrategia basada en roles que dirige a los usuarios a diferentes secciones de la aplicación según sus permisos. Esta segregación no solo mejora la experiencia del usuario al presentar únicamente las funcionalidades relevantes para cada rol, sino que también refuerza la seguridad al prevenir el acceso no autorizado a rutas protegidas. El enrutamiento se gestiona a través de React Router, que facilita la navegación declarativa y la gestión de parámetros dinámicos (como IDs de formularios o estudiantes).

Las rutas públicas son accesibles sin autenticación y principalmente se enfocan en el proceso de acceso al sistema. Las rutas protegidas requieren autenticación y, además, verifican el rol del usuario para garantizar que solo accedan a las funcionalidades correspondientes a su perfil. Este sistema se complementa con redirecciones inteligentes que llevan al usuario a su dashboard específico tras el inicio de sesión, mejorando así la fluidez de la experiencia de usuario.

### 2.4 Diagrama de Flujo del Sistema

```
┌─────────────┐     ┌─────────────┐     ┌─────────────────────┐
│             │     │             │     │                     │
│  GitHub     │────▶│  Netlify    │────▶│  Navegador Web      │
│  (Código)   │     │  (Hosting)  │     │  (Aplicación Web)   │
│             │     │             │     │                     │
└─────────────┘     └─────────────┘     └──────────┬──────────┘
                                                   │
                                                   ▼
┌─────────────┐     ┌─────────────┐     ┌─────────────────────┐
│             │     │             │     │                     │
│ WebIntoApp  │◀───▶│ APK Android │◀───▶│  Supabase           │
│ (Conversión)│     │ (App móvil) │     │  (Backend/Base de   │
│             │     │             │     │   datos/Storage)    │
└─────────────┘     └─────────────┘     └─────────────────────┘
```

El flujo de datos y operaciones en EduApp sigue un patrón circular que comienza con el desarrollo y termina con la experiencia del usuario. El código fuente se almacena en GitHub, donde los desarrolladores colaboran y gestionan versiones. Cuando se realiza un cambio en la rama principal, Netlify detecta automáticamente la actualización y activa el proceso de construcción y despliegue, generando una nueva versión de la aplicación web accesible a través de cualquier navegador.

Paralelamente, la aplicación se convierte en un APK nativo para Android utilizando WebIntoApp, proporcionando una experiencia móvil optimizada. Tanto la versión web como la aplicación móvil se comunican con Supabase, que actúa como capa de backend y almacenamiento, gestionando datos, autenticación y lógica de servidor a través de las funciones Edge y políticas de RLS. Este diseño arquitectónico garantiza coherencia en la experiencia del usuario independientemente del dispositivo utilizado, mientras optimiza el rendimiento mediante la distribución equilibrada de responsabilidades entre cliente y servidor.

### 2.5 Flujo de Autenticación
1. El usuario ingresa credenciales en la página de login
2. La aplicación envía las credenciales a Supabase Auth
3. Supabase valida y devuelve un token JWT
4. La aplicación almacena el token y redirige al dashboard correspondiente según el rol
5. Las solicitudes posteriores incluyen el token para autenticación

El proceso de autenticación implementado en EduApp utiliza un flujo de credenciales (email/password) procesado por Supabase Auth. Cuando un usuario introduce sus credenciales, la solicitud se transmite de forma segura (HTTPS) a los servicios de autenticación de Supabase, que verifican la validez de las credenciales contra los registros de `user_credentials` en la base de datos. Si son correctas, Supabase genera un token JWT (JSON Web Token) firmado que contiene información sobre la identidad y los privilegios del usuario.

Este token se almacena en el navegador mediante localStorage, siguiendo prácticas de seguridad para prevenir ataques XSS. El token incluye la fecha de expiración y se renueva automáticamente mediante un sistema de refresh tokens cuando está próximo a caducar, lo que permite mantener sesiones persistentes sin comprometer la seguridad. El contexto de autenticación en la aplicación React observa este token y actualiza el estado global, habilitando o restringiendo funcionalidades según los permisos del usuario. Todas las solicitudes subsiguientes a las APIs de Supabase incluyen este token en los encabezados, permitiendo la validación continua de la identidad y derechos de acceso del usuario.

### 2.6 Principales Flujos de Usuario

#### Registro de Asistencia (Profesor)
1. Profesor ingresa a `/teacher/attendance`
2. Selecciona fecha y grupo
3. Marca asistencia individual o masiva
4. Sistema registra en `attendance_records`
5. Notificación automática a padres (opcional)

El flujo de registro de asistencia está diseñado para optimizar la eficiencia del profesor mientras asegura la precisión de los registros. Cuando un docente accede a la página de asistencia, el sistema carga automáticamente la lista de estudiantes asignados, agrupados por grado y grupo para facilitar la gestión de clases múltiples. La interfaz permite dos modalidades de registro: individual, donde el profesor puede marcar entradas, salidas y ausencias estudiante por estudiante, agregando notas específicas cuando sea necesario; y masiva, que permite marcar asistencia o ausencia para todo un grupo con un solo clic, ideal para situaciones rutinarias.

Cada registro de asistencia se almacena en tiempo real en la tabla `attendance_records`, vinculando el estudiante, fecha, hora de entrada/salida y estado (presente, ausente, tardanza). Opcionalmente, el sistema puede enviar notificaciones automáticas a los padres cuando se registra una ausencia o llegada tardía, facilitando la comunicación temprana de situaciones que requieren atención. La interfaz también ofrece visualización de tendencias y patrones de asistencia, ayudando al profesor a identificar estudiantes con problemas recurrentes que podrían necesitar seguimiento adicional.

#### Solicitud de Permiso de Recogida (Padre)
1. Padre ingresa a `/parent/permissions`
2. Completa formulario con datos de la persona autorizada
3. Adjunta identificación (almacenada en Supabase Storage)
4. Envía solicitud que se registra en `pickup_permissions`
5. Profesor recibe notificación para aprobar/rechazar

El flujo de solicitud de permisos de recogida está diseñado pensando en la seguridad de los estudiantes y la tranquilidad de los padres. Los padres o tutores acceden a la sección de permisos donde pueden visualizar autorizaciones anteriores y crear nuevas. Al solicitar un nuevo permiso, el sistema guía al usuario a través de un formulario estructurado que captura información esencial: identidad de la persona autorizada, relación con el estudiante, fecha específica o rango de fechas para la autorización, y un motivo que justifique la solicitud.

Un componente crítico de este proceso es la carga de una identificación oficial de la persona autorizada, que se almacena de forma segura en Supabase Storage con encriptación y acceso controlado. El sistema verifica automáticamente que la imagen sea legible y cumpla con requisitos mínimos de calidad antes de aceptar la solicitud. Una vez enviada, la solicitud se registra en la tabla `pickup_permissions` con estado "pendiente" y genera una notificación instantánea para el profesor responsable del estudiante. El profesor puede entonces revisar todos los detalles, incluyendo la identificación adjunta, y aprobar o rechazar la solicitud desde su dashboard, enviando una confirmación al padre y actualizando el registro en la base de datos. Este flujo bidireccional asegura que solo personas explícitamente autorizadas puedan recoger a los estudiantes, manteniendo un registro detallado de todas las autorizaciones y sus estados.

#### Evaluación de Desarrollo Motriz (Profesor)
1. Profesor ingresa a `/teacher/motor-skills`
2. Crea nuevo formulario o utiliza plantilla existente
3. Selecciona estudiantes para evaluar
4. Completa evaluación individual o grupal
5. Sistema almacena resultados y genera reportes

El sistema de evaluación de desarrollo motriz representa una de las funcionalidades más sofisticadas de EduApp, diseñada para facilitar el seguimiento detallado del desarrollo físico y cognitivo de los estudiantes de preescolar. Los profesores pueden acceder a un conjunto de herramientas especializadas para crear formularios de evaluación personalizados o utilizar plantillas predefinidas que cubren diferentes aspectos del desarrollo motriz según grupos de edad y objetivos pedagógicos específicos.

El proceso comienza con la selección de un formulario, que puede contener diversos tipos de campos de evaluación: escalas de valoración, opciones múltiples, observaciones cualitativas, e incluso la posibilidad de adjuntar imágenes o grabaciones cortas que documenten el desempeño del estudiante. El profesor puede optar por evaluaciones individuales detalladas o por evaluaciones grupales más ágiles donde se aplica el mismo criterio a múltiples estudiantes simultáneamente.

Una vez completada la evaluación, los resultados se almacenan en las tablas `motor_activity_responses` y `student_activities`, manteniendo un histórico completo de la evolución de cada estudiante. El sistema utiliza estos datos para generar automáticamente visualizaciones y reportes que muestran tendencias, fortalezas y áreas de oportunidad. Estos reportes están disponibles tanto para los profesores, que pueden utilizarlos para ajustar sus estrategias pedagógicas, como para los padres, que reciben información clara y contextualizada sobre el progreso de sus hijos a través de la sección correspondiente en su dashboard.

## 3. TECNOLOGÍAS UTILIZADAS

EduApp combina tecnologías modernas del ecosistema web para crear una solución robusta, ágil y escalable. La selección tecnológica prioriza herramientas con comunidades activas, documentación completa y enfoques contemporáneos de desarrollo que facilitan tanto la implementación inicial como el mantenimiento a largo plazo.

### 3.1 Frontend
- **React**: Biblioteca principal para construcción de interfaces
- **TypeScript**: Lenguaje tipado para desarrollo más robusto
- **Vite**: Herramienta de construcción y servidor de desarrollo
- **Tailwind CSS**: Framework CSS utilitario
- **shadcn/ui**: Componentes UI reutilizables
- **React Router**: Enrutamiento de la aplicación
- **React Query**: Gestión de estado del servidor y caché
- **Zod**: Validación de esquemas
- **Recharts**: Visualización de datos
- **react-hook-form**: Manejo avanzado de formularios

El frontend de EduApp se construye sobre React, aprovechando su paradigma de componentes para crear interfaces modulares y reutilizables. La adopción de TypeScript añade un sistema de tipos estático que detecta errores potenciales durante el desarrollo, mejorando significativamente la mantenibilidad del código y facilitando la colaboración en equipo. Vite proporciona un entorno de desarrollo ultrarrápido con recarga instantánea (HMR) y una configuración de construcción optimizada que genera bundles eficientes para producción.

La combinación de Tailwind CSS y shadcn/ui permite un desarrollo visual coherente y eficiente, eliminando la necesidad de escribir CSS personalizado para la mayoría de los componentes y garantizando una experiencia de usuario consistente en toda la aplicación. React Router gestiona la navegación y el enrutamiento, mientras que React Query simplifica la obtención, actualización y caching de datos del servidor, reduciendo significativamente el código boilerplate tradicionalmente asociado con estas operaciones.

Las bibliotecas complementarias como Zod para validación de esquemas, Recharts para visualizaciones de datos y react-hook-form para manejo avanzado de formularios, completan el ecosistema frontend proporcionando soluciones especializadas para necesidades específicas de la aplicación.

### 3.2 Backend (Supabase)
- **PostgreSQL**: Base de datos relacional
- **Row Level Security (RLS)**: Políticas de seguridad a nivel de fila
- **Edge Functions**: Funciones serverless para lógica personalizada
- **Storage**: Almacenamiento de archivos
- **Authentication**: Sistema de autenticación y autorización

El backend de EduApp se implementa utilizando Supabase, una plataforma de desarrollo que proporciona una alternativa open-source a soluciones como Firebase, construida sobre tecnologías robustas y estándares abiertos. PostgreSQL sirve como el motor de base de datos principal, ofreciendo un sistema relacional potente, confiable y con soporte para características avanzadas como consultas geoespaciales, búsqueda de texto completo y tipos de datos JSON nativos.

Las políticas de Row Level Security (RLS) constituyen una capa de seguridad crítica, implementando restricciones de acceso a nivel de fila que garantizan que los usuarios solo pueden ver y modificar datos para los que tienen autorización explícita, independientemente de cómo accedan a la base de datos. Estas políticas se definen de manera declarativa y se evalúan automáticamente en cada consulta, proporcionando una barrera de seguridad robusta contra accesos no autorizados.

Las Edge Functions permiten ejecutar código personalizado en la nube en respuesta a eventos específicos o solicitudes directas, extendiendo la funcionalidad más allá de las operaciones CRUD básicas. El sistema de almacenamiento (Storage) facilita la gestión de archivos como documentos, imágenes de perfil e identificaciones para los permisos de recogida, con control de acceso detallado. Finalmente, el sistema de autenticación integrado maneja todo el ciclo de vida de los usuarios, incluyendo registro, inicio de sesión, recuperación de contraseñas y gestión de sesiones.

### 3.3 Herramientas de Desarrollo
- **ESLint**: Linting de código
- **Prettier**: Formateo de código
- **Git**: Control de versiones
- **GitHub Actions**: CI/CD
- **npm**: Gestor de paquetes

El proceso de desarrollo de EduApp se apoya en un conjunto de herramientas que mejoran la productividad, la calidad del código y la colaboración. ESLint analiza estáticamente el código JavaScript/TypeScript para identificar patrones problemáticos y hacer cumplir estándares de codificación consistentes, mientras que Prettier garantiza un formato uniforme en todo el codebase, eliminando debates sobre estilos y facilitando la lectura del código.

Git proporciona control de versiones distribuido, permitiendo a los desarrolladores trabajar en paralelo en diferentes características sin interferencias, mientras mantienen la capacidad de fusionar sus cambios de manera controlada. GitHub Actions implementa un pipeline de CI/CD (Integración Continua/Entrega Continua) que automatiza pruebas, verificaciones de calidad y despliegues, garantizando que solo código validado llegue a producción. El ecosistema npm gestiona las dependencias del proyecto, facilitando la incorporación y actualización de bibliotecas externas mientras mantiene un registro detallado de las versiones utilizadas.

## 4. SEGURIDAD

La arquitectura de seguridad de EduApp implementa múltiples capas de protección para salvaguardar datos sensibles y garantizar que cada usuario tenga acceso únicamente a la información y funcionalidades pertinentes a su rol. El enfoque holístico incluye medidas en el cliente, en la transmisión de datos y en el almacenamiento y procesamiento en el servidor.

### 4.1 Autenticación y Autorización
- **Método principal**: Email/Password con Supabase Auth
- **Gestión de sesiones**: JWT con renovación automática
- **Autorización**: Basada en roles (admin, teacher, parent)
- **Protección de rutas**: Componente `ProtectedRoute` con verificación de roles

El sistema de autenticación implementa un flujo seguro basado en credenciales (email/password) con validaciones robustas que incluyen verificación de formatos, complejidad mínima de contraseñas y protección contra ataques de fuerza bruta mediante limitación de intentos. Una vez autenticado, el usuario recibe un token JWT (JSON Web Token) firmado criptográficamente que incluye su identidad y rol, con una duración limitada pero con renovación automática mientras la sesión permanezca activa.

La autorización se implementa en dos niveles complementarios: en el cliente, mediante el componente `ProtectedRoute` que verifica el rol del usuario antes de renderizar rutas protegidas, redirigiendo automáticamente a usuarios no autorizados; y en el servidor, a través de políticas RLS en la base de datos y validaciones en las Edge Functions, garantizando que incluso si se eludieran las protecciones del cliente, los datos permanecerían seguros.

### 4.2 Seguridad de Datos
- **Row Level Security (RLS)**: Políticas en todas las tablas para asegurar que los usuarios solo accedan a sus propios datos
- **Validación de datos**: Implementada tanto en el cliente (Zod) como en el servidor
- **Sanitización de entradas**: Prevención de inyección SQL y XSS
- **CORS**: Configurado para permitir solo orígenes específicos

La seguridad de datos en EduApp se centra en el principio de "defensa en profundidad", implementando múltiples capas de protección. Las políticas de Row Level Security (RLS) en la base de datos establecen reglas granulares que determinan qué registros puede ver o modificar cada usuario según su identidad y rol. Por ejemplo, los profesores solo pueden ver estudiantes asignados a ellos, y los padres únicamente pueden acceder a la información de sus propios hijos.

La validación de datos se realiza en el cliente utilizando Zod para verificar formatos, rangos y relaciones antes de enviar datos al servidor, y nuevamente en el servidor antes de cualquier operación en la base de datos. Esta redundancia protege contra intentos de eludir las validaciones del cliente. La sanitización de entradas previene vulnerabilidades comunes como inyección SQL y Cross-Site Scripting (XSS), procesando y escapando adecuadamente todos los datos proporcionados por los usuarios.

La configuración CORS (Cross-Origin Resource Sharing) restringe qué dominios pueden realizar solicitudes a las APIs de EduApp, bloqueando intentos no autorizados desde orígenes desconocidos y mitigando ataques de tipo CSRF (Cross-Site Request Forgery).

### 4.3 Almacenamiento de Credenciales
- **API Keys y tokens**: Almacenados como secretos en Supabase
- **Credenciales de acceso**: Gestionar mediante un administrador de contraseñas seguro (recomendado: Bitwarden o similar)
- **Variables de entorno**: Configuradas en Netlify para el entorno de producción

Las credenciales sensibles necesarias para la operación de EduApp, como API keys para servicios externos y tokens de acceso, se almacenan como secretos encriptados en Supabase, accesibles únicamente por las Edge Functions autorizadas durante su ejecución. Nunca se incluyen directamente en el código fuente ni se exponen al cliente.

Para el acceso administrativo a las diferentes plataformas (GitHub, Netlify, Supabase, WebIntoApp), se recomienda estrictamente el uso de un gestor de contraseñas seguro como Bitwarden, 1Password o LastPass, utilizando contraseñas únicas y robustas para cada servicio, preferiblemente con autenticación de dos factores (2FA) habilitada cuando esté disponible.

Las variables de entorno necesarias para la construcción y operación de la aplicación se configuran directamente en Netlify para el entorno de producción, manteniendo separados los valores específicos de cada entorno (desarrollo, staging, producción) y evitando la necesidad de incluir información sensible en el repositorio.

### 4.4 Seguridad en el APK
- **HTTPS obligatorio**: Comunicación cifrada
- **Certificate Pinning**: Para prevenir ataques man-in-the-middle
- **Almacenamiento seguro**: Datos sensibles almacenados con encriptación

La versión APK de EduApp implementa medidas de seguridad adicionales específicas para el entorno móvil. Todas las comunicaciones con el backend se realizan exclusivamente a través de HTTPS, con Certificate Pinning configurado para verificar la autenticidad del servidor, previniendo ataques man-in-the-middle que podrían interceptar credenciales u otros datos sensibles.

Los datos almacenados localmente en el dispositivo, como tokens de sesión, preferencias de usuario o información en caché, se guardan utilizando el sistema de almacenamiento seguro de Android (EncryptedSharedPreferences), que implementa encriptación AES para proteger la información incluso en dispositivos comprometidos. Adicionalmente, se implementan políticas de expiración y limpieza automática para datos sensibles, minimizando la ventana de vulnerabilidad en caso de pérdida o robo del dispositivo.

## 5. MANTENIMIENTO Y DESPLIEGUE

El mantenimiento y despliegue de EduApp sigue prácticas DevOps que automatizan y optimizan los procesos de integración, pruebas y publicación, garantizando actualizaciones fluidas y minimizando el tiempo de inactividad. La infraestructura utilizada permite despliegues frecuentes e incrementales con alta confiabilidad.

### 5.1 Flujo de Trabajo de Desarrollo
1. Desarrollo local con `npm run dev`
2. Pruebas unitarias con `npm run test`
3. Commit y push a GitHub
4. Despliegue automático en Netlify (rama main)

El ciclo de desarrollo comienza con el trabajo local, donde los desarrolladores utilizan el comando `npm run dev` para iniciar un servidor de desarrollo con recarga en caliente, permitiendo ver cambios inmediatamente sin necesidad de recargar manualmente. Las pruebas unitarias se ejecutan localmente con `npm run test` para validar que los cambios no rompen funcionalidades existentes. Una vez satisfecho con los cambios, el desarrollador realiza un commit en su rama de trabajo y eventualmente integra estos cambios a la rama principal a través de pull requests.

GitHub Actions ejecuta automáticamente verificaciones de calidad y pruebas en cada pull request, garantizando que solo código que cumple con los estándares establecidos pueda ser fusionado. Una vez que los cambios se integran en la rama principal, Netlify detecta automáticamente la actualización y activa un nuevo proceso de construcción y despliegue, publicando la versión actualizada en producción típicamente en menos de 5 minutos desde la integración.

### 5.2 Actualización de APK
1. Desplegar cambios a Netlify
2. Acceder a WebIntoApp con las credenciales almacenadas
3. Crear nueva versión del APK con la URL actualizada
4. Actualizar metadatos y versión si es necesario
5. Generar y distribuir el nuevo APK

Dado que la versión APK de EduApp es esencialmente un contenedor nativo para la aplicación web, el proceso de actualización es relativamente sencillo pero requiere pasos manuales. Una vez que la versión web ha sido desplegada y validada en Netlify, un administrador accede a la plataforma WebIntoApp utilizando las credenciales almacenadas en el gestor de contraseñas.

Dentro de WebIntoApp, se crea una nueva versión del APK apuntando a la URL actualizada de la aplicación. Si los cambios incluyen modificaciones significativas en la funcionalidad o interfaz, se actualiza también el número de versión y, potencialmente, los metadatos como capturas de pantalla o descripciones. El nuevo APK generado se distribuye entonces a través de los canales establecidos, que pueden incluir distribución directa a usuarios específicos para pruebas beta o publicación en plataformas de distribución privadas para acceso general.

### 5.3 Backups
- **Base de datos**: Supabase realiza copias de seguridad automáticas
- **Código**: Respaldado en GitHub
- **Configuración personalizada**: Documentada en este documento y en archivos específicos

La estrategia de respaldo de EduApp aprovecha las capacidades integradas de las plataformas utilizadas, complementadas con procedimientos específicos. Supabase realiza copias de seguridad automáticas diarias de la base de datos completa, con retención configurable para equilibrar seguridad y costes. Estas copias permiten restaurar el sistema completo o datos específicos en caso de pérdida accidental, corrupción o ataque malicioso.

El código fuente se respalda inherentemente a través del sistema de control de versiones Git en GitHub, con cada commit preservando un estado recuperable del proyecto. Para mayor seguridad, se mantienen copias locales en sistemas de los desarrolladores principales y, periódicamente, se generan archivos ZIP del repositorio completo que se almacenan en ubicaciones seguras desconectadas.

La configuración personalizada, incluyendo variables de entorno, políticas de RLS, definiciones de Edge Functions y otros parámetros que no forman parte del código versionado, se documenta meticulosamente en este documento técnico y en archivos específicos almacenados en ubicaciones seguras, permitiendo reconstruir completamente el entorno en caso necesario.

### 5.4 Monitoreo
- **Errores de Frontend**: Integración con Sentry (recomendado para una implementación futura)
- **Rendimiento del servidor**: Panel de Supabase
- **Disponibilidad**: Verificación periódica con herramientas de monitoreo

El monitoreo de EduApp combina herramientas automatizadas y revisiones manuales periódicas para garantizar el funcionamiento óptimo del sistema. Se recomienda implementar en el futuro la integración con Sentry para la captura y análisis de errores en el frontend, proporcionando visibilidad inmediata de problemas que afectan a los usuarios, contexto detallado para diagnóstico y alertas automatizadas.

El rendimiento y estado del backend se monitorea a través del panel de control de Supabase, que proporciona métricas en tiempo real sobre uso de recursos, tiempos de respuesta de consultas, errores en Edge Functions y otros indicadores clave. Adicionalmente, se realizan verificaciones periódicas de disponibilidad utilizando herramientas externas que simulan acceso de usuarios desde diferentes ubicaciones geográficas, midiendo tiempos de respuesta y detectando interrupciones parciales o totales del servicio.

## 6. DESARROLLO FUTURO

La hoja de ruta de EduApp contempla mejoras iterativas que expandirán funcionalidades, optimizarán el rendimiento y mejorarán la experiencia de usuario, manteniendo siempre la coherencia con la misión educativa de la plataforma. Las prioridades se establecen considerando feedback de usuarios reales y tendencias en tecnología educativa.

### 6.1 Mejoras Planeadas
- Implementación de notificaciones push
- Integración con sistemas de videoconferencia
- Módulo de reportes académicos avanzados
- Sistema de comunicación directa entre padres y profesores
- Mejoras en la visualización de datos de desarrollo motriz

Entre las mejoras planeadas para futuras versiones, destaca la implementación de notificaciones push tanto en la versión web (mediante Web Push API) como en la aplicación móvil (utilizando Firebase Cloud Messaging). Esta característica permitirá alertas en tiempo real sobre eventos importantes como registro de ausencias, aprobación de permisos o publicación de nuevos reportes de desarrollo, mejorando significativamente la comunicación con los usuarios incluso cuando no están utilizando activamente la aplicación.

La integración con sistemas de videoconferencia busca facilitar reuniones virtuales entre docentes y padres, especialmente relevantes en contextos de educación híbrida o para familias con dificultades para asistir presencialmente. El módulo de reportes académicos avanzados expandirá las capacidades analíticas de la plataforma, proporcionando visualizaciones personalizables y insights basados en inteligencia artificial que ayudarán a identificar patrones y áreas de oportunidad en el desarrollo de los estudiantes.

El sistema de comunicación directa entre padres y profesores establecerá canales seguros y organizados para intercambiar mensajes relacionados con el progreso educativo de los estudiantes, manteniendo un registro centralizado de todas las interacciones. Finalmente, las mejoras en visualización de datos de desarrollo motriz implementarán gráficos interactivos y comparativos que facilitarán la comprensión de la evolución individual y grupal.

### 6.2 Escalabilidad
- La arquitectura actual permite escalar horizontalmente
- Supabase puede manejar un aumento significativo en usuarios
- Consideraciones para escalar:
  - Optimización de consultas a base de datos
  - Implementación de estrategias de caché adicionales
  - Separación de servicios críticos si es necesario

EduApp ha sido diseñada desde sus cimientos pensando en la escalabilidad, implementando una arquitectura que puede adaptarse tanto a un crecimiento orgánico gradual como a expansiones rápidas del usuario base. En el frontend, la aplicación utiliza lazy loading y code splitting para cargar únicamente el código necesario según la ruta actual, reduciendo el tiempo de carga inicial y optimizando el uso de recursos del cliente. React Query implementa estrategias de caché inteligentes que minimizan las solicitudes al servidor y mejoran la experiencia de usuario en condiciones de red subóptimas.

En el backend, Supabase proporciona una infraestructura elastic que puede escalar automáticamente según la demanda, con capacidad para manejar desde unos pocos usuarios concurrentes hasta miles simultáneos. Para prepararse para un crecimiento sustancial, se recomienda implementar optimizaciones adicionales como índices específicos en tablas de uso frecuente, consultas denormalizadas para operaciones críticas de lectura y estrategias de caché distribuidas para datos relativamente estáticos.

Si el crecimiento eventualmente supera las capacidades de la arquitectura actual, el diseño modular permitiría una transición gradual hacia una arquitectura de microservicios, separando funcionalidades críticas en servicios independientes que podrían escalarse individualmente según sus requisitos específicos.

## 7. RESOLUCIÓN DE PROBLEMAS COMUNES

Esta sección proporciona guías para diagnosticar y resolver problemas recurrentes que pueden surgir durante la operación o mantenimiento de EduApp. Las soluciones se basan en experiencias reales y están diseñadas para minimizar el tiempo de inactividad y facilitar la resolución rápida de incidencias.

### 7.1 Errores de Autenticación
- Verificar estado de la sesión en el almacenamiento local
- Comprobar políticas RLS en Supabase
- Revisar logs de autenticación en el panel de Supabase

Los problemas relacionados con autenticación típicamente se manifiestan como redirecciones inesperadas a la página de login, acceso denegado a recursos específicos o errores al intentar realizar acciones que requieren permisos. El primer paso para diagnosticar estos problemas es examinar el estado de la sesión en el almacenamiento local del navegador, verificando la existencia y validez del token JWT. Si el token aparenta ser válido pero persisten los problemas, es recomendable comprobar las políticas RLS en Supabase, asegurando que estén correctamente configuradas para permitir las operaciones deseadas según el rol del usuario.

Los logs de autenticación en el panel de Supabase proporcionan información detallada sobre intentos de inicio de sesión, renovaciones de token y operaciones fallidas, ayudando a identificar patrones específicos o errores recurrentes. En casos donde un usuario específico experimenta problemas persistentes, puede ser necesario regenerar su sesión o, en casos extremos, restablecer su contraseña para forzar una renovación completa de credenciales.

### 7.2 Problemas de Despliegue
- Revisar logs de construcción en Netlify
- Verificar variables de entorno configuradas
- Comprobar compatibilidad de dependencias

Los fallos en el proceso de despliegue automático suelen estar relacionados con errores durante la fase de construcción, configuraciones incorrectas o incompatibilidades entre dependencias. Los logs detallados de construcción disponibles en el panel de Netlify son el primer recurso para diagnosticar estos problemas, proporcionando información precisa sobre qué fase del proceso falló y los errores específicos encontrados.

Es crucial verificar que todas las variables de entorno requeridas estén correctamente configuradas en Netlify, especialmente tras actualizaciones que introducen nuevas dependencias de servicios externos. Las discrepancias entre variables de entorno locales y las configuradas en el servidor de despliegue son una causa común de problemas que funcionan correctamente en desarrollo pero fallan en producción.

La compatibilidad entre dependencias debe revisarse periódicamente, especialmente al actualizar bibliotecas o frameworks importantes. El archivo package-lock.json (o equivalente) debe versionarse para garantizar que todos los entornos utilicen exactamente las mismas versiones de dependencias, evitando comportamientos inconsistentes.

### 7.3 Errores en el APK
- Validar que la URL base es correcta
- Comprobar permisos solicitados
- Verificar configuración de WebView

Los problemas específicos de la versión APK generalmente están relacionados con la configuración del WebView que renderiza la aplicación web dentro del contenedor nativo. Es fundamental validar que la URL base configurada en WebIntoApp sea exactamente la URL correcta de producción, incluyendo el protocolo HTTPS y cualquier subdominio relevante.

Los permisos solicitados en el manifiesto de la aplicación deben revisarse para asegurar que incluyen todos los necesarios para la funcionalidad completa (almacenamiento, cámara, notificaciones) sin solicitar permisos excesivos que podrían generar desconfianza en los usuarios o ser rechazados por las tiendas de aplicaciones.

La configuración del WebView debe optimizarse para permitir JavaScript, almacenamiento local, cookies y otras tecnologías web requeridas por la aplicación, mientras se mantienen configuraciones de seguridad adecuadas como la restricción de acceso a archivos del sistema o la ejecución de código arbitrario.

## 8. INTEGRACIÓN DE APIS DE INTELIGENCIA ARTIFICIAL

EduApp incorpora tecnologías de inteligencia artificial avanzada a través de integraciones con las APIs de OpenAI y Perplexity, aprovechando el potencial de estos modelos para mejorar la experiencia educativa tanto para docentes como para estudiantes. Estas integraciones están diseñadas con un enfoque cuidadoso en la privacidad de los datos, la eficiencia computacional y la generación de valor pedagógico real.

### 8.1 OpenAI API
- **Ubicación en el proyecto:** `supabase/functions/generate_motor_analysis/index.ts`
- **Propósito:** Análisis avanzado de reportes de desarrollo motriz
- **Detalles de implementación:**
  - **Método de autenticación:** API Key almacenada en secretos de Supabase Edge Functions
  - **Modelo utilizado:** gpt-4o-mini
  - **Endpoints utilizados:** `https://api.openai.com/v1/chat/completions`
  - **Formato de solicitud:**
    ```javascript
    {
      model: 'gpt-4o-mini',
      messages: [
        { role: 'system', content: 'Instrucciones del sistema' },
        { role: 'user', content: 'Prompt con datos a analizar' }
      ],
      temperature: 0.2,
      max_tokens: 2048
    }
    ```
  - **Configuración adicional:**
    - Temperature: 0.2 (baja para mayor precisión en análisis educativos)
    - Max tokens: 2048 (suficiente para análisis detallados)

La integración con OpenAI se implementa principalmente a través de la Edge Function `generate_motor_analysis`, que procesa los datos recopilados sobre el desarrollo motriz de los estudiantes y genera análisis comprensivos, identificando patrones, fortalezas y áreas de oportunidad. Esta funcionalidad aprovecha la capacidad de los modelos GPT para interpretar datos complejos y generar insights detallados en lenguaje natural, adaptados al contexto educativo específico de preescolar.

El proceso comienza cuando un docente solicita un análisis desde la interfaz de usuario. La aplicación recopila todos los datos relevantes de evaluaciones previas y los estructura en un formato optimizado para el procesamiento por IA. Esta información se envía a la Edge Function, que construye un prompt especializado con instrucciones detalladas sobre cómo interpretar los datos y qué tipo de análisis generar. La función se comunica con la API de OpenAI utilizando la clave almacenada de forma segura como secreto en Supabase, garantizando que esta credencial nunca se exponga en el frontend.

Los prompts están cuidadosamente diseñados para maximizar la calidad y relevancia de los análisis, incluyendo contexto específico sobre desarrollo infantil, hitos apropiados para cada edad y terminología pedagógica precisa. La configuración de temperatura baja (0.2) prioriza respuestas coherentes y fundamentadas sobre creatividad, asegurando que el análisis sea confiable y basado en los datos proporcionados.

#### 8.1.1 Proceso de Cambio de Configuración OpenAI
1. **Cambio de API Key:**
   - Acceder al panel de Supabase: https://supabase.com/dashboard/project/mucdwmcxdaosxivkowfq/settings/functions
   - Editar el secreto `OPENAI_API_KEY` con el nuevo valor
   - No es necesario redesplegar las funciones, se actualizan automáticamente

2. **Cambio de Modelos:**
   - Editar el archivo `supabase/functions/generate_motor_analysis/index.ts`
   - Modificar la propiedad `model` en la llamada a la API
   - Validar compatibilidad del prompt con el nuevo modelo
   - Desplegar cambios mediante push a GitHub

3. **Ajuste de Parámetros:**
   - Para ajustar temperature, tokens, etc., modificar los parámetros en la llamada API
   - Probar en un entorno de desarrollo antes de desplegar a producción
   - Actualizar la documentación con los nuevos valores

4. **Monitoreo y Cuotas:**
   - Supervisar uso de tokens en el panel de OpenAI: https://platform.openai.com/usage
   - Establecer límites de gasto para evitar cargos inesperados
   - Implementar mecanismos de caché para reducir llamadas redundantes

La gestión de la integración con OpenAI incluye procedimientos claros para realizar cambios en la configuración, garantizando que las actualizaciones se implementen de manera segura y eficiente. El cambio de la API Key es un proceso simple que se realiza directamente en el panel de administración de Supabase, donde las claves se almacenan como secretos encriptados accesibles únicamente por las Edge Functions autorizadas. Esta operación no requiere redespliegue, ya que las funciones acceden dinámicamente a los secretos en tiempo de ejecución.

Para cambios más sustanciales como la actualización del modelo utilizado, es necesario modificar directamente el código de la función `generate_motor_analysis`. Es crucial validar que los prompts existentes sean compatibles con el nuevo modelo, ya que diferentes versiones pueden tener capacidades variadas o requerir estructuras de prompt específicas para resultados óptimos. Estos cambios deben probarse exhaustivamente en un entorno de desarrollo antes de desplegarse a producción mediante un push al repositorio principal.

El monitoreo regular del uso de tokens a través del panel de OpenAI es fundamental para controlar costes y detectar patrones anómalos que podrían indicar uso ineficiente o problemas en la implementación. Se recomienda establecer límites de gasto y alertas para prevenir cargos excesivos, especialmente durante fases de mayor actividad como fin de semestre o períodos de evaluación.

### 8.2 Perplexity API
- **Ubicación en el proyecto:** 
  - `supabase/functions/get_ai_suggestion/index.ts`
  - `supabase/functions/search_institutions/perplexity.ts`
- **Propósito:** 
  - Generación de sugerencias para actividades educativas
  - Búsqueda inteligente de instituciones educativas
- **Detalles de implementación:**
  - **Método de autenticación:** API Key almacenada en secretos de Supabase Edge Functions
  - **Modelo utilizado:** llama-3.1-sonar-small-128k-online
  - **Endpoints utilizados:** `https://api.perplexity.ai/chat/completions`
  - **Formato de solicitud:**
    ```javascript
    {
      model: 'llama-3.1-sonar-small-128k-online',
      messages: [
        { role: 'system', content: 'Instrucciones del sistema' },
        { role: 'user', content: 'Prompt del usuario' }
      ],
      temperature: 0.2,
      max_tokens: 1000,
      return_images: false,
      return_related_questions: false
    }
    ```
  - **Configuración adicional:**
    - Temperature: 0.2 (baja para respuestas consistentes y precisas)
    - Manejo especial de respuestas en formato JSON para instituciones educativas

La integración con Perplexity API se implementa en dos áreas clave de EduApp. En primer lugar, la función `get_ai_suggestion` proporciona a los docentes sugerencias contextualizadas de actividades educativas basadas en objetivos pedagógicos específicos, edad de los estudiantes y recursos disponibles. Esta capacidad ayuda a diversificar las estrategias didácticas y adaptar la enseñanza a las necesidades particulares del grupo.

La segunda implementación, en `search_institutions/perplexity.ts`, ofrece una búsqueda inteligente de instituciones educativas que va más allá de simples coincidencias textuales, incorporando comprensión contextual de ubicaciones geográficas, tipos de instituciones y características educativas. Esta funcionalidad es especialmente valiosa durante el proceso de registro, ayudando a los usuarios a encontrar y seleccionar correctamente su institución educativa.

La elección del modelo llama-3.1-sonar-small-128k-online representa un equilibrio óptimo entre capacidad de procesamiento y eficiencia, ofreciendo respuestas de alta calidad con tiempos de respuesta rápidos y costos operativos razonables. La configuración de temperature baja garantiza respuestas consistentes y orientadas a hechos, priorizando la precisión informativa sobre variaciones creativas.

En el caso específico de la búsqueda de instituciones, se implementa un manejo especializado para las respuestas, transformando el texto generado en estructuras JSON bien formadas que la aplicación puede procesar directamente. Este enfoque combina la flexibilidad de la generación en lenguaje natural con la estructuración necesaria para la integración técnica.

#### 8.2.1 Proceso de Cambio de Configuración Perplexity
1. **Cambio de API Key:**
   - Acceder al panel de Supabase: https://supabase.com/dashboard/project/mucdwmcxdaosxivkowfq/settings/functions
   - Editar el secreto `PERPLEXITY_API_KEY` con el nuevo valor
   - Verificar que todas las funciones relevantes tengan acceso al secreto

2. **Cambio de Modelos:**
   - Editar los archivos `supabase/functions/get_ai_suggestion/index.ts` y `supabase/functions/search_institutions/perplexity.ts`
   - Modificar la propiedad `model` en las llamadas a la API
   - Consultar la documentación de Perplexity para modelos disponibles y compatibles
   - Validar que los prompts sean compatibles con el nuevo modelo

3. **Ajuste de Parámetros:**
   - Para modificar temperature, tokens u otros parámetros, actualizar los valores en las llamadas API
   - Implementar pruebas de calidad de respuesta con los nuevos parámetros antes de desplegar

4. **Manejo de Errores:**
   - Verificar que los mecanismos de recuperación ante fallos sigan funcionando con los cambios
   - Actualizar los mecanismos de fallback si es necesario
   - Asegurar que el sistema de caché de respuestas funcione correctamente

El proceso de actualización de la configuración de Perplexity sigue protocolos similares a los de OpenAI, pero con consideraciones específicas para las particularidades de esta API. La actualización de la clave API se realiza en el panel de Supabase, pero es crucial verificar que todas las funciones relevantes tengan explícitamente configurado el acceso a este secreto, ya que Perplexity se utiliza en múltiples puntos de la aplicación y un permiso faltante podría causar fallos parciales.

Al cambiar entre modelos de Perplexity, es importante consultar la documentación actualizada del proveedor, ya que su catálogo de modelos evoluciona regularmente con nuevas capacidades y características. Los prompts existentes pueden requerir ajustes para aprovechar al máximo las capacidades específicas de cada modelo o para adaptarse a sus particularidades.

El sistema implementa mecanismos robustos de manejo de errores y recuperación ante fallos para todas las interacciones con Perplexity, incluyendo reintentos automáticos con backoff exponencial para errores transitorios, degradación elegante a respuestas predeterminadas cuando no es posible obtener una generación de IA, y sistemas de caché que almacenan respuestas para consultas frecuentes, reduciendo tanto la latencia como los costos operativos.

### 8.3 Integración con Componentes Frontend
- **Componentes que utilizan OpenAI:**
  - `src/pages/teacher/motor-skills/hooks/analysis/useAIAnalysis.ts`
  - `src/components/motor-skills/hooks/useAISuggestions.ts`

- **Componentes que utilizan Perplexity:**
  - `src/pages/teacher/motor-skills/hooks/reports/useAISuggestions.ts`
  - `src/components/motor-skills/AIAssistant.tsx`

La integración de las capacidades de IA con la interfaz de usuario se implementa principalmente a través de hooks personalizados y componentes especializados que encapsulan la lógica de comunicación con las Edge Functions. Esta arquitectura proporciona una clara separación de responsabilidades: los componentes de UI se centran en la presentación y la experiencia de usuario, mientras que los hooks gestionan el estado, las solicitudes a las APIs y el procesamiento de respuestas.

El hook `useAIAnalysis` facilita el análisis automatizado de datos de desarrollo motriz, invocando la Edge Function correspondiente y procesando los resultados para presentarlos de manera coherente en la interfaz de usuario. Incluye gestión de estados de carga, manejo de errores y formateo de los análisis generados para su presentación visual.

El componente `AIAssistant` proporciona una interfaz interactiva donde los docentes pueden solicitar sugerencias específicas para actividades educativas, presentando las respuestas generadas en un formato estructurado y accionable. Este componente implementa técnicas de UX como estados de carga animados y visualización progresiva para mantener una experiencia fluida incluso cuando las respuestas de la API pueden tomar algunos segundos.

En conjunto, estas integraciones frontend están diseñadas para hacer que la tecnología de IA sea accesible y útil para usuarios sin conocimientos técnicos, ocultando la complejidad subyacente y presentando los resultados en formatos pedagógicamente relevantes que pueden aplicarse directamente en el contexto educativo.

### 8.4 Buenas Prácticas Implementadas
- **Seguridad:**
  - API Keys almacenadas exclusivamente como secretos de Supabase
  - Sin exposición de credenciales en el frontend
  - Validación de entradas antes de enviar a las APIs

- **Rendimiento:**
  - Caché de resultados para consultas frecuentes
  - Límite de tokens para optimizar costos
  - Mecanismos de fallback para garantizar disponibilidad

- **UX:**
  - Estados de carga durante peticiones
  - Manejo elegante de errores
  - Presentación optimizada de resultados

La implementación de las integraciones de IA en EduApp sigue un conjunto riguroso de buenas prácticas que equilibran seguridad, rendimiento y experiencia de usuario. En términos de seguridad, todas las credenciales de API se almacenan exclusivamente como secretos encriptados en Supabase, accesibles únicamente por las Edge Functions autorizadas, eliminando cualquier riesgo de exposición en el frontend o en el código fuente. Adicionalmente, todas las entradas de usuario se validan y sanitizan antes de incluirse en prompts enviados a las APIs de IA, previniendo posibles vectores de ataque como inyecciones de prompt o manipulaciones maliciosas.

Para optimizar el rendimiento y controlar costos, se implementan estrategias de caché que almacenan resultados para consultas frecuentes o similares, reduciendo significativamente el número de llamadas a APIs externas. Los límites de tokens se ajustan cuidadosamente para cada tipo de solicitud, asegurando respuestas completas sin desperdiciar recursos en generaciones innecesariamente extensas. Los mecanismos de fallback garantizan que la aplicación permanezca funcional incluso cuando los servicios de IA no están disponibles, degradando elegantemente a alternativas predefinidas o alertando al usuario sobre la situación.

La experiencia de usuario durante interacciones con IA está cuidadosamente diseñada para mantener la sensación de fluidez y responsividad a pesar de la naturaleza asincrónica de estas operaciones. Los estados de carga utilizan animaciones sutiles que proporcionan feedback visual sin resultar intrusivos. El manejo de errores incluye mensajes comprensibles y sugerencias de acción cuando algo falla. La presentación de resultados está optimizada para cada caso de uso específico, con formatos visuales adaptados al tipo de información y contexto educativo.

### 8.5 Monitoreo y Gestión de Costes
- **Panel de uso OpenAI:** https://platform.openai.com/usage
- **Panel de uso Perplexity:** https://www.perplexity.ai/settings/api
- **Estrategias implementadas:**
  - Almacenamiento en caché de respuestas frecuentes
  - Agrupación de solicitudes cuando es posible
  - Límites de uso configurables por rol de usuario

El monitoreo y control de costos es un aspecto crítico en la implementación de tecnologías de IA, especialmente en un contexto educativo donde los presupuestos suelen ser limitados. EduApp implementa un enfoque proactivo mediante el seguimiento regular de los paneles de uso de OpenAI y Perplexity, que proporcionan visibilidad detallada sobre el consumo de tokens, costos asociados y patrones de uso.

El sistema de caché implementado reduce significativamente los costos al almacenar respuestas para consultas frecuentes o muy similares, evitando regenerar contenido prácticamente idéntico. Por ejemplo, las sugerencias de actividades para objetivos pedagógicos comunes o los análisis de patrones típicos de desarrollo se almacenan y reutilizan cuando es apropiado, refrescándose periódicamente para mantener la relevancia.

La agrupación de solicitudes optimiza aún más el uso de recursos, combinando múltiples consultas relacionadas en una sola llamada a la API cuando es posible. Por ejemplo, al generar análisis de desarrollo para un grupo de estudiantes, el sistema puede estructurar la solicitud para procesar múltiples perfiles en una sola llamada, en lugar de realizar solicitudes individuales para cada estudiante.

Los límites de uso configurables basados en roles garantizan una distribución equitativa y controlada de los recursos de IA. Los administradores pueden establecer cuotas diferenciadas según el rol del usuario (profesor, coordinador, director), ajustando dinámicamente estos límites según las necesidades y presupuesto disponible. Este enfoque garantiza que las capacidades de IA estén disponibles cuando realmente añaden valor pedagógico, mientras se previene el uso excesivo o innecesario que podría generar costos desproporcionados.

## 9. CONTACTO Y SOPORTE

- **Responsable técnico principal**: [Información de contacto]
- **Repositorio de documentación adicional**: [URL del repositorio interno]
- **Canal de comunicación para incidencias**: [Correo/Plataforma]

---

**NOTA IMPORTANTE**: Este documento contiene información confidencial del proyecto EduApp. No debe ser compartido fuera del equipo de desarrollo autorizado. Las credenciales reales deben almacenarse en un gestor de contraseñas seguro y no incluirse en esta documentación.
