
# MANUAL TÉCNICO DEL SISTEMA EDUAPP

<img src="https://silly-banoffee-6e8cac.netlify.app/lovable-uploads/bd094bea-a8f4-4bc7-b320-bbcb1ca4f552.png" alt="Logo EduApp" width="200"/>

**INGENIERÍA DE SOFTWARE**

**Versión:** 1.0  
**Fecha:** 21 de mayo de 2025  
**Equipo de Desarrollo:** Equipo EduApp

## ÍNDICE

1. [Presentación](#presentación)
2. [Resumen](#resumen)
3. [Palabras clave](#palabras-clave)
4. [Objetivo](#objetivo)
5. [Introducción](#introducción)
6. [Requerimientos técnicos](#requerimientos-técnicos)
   - [Requerimientos mínimos de hardware](#requerimientos-mínimos-de-hardware)
   - [Requerimientos mínimos de software](#requerimientos-mínimos-de-software)
7. [Aspectos técnicos](#aspectos-técnicos)
   - [Tecnologías y herramientas utilizadas](#tecnologías-y-herramientas-utilizadas)
   - [Arquitectura del sistema](#arquitectura-del-sistema)
8. [Diagramas de modelamiento](#diagramas-de-modelamiento)
   - [Diagramas de casos de uso](#diagramas-de-casos-de-uso)
   - [Modelo Entidad-Relación](#modelo-entidad-relación)
   - [Diagrama de clases](#diagrama-de-clases)
   - [Diagrama de Base de Datos](#diagrama-de-base-de-datos)
   - [Diccionario de datos](#diccionario-de-datos)
   - [Prototipos de la aplicación](#prototipos-de-la-aplicación)
9. [Estructura del proyecto](#estructura-del-proyecto)
   - [Organización de directorios](#organización-de-directorios)
   - [Componentes principales](#componentes-principales)
10. [Componentes principales](#componentes-principales)
    - [Módulo de autenticación](#módulo-de-autenticación)
    - [Módulo de asistencia](#módulo-de-asistencia)
    - [Módulo de permisos de recogida](#módulo-de-permisos-de-recogida)
    - [Módulo de reportes de desarrollo motriz](#módulo-de-reportes-de-desarrollo-motriz)
    - [Módulo de gestión de usuarios](#módulo-de-gestión-de-usuarios)
11. [Integración con APIs externas](#integración-con-apis-externas)
    - [Configuración de API OpenAI](#configuración-de-api-openai)
    - [Configuración de API Perplexity](#configuración-de-api-perplexity)
12. [Optimización y rendimiento](#optimización-y-rendimiento)
    - [Estrategias de optimización implementadas](#estrategias-de-optimización-implementadas)
    - [Consideraciones de rendimiento](#consideraciones-de-rendimiento)
13. [Proceso de despliegue](#proceso-de-despliegue)
    - [Despliegue en entorno de desarrollo](#despliegue-en-entorno-de-desarrollo)
    - [Despliegue en entorno de producción](#despliegue-en-entorno-de-producción)
14. [Seguridad implementada](#seguridad-implementada)
    - [Prácticas de seguridad aplicadas](#prácticas-de-seguridad-aplicadas)
    - [Medidas de protección de datos](#medidas-de-protección-de-datos)
15. [Guía de mantenimiento](#guía-de-mantenimiento)
    - [Procedimientos de actualización](#procedimientos-de-actualización)
    - [Solución a problemas comunes](#solución-a-problemas-comunes)
16. [Referencias bibliográficas](#referencias-bibliográficas)

---

## Presentación

El presente manual técnico documenta en detalle la implementación y estructura del sistema EduApp, una aplicación web y móvil diseñada para facilitar la gestión escolar en instituciones de educación preescolar. Este documento está dirigido a desarrolladores, administradores de sistemas y personal técnico involucrado en el mantenimiento, extensión o modificación del sistema.

## Resumen

EduApp es un sistema de gestión escolar integral desarrollado utilizando tecnologías modernas como React, TypeScript, Supabase y servicios de inteligencia artificial. La aplicación proporciona funcionalidades críticas para la administración educativa, incluyendo registro de asistencia, seguimiento del desarrollo motriz de los estudiantes, gestión de permisos de recogida, y administración de usuarios con diferentes roles (administradores, docentes y padres). Este manual técnico detalla la arquitectura, componentes, flujos de datos, y consideraciones técnicas necesarias para comprender el funcionamiento del sistema a nivel de implementación.

## Palabras clave

Gestión escolar, React, TypeScript, Supabase, PostgreSQL, Autenticación, Row-Level Security, API REST, Desarrollo motriz, Integración de IA, PWA, Responsive Design, Arquitectura de componentes.

## Objetivo

El objetivo principal de este manual técnico es proporcionar una documentación completa y detallada de los aspectos técnicos de EduApp, facilitando su mantenimiento, actualización y extensión. Se busca ofrecer una guía clara para desarrolladores que necesiten trabajar con el código del sistema, administradores que requieran configurar o desplegar la aplicación, y cualquier otro personal técnico involucrado en el ciclo de vida del software.

## Introducción

EduApp surge como respuesta a la necesidad de digitalizar y optimizar los procesos administrativos y pedagógicos en instituciones de educación preescolar. La aplicación está diseñada siguiendo principios de usabilidad, seguridad, y escalabilidad, con un enfoque centrado en las necesidades específicas de docentes, administradores y padres de familia.

El sistema implementa una arquitectura moderna basada en componentes, utilizando React como librería principal para el desarrollo del frontend, complementado con TypeScript para proporcionar tipado estático y mejorar la robustez del código. Para el backend, se utiliza Supabase, una plataforma de desarrollo que proporciona una base de datos PostgreSQL, autenticación, almacenamiento de archivos, y funciones serverless.

La aplicación se estructura en módulos funcionales claramente separados, cada uno con responsabilidades específicas:

- **Módulo de autenticación**: Gestiona el acceso seguro al sistema mediante credenciales, con soporte para múltiples roles de usuario.
- **Módulo de asistencia**: Facilita el registro y seguimiento de la asistencia diaria de estudiantes.
- **Módulo de permisos de recogida**: Permite a los padres solicitar autorizaciones para que terceros recojan a sus hijos, incluyendo gestión de documentos de identificación.
- **Módulo de reportes de desarrollo motriz**: Proporciona herramientas para evaluar y realizar seguimiento del desarrollo motriz de los estudiantes, con integración de inteligencia artificial para análisis y recomendaciones.
- **Módulo de gestión de usuarios**: Administra los diferentes roles y permisos dentro del sistema.

Este manual técnico detalla cada uno de estos módulos, así como las tecnologías, arquitectura, y mejores prácticas implementadas en el desarrollo de EduApp.

## Requerimientos técnicos

### Requerimientos mínimos de hardware

Para garantizar un funcionamiento óptimo de EduApp, se recomiendan los siguientes requerimientos mínimos de hardware:

**Para servidores de producción:**
- **CPU**: 2 núcleos, 2.0 GHz o superior
- **RAM**: 4 GB mínimo, 8 GB recomendado
- **Almacenamiento**: 20 GB de espacio disponible (SSD recomendado para mejor rendimiento)
- **Conexión a Internet**: Banda ancha estable con 10 Mbps mínimos

**Para equipos de desarrollo:**
- **CPU**: Intel Core i5 o equivalente (6ª generación o superior)
- **RAM**: 8 GB mínimo, 16 GB recomendado para entornos de desarrollo
- **Almacenamiento**: 40 GB de espacio disponible (SSD recomendado)
- **Pantalla**: Resolución mínima de 1366x768, recomendado 1920x1080
- **Conexión a Internet**: 5 Mbps mínimo

**Para usuarios finales (acceso web):**
- **CPU**: Procesador dual-core o superior
- **RAM**: 4 GB mínimo
- **Navegadores compatibles**: Chrome (versión 90+), Firefox (versión 88+), Safari (versión 14+), Edge (versión 90+)
- **Conexión a Internet**: 2 Mbps mínimo

**Para usuarios móviles (aplicación PWA/APK):**
- **Sistema operativo**: Android 8.0+ o iOS 13+
- **RAM**: 2 GB mínimo
- **Almacenamiento disponible**: 100 MB mínimo
- **Conexión a Internet**: Conectividad móvil 3G o superior, WiFi recomendado

Las especificaciones de hardware recomendadas aseguran un rendimiento fluido del sistema tanto en entornos de desarrollo como en producción. Para un rendimiento óptimo en situaciones de uso intensivo, se recomienda incrementar las especificaciones, especialmente en términos de RAM y capacidad de procesamiento.

### Requerimientos mínimos de software

#### Entorno de desarrollo:
- **Sistema operativo**: Windows 10/11, macOS 12+, o Linux (Ubuntu 20.04 LTS o superior)
- **Node.js**: Versión 18.0.0 o superior
- **npm**: Versión 8.0.0 o superior (incluido con Node.js)
- **Git**: Versión 2.30.0 o superior
- **Editor de código**: Visual Studio Code (recomendado), WebStorm, o similar
- **Navegadores para pruebas**: Google Chrome, Mozilla Firefox, Safari, Microsoft Edge

#### Entorno de producción:
- **Plataforma de hosting**: Netlify, Vercel, o cualquier servicio que soporte aplicaciones React/SPA
- **Backend as a Service**: Supabase (vinculado al proyecto)
- **Servicios de nube**: Cuenta en Supabase para base de datos, autenticación y almacenamiento
- **Dominios y SSL**: Dominio personalizado con certificados SSL configurados

#### Dependencias principales:
- **React**: v18.3.1
- **TypeScript**: v5.0.0 o superior
- **Vite**: Para compilación y empaquetado
- **Supabase JS Client**: v2.49.4
- **React Router DOM**: v6.26.2
- **Tanstack React Query**: v5.56.2
- **Shadcn/UI**: Componentes de interfaz prediseñados
- **Tailwind CSS**: Framework de utilidades CSS
- **JSPDF**: v3.0.1 para generación de documentos PDF
- **Zod**: v3.23.8 para validación de esquemas
- **Framer Motion**: v12.6.0 para animaciones

La combinación de estas tecnologías y herramientas forma un ecosistema robusto para el desarrollo y despliegue de EduApp. Las versiones específicas de cada dependencia están definidas en el archivo `package.json` del proyecto, garantizando la compatibilidad entre componentes y una base estable para el desarrollo.

## Aspectos técnicos

### Tecnologías y herramientas utilizadas

#### React y TypeScript

EduApp utiliza React v18.3.1 como biblioteca principal para la construcción de interfaces de usuario. La elección de React se basa en su rendimiento, flexibilidad y su amplio ecosistema de herramientas y bibliotecas complementarias. Para mejorar la calidad y mantenibilidad del código, se implementa TypeScript, que proporciona un sistema de tipos estáticos que permite detectar errores en tiempo de compilación y mejora la documentación del código.

```typescript
// Ejemplo de componente React con TypeScript
interface StudentRowProps {
  student: Student;
  options: string[];
  selectedOption: Record<string, string>;
  handleOptionSelect: (studentId: string, option: string) => void;
  isMobile: boolean;
}

const StudentRow = ({
  student,
  options,
  selectedOption,
  handleOptionSelect,
  isMobile
}: StudentRowProps) => {
  // Implementación del componente
};
```

El uso de TypeScript ha sido fundamental para mantener un código robusto y escalable, especialmente en un proyecto con múltiples desarrolladores. Las interfaces bien definidas y el tipado estricto han reducido significativamente los errores de tiempo de ejecución y han facilitado el proceso de refactorización.

#### Supabase

Supabase funciona como el backend principal de EduApp, proporcionando servicios esenciales:

- **Base de datos PostgreSQL**: Almacenamiento estructurado de datos con soporte para relaciones complejas y consultas avanzadas.
- **Autenticación y autorización**: Manejo seguro de usuarios y sesiones con diferentes roles y permisos.
- **Almacenamiento de archivos**: Gestión de documentos, imágenes y otros archivos vinculados a la aplicación.
- **Funciones Serverless (Edge Functions)**: Ejecución de lógica en el servidor para operaciones complejas o integración con servicios externos.

La implementación de Supabase en EduApp aprovecha el potente sistema de Row-Level Security (RLS) de PostgreSQL para garantizar que los datos solo sean accesibles por los usuarios autorizados:

```typescript
// Ejemplo de cliente Supabase configurado
export const supabase = createClient<Database>(SUPABASE_URL, SUPABASE_PUBLISHABLE_KEY, {
  auth: {
    persistSession: true,
    autoRefreshToken: true,
    storage: localStorage
  },
  global: {
    headers: {
      'Content-Type': 'application/json',
      'Accept-Profile': 'public',
      'apikey': SUPABASE_PUBLISHABLE_KEY
    }
  }
});
```

#### Vite

EduApp utiliza Vite como herramienta de compilación y desarrollo, proporcionando un entorno de desarrollo rápido con recarga en caliente (HMR) y una configuración simplificada. Vite ofrece tiempos de compilación significativamente más rápidos que otras herramientas como Create React App, lo que agiliza el ciclo de desarrollo.

#### Tailwind CSS y Shadcn/UI

Para el diseño de la interfaz de usuario, EduApp combina:

- **Tailwind CSS**: Framework de utilidades CSS que permite un desarrollo rápido y consistente mediante clases predefinidas.
- **Shadcn/UI**: Biblioteca de componentes basada en Radix UI que proporciona elementos de interfaz accesibles y personalizables.

Esta combinación permite crear interfaces consistentes, accesibles y visualmente atractivas con un mínimo de código personalizado:

```jsx
<Button 
  className="w-full bg-emerald-400 hover:bg-emerald-500 transition-all duration-300 hover:scale-[1.02] text-black"
  disabled={isSubmitting}
>
  <UserPlus className="mr-2 h-4 w-4" />
  {isSubmitting ? "Agregando..." : "Agregar Estudiante"}
</Button>
```

#### React Query

Para la gestión del estado del servidor y las operaciones de datos, EduApp utiliza Tanstack Query (anteriormente React Query), que proporciona:

- Caché optimizada de datos
- Revalidación en segundo plano
- Manejo de estados de carga y error
- Mutaciones de datos con actualizaciones optimistas

Esto permite mantener la interfaz de usuario sincronizada con los datos del servidor de manera eficiente, mejorando la experiencia del usuario y reduciendo la carga en el servidor.

#### Herramientas de desarrollo

El desarrollo de EduApp se apoya en varias herramientas:

- **ESLint**: Para la verificación estática del código y la aplicación de estándares de codificación.
- **Git**: Sistema de control de versiones para colaboración y seguimiento de cambios.
- **GitHub**: Plataforma para el alojamiento del repositorio y la gestión del proyecto.
- **Netlify**: Plataforma para el despliegue continuo y el alojamiento de la aplicación.

Estas herramientas forman parte integral del flujo de trabajo de desarrollo, asegurando la calidad del código y facilitando la colaboración entre desarrolladores.

### Arquitectura del sistema

EduApp implementa una arquitectura de cliente-servidor moderna con énfasis en la separación de responsabilidades:

#### Arquitectura Frontend

El frontend de EduApp sigue una arquitectura basada en componentes con separación clara entre:

1. **Componentes de presentación**: Encargados exclusivamente de la renderización de la interfaz de usuario.
2. **Componentes contenedores**: Manejan la lógica de estado y conectan los componentes de presentación con los datos.
3. **Hooks personalizados**: Encapsulan la lógica de negocio y las operaciones de datos.
4. **Servicios**: Abstraen la comunicación con APIs externas y proporcionan interfaces limpias para los componentes.

Esta separación facilita el mantenimiento y las pruebas, permitiendo que cada parte de la aplicación tenga responsabilidades claramente definidas.

#### Arquitectura Backend (Supabase)

El backend de EduApp se estructura en torno a los servicios proporcionados por Supabase:

1. **Base de datos PostgreSQL**: Organizada en tablas con relaciones bien definidas y políticas de RLS para control de acceso.
2. **API RESTful**: Generada automáticamente por Supabase para operaciones CRUD en las tablas.
3. **Edge Functions**: Implementaciones serverless para lógica de negocio compleja o integración con servicios externos.
4. **Almacenamiento**: Sistema para la gestión de archivos con políticas de acceso granulares.

La arquitectura de Supabase permite un escalado horizontal eficiente, con separación clara entre los servicios de autenticación, base de datos y almacenamiento.

#### Flujo de datos

El flujo de datos en EduApp sigue un patrón unidireccional:

1. **Interacción del usuario**: El usuario interactúa con la interfaz de usuario a través de componentes de React.
2. **Gestión de estado local**: Los componentes y hooks mantienen el estado local necesario para la interfaz.
3. **Solicitudes al servidor**: React Query gestiona las solicitudes al servidor a través del cliente de Supabase.
4. **Operaciones de base de datos**: Supabase procesa las solicitudes, aplica las políticas de RLS y ejecuta las operaciones en la base de datos.
5. **Respuesta y actualización**: Los datos retornan al cliente, donde React Query los almacena en caché y los componentes se actualizan.

Este flujo unidireccional simplifica el razonamiento sobre el estado de la aplicación y facilita la depuración.

![Diagrama de arquitectura](public/placeholder.svg)
*Figura 1: Diagrama de arquitectura general de EduApp*

## Diagramas de modelamiento

### Diagramas de casos de uso

Los diagramas de casos de uso representan las interacciones entre los usuarios (actores) y el sistema, mostrando las funcionalidades principales disponibles para cada tipo de usuario.

#### Diagrama de casos de uso general

![Diagrama de casos de uso general](public/placeholder.svg)
*Figura 2: Diagrama de casos de uso general de EduApp*

El diagrama muestra los tres tipos de usuarios principales (Administradores, Docentes y Padres) y sus interacciones con los módulos del sistema.

#### Casos de uso para Administradores

Los administradores tienen acceso a funcionalidades de gestión del sistema:

1. **Gestionar usuarios**
   - Crear cuentas de usuario
   - Modificar permisos
   - Desactivar usuarios

2. **Gestionar instituciones**
   - Configurar datos de la institución
   - Asignar administradores

3. **Acceder a reportes administrativos**
   - Ver estadísticas de uso
   - Monitorear actividad

#### Casos de uso para Docentes

Los docentes interactúan principalmente con funcionalidades relacionadas con estudiantes:

1. **Gestionar asistencia**
   - Registrar asistencia diaria
   - Generar reportes de asistencia
   - Notificar ausencias

2. **Evaluar desarrollo motriz**
   - Crear formularios de evaluación
   - Aplicar evaluaciones individuales o grupales
   - Generar reportes de desarrollo

3. **Gestionar permisos de recogida**
   - Aprobar/rechazar solicitudes
   - Verificar documentos de identidad

4. **Administrar estudiantes**
   - Agregar nuevos estudiantes
   - Asignar estudiantes a grupos
   - Actualizar información

#### Casos de uso para Padres

Los padres tienen acceso a información sobre sus hijos y funcionalidades específicas:

1. **Consultar asistencia**
   - Ver registro de asistencia
   - Recibir notificaciones

2. **Solicitar permisos de recogida**
   - Crear solicitudes para terceros
   - Adjuntar documentos de identidad
   - Ver historial de solicitudes

3. **Revisar reportes de desarrollo**
   - Acceder a evaluaciones
   - Ver progreso en habilidades motrices

### Modelo Entidad-Relación

El modelo Entidad-Relación (ER) representa la estructura de datos de EduApp, mostrando las entidades principales, sus atributos y las relaciones entre ellas.

![Modelo Entidad-Relación](public/placeholder.svg)
*Figura 3: Modelo Entidad-Relación de la base de datos de EduApp*

#### Entidades principales

1. **Users (user_credentials)**
   - Almacena las credenciales de autenticación
   - Contiene información básica de usuarios
   - Se relaciona con perfiles y roles

2. **Profiles (user_profiles)**
   - Información extendida de usuarios
   - Preferencias y configuraciones
   - Datos de contacto

3. **Institutions**
   - Datos de instituciones educativas
   - Se relaciona con administradores y docentes

4. **Students**
   - Información de estudiantes
   - Relaciones con padres y docentes
   - Datos académicos

5. **Attendance Records**
   - Registros diarios de asistencia
   - Estado de presencia/ausencia
   - Notas adicionales

6. **Pickup Permissions**
   - Solicitudes de recogida
   - Documentos de identidad
   - Estado de aprobación

7. **Motor Activity Forms**
   - Plantillas de evaluación motriz
   - Configuración de campos
   - Criterios de evaluación

8. **Motor Activity Responses**
   - Respuestas a evaluaciones
   - Observaciones y resultados
   - Sugerencias de AI

#### Relaciones clave

- **Users - Profiles**: Relación 1:1 entre credenciales y perfiles extendidos
- **Users - Institutions**: Relación N:M a través de roles específicos
- **Teachers - Students**: Relación 1:N donde un docente puede tener múltiples estudiantes
- **Parents - Students**: Relación 1:N donde un padre puede tener múltiples hijos
- **Students - Attendance**: Relación 1:N de registros diarios
- **Parents - Pickup Permissions**: Relación 1:N de solicitudes
- **Teachers - Motor Forms**: Relación 1:N donde un docente crea formularios
- **Students - Motor Responses**: Relación 1:N de evaluaciones aplicadas

### Diagrama de clases

Aunque EduApp está construido principalmente con componentes funcionales de React y hooks, el siguiente diagrama conceptual representa las principales estructuras de datos y sus relaciones.

![Diagrama de clases](public/placeholder.svg)
*Figura 4: Representación conceptual de clases en EduApp*

El diagrama muestra la organización lógica de los principales tipos de datos utilizados en la aplicación, incluyendo sus propiedades y métodos conceptuales. Esta representación ayuda a comprender las relaciones entre los diferentes objetos de datos, aunque la implementación real se basa en objetos literales, interfaces TypeScript y hooks personalizados.

### Diagrama de Base de Datos

El siguiente diagrama muestra la estructura relacional de la base de datos implementada en PostgreSQL a través de Supabase.

![Diagrama de base de datos](public/placeholder.svg)
*Figura 5: Diagrama de la estructura de la base de datos*

El diagrama detalla las tablas implementadas, sus columnas, tipos de datos, claves primarias y relaciones. Las políticas de Row-Level Security (RLS) implementadas en cada tabla garantizan el acceso seguro a los datos según el rol del usuario autenticado.

### Diccionario de datos

A continuación se presenta el diccionario de datos que detalla la estructura de las principales tablas de la base de datos.

#### Tabla: user_credentials

| Campo          | Tipo          | Descripción                                   | Restricciones   |
|----------------|---------------|-----------------------------------------------|----------------|
| id             | uuid          | Identificador único del usuario               | PK, NOT NULL, DEFAULT uuid_generate_v4() |
| email          | text          | Correo electrónico (identificador de acceso)  | NOT NULL, UNIQUE |
| password       | text          | Contraseña encriptada                         | NOT NULL |
| full_name      | text          | Nombre completo del usuario                   | NOT NULL |
| role           | text          | Rol del usuario (admin, teacher, parent)      | NOT NULL |
| status         | text          | Estado del usuario (active, inactive)         | NOT NULL, DEFAULT 'active' |
| institution_id | uuid          | ID de la institución asociada                 | FK -> institutions.id |
| created_at     | timestamptz   | Fecha y hora de creación del registro         | NOT NULL, DEFAULT now() |

La tabla `user_credentials` almacena la información básica de autenticación para todos los usuarios del sistema. La contraseña se almacena de forma segura utilizando algoritmos de hash. El campo `role` determina los permisos y capacidades del usuario dentro del sistema, mientras que `status` permite desactivar cuentas sin eliminarlas.

#### Tabla: user_profiles

| Campo              | Tipo          | Descripción                               | Restricciones   |
|--------------------|---------------|-------------------------------------------|----------------|
| id                 | uuid          | Identificador único del perfil            | PK, NOT NULL, DEFAULT uuid_generate_v4() |
| user_id            | uuid          | ID del usuario asociado                   | FK -> user_credentials.id |
| email              | text          | Correo electrónico (duplicado para acceso rápido) | |
| display_name       | text          | Nombre para mostrar                       | |
| profile_image_url  | text          | URL de la imagen de perfil                | |
| phone_number       | text          | Número telefónico                         | |
| emergency_contact  | text          | Contacto de emergencia                    | |
| emergency_phone    | text          | Teléfono de emergencia                    | |
| address            | text          | Dirección física                          | |
| title              | text          | Título profesional                        | |
| position           | text          | Cargo en la institución                   | |
| preferences        | jsonb         | Preferencias de usuario (JSON)            | DEFAULT '{}' |
| additional_info    | jsonb         | Información adicional (JSON)              | |
| created_at         | timestamptz   | Fecha y hora de creación                  | NOT NULL, DEFAULT now() |

La tabla `user_profiles` extiende la información de los usuarios con datos adicionales no directamente relacionados con la autenticación. El uso de campos JSON (jsonb) permite almacenar estructuras de datos flexibles para preferencias y configuraciones personalizadas sin necesidad de modificar el esquema de la base de datos.

#### Tabla: students

| Campo        | Tipo          | Descripción                                | Restricciones   |
|-------------|---------------|-------------------------------------------|----------------|
| id           | uuid          | Identificador único del estudiante         | PK, NOT NULL, DEFAULT uuid_generate_v4() |
| first_name   | text          | Nombre del estudiante                      | NOT NULL |
| last_name    | text          | Apellido del estudiante                    | NOT NULL |
| grade        | text          | Grado escolar                              | NOT NULL |
| group_name   | text          | Nombre del grupo/aula                      | NOT NULL |
| birth_date   | date          | Fecha de nacimiento                        | NOT NULL |
| gender       | text          | Género                                     | NOT NULL, DEFAULT 'no_especificado' |
| parent_id    | uuid          | ID del padre/tutor                         | FK -> user_credentials.id |
| teacher_id   | uuid          | ID del docente principal                   | FK -> user_credentials.id |
| status       | text          | Estado (active, inactive)                  | NOT NULL, DEFAULT 'active' |
| created_at   | timestamptz   | Fecha de registro                          | NOT NULL, DEFAULT now() |

La tabla `students` almacena la información de los estudiantes registrados en el sistema. Los campos `parent_id` y `teacher_id` establecen las relaciones con los usuarios responsables del estudiante, permitiendo filtrar y organizar los estudiantes por docente o por padre/tutor.

El diccionario continúa con definiciones detalladas para todas las tablas principales del sistema, proporcionando una referencia completa de la estructura de datos.

#### Tabla: attendance_records

| Campo       | Tipo           | Descripción                            | Restricciones   |
|-------------|----------------|----------------------------------------|----------------|
| id          | uuid           | Identificador único del registro       | PK, NOT NULL, DEFAULT uuid_generate_v4() |
| student_id  | uuid           | ID del estudiante                      | FK -> students.id, NOT NULL |
| date        | date           | Fecha del registro                     | NOT NULL |
| status      | text           | Estado de asistencia                   | NOT NULL |
| entry_time  | time           | Hora de entrada                        | |
| exit_time   | time           | Hora de salida                         | |
| notes       | text           | Observaciones                          | |
| created_at  | timestamptz    | Fecha y hora de creación del registro  | NOT NULL, DEFAULT now() |

La tabla `attendance_records` permite el seguimiento diario de la asistencia de cada estudiante, registrando su estado (presente, ausente, con permiso, etc.), horarios de entrada y salida, y observaciones relevantes. La combinación de `student_id` y `date` permite consultas eficientes para obtener el historial de asistencia de un estudiante o los registros de un día específico.

### Prototipos de la aplicación

Durante el proceso de diseño y desarrollo de EduApp, se crearon diversos prototipos para visualizar la interfaz de usuario y validar la experiencia de usuario antes de la implementación.

![Prototipo de pantalla de inicio de sesión](public/placeholder.svg)
*Figura 6: Prototipo de la pantalla de inicio de sesión*

![Prototipo de registro de asistencia](public/placeholder.svg)
*Figura 7: Prototipo del módulo de registro de asistencia*

![Prototipo de evaluación motriz](public/placeholder.svg)
*Figura 8: Prototipo del módulo de evaluación de desarrollo motriz*

Los prototipos fueron diseñados siguiendo principios de usabilidad adaptados a los diferentes roles de usuario, con especial atención a:

- **Simplicidad**: Interfaces limpias y enfocadas en la tarea principal
- **Accesibilidad**: Diseño inclusivo con consideraciones para diferentes capacidades
- **Adaptabilidad**: Diseño responsive para dispositivos móviles y de escritorio
- **Consistencia**: Elementos de interfaz coherentes en todos los módulos

Los prototipos sirvieron como guía para el desarrollo de la interfaz final, permitiendo iteraciones y mejoras basadas en la retroalimentación de usuarios antes de la implementación completa.

## Estructura del proyecto

### Organización de directorios

El proyecto EduApp sigue una estructura organizada por características y responsabilidades, facilitando la localización de archivos y la mantenibilidad del código.

```
/src
  /components        # Componentes compartidos reutilizables
    /ui              # Componentes de interfaz básicos (shadcn/ui)
    /navigation      # Componentes de navegación
    /shared          # Componentes compartidos entre módulos
    /attendance      # Componentes específicos del módulo de asistencia
    /permissions     # Componentes del módulo de permisos de recogida
    /motor-skills    # Componentes del módulo de desarrollo motriz
    /parent          # Componentes para interfaces de padres
    /admin           # Componentes para interfaces de administradores
    /auth            # Componentes de autenticación
  
  /hooks             # Hooks personalizados para lógica compartida
    /use-mobile.tsx  # Hook para detección de dispositivo móvil
    /useAuth.ts      # Hook para gestión de autenticación
    /useProfile.ts   # Hook para datos de perfil
    /useStudentAttendance.ts  # Hook para datos de asistencia
    
  /lib               # Bibliotecas y utilidades
    /supabase        # Cliente y tipos de Supabase
      /client        # Implementación modular del cliente
        /core.ts     # Cliente base de Supabase
        /auth.ts     # Utilidades de autenticación
        /headers.ts  # Gestión de encabezados HTTP
        /requests.ts # Funciones para solicitudes autenticadas
        /user.ts     # Funciones relacionadas con usuarios
      /types        # Definiciones de tipos TypeScript
    /utils.ts       # Utilidades generales
  
  /pages             # Páginas por rol de usuario
    /auth            # Páginas de autenticación
    /admin           # Interfaces para administradores
    /parent          # Interfaces para padres
    /teacher         # Interfaces para docentes
      /attendance    # Página de asistencia para docentes
      /motor-skills  # Páginas de desarrollo motriz
      /permissions   # Página de permisos de recogida
      /profile       # Página de perfil del docente
  
  /integrations      # Código para integraciones externas
    /supabase        # Integración con Supabase
  
  /styles            # Estilos globales
```

Esta estructura organiza el código de forma lógica:

- Los **componentes** se agrupan por funcionalidad o módulo, con subdirectorios para componentes específicos.
- Los **hooks** encapsulan la lógica de negocio reutilizable.
- La carpeta **lib** contiene utilidades y configuraciones compartidas.
- Las **páginas** están organizadas por rol de usuario, facilitando la comprensión de los flujos específicos de cada tipo de usuario.

### Componentes principales

Los componentes en EduApp siguen un patrón de diseño modular con responsabilidades claramente definidas:

#### Componentes de presentación

Estos componentes se enfocan exclusivamente en la renderización de la interfaz de usuario, recibiendo datos y callbacks como props:

```tsx
// src/components/attendance/AttendanceTable.tsx
const AttendanceTable = ({ 
  students, 
  onStatusChange 
}: AttendanceTableProps) => {
  return (
    <Table>
      {/* Renderizado de la tabla */}
    </Table>
  );
};
```

#### Hooks de lógica

La lógica de negocio y estado se encapsula en hooks personalizados:

```tsx
// src/hooks/useStudentAttendance.ts
export const useStudentAttendance = (date: Date) => {
  const [students, setStudents] = useState<Student[]>([]);
  const [loading, setLoading] = useState(true);
  
  useEffect(() => {
    // Lógica para cargar datos de asistencia
  }, [date]);
  
  const updateAttendance = async (studentId: string, status: string) => {
    // Lógica para actualizar asistencia
  };
  
  return { students, loading, updateAttendance };
};
```

#### Componentes contenedores

Conectan los hooks con los componentes de presentación:

```tsx
// src/pages/teacher/attendance/AttendancePage.tsx
const AttendancePage = () => {
  const { date, setDate } = useAttendanceState();
  const { students, loading, updateAttendance } = useStudentAttendance(date);
  
  return (
    <div>
      <DatePicker date={date} onChange={setDate} />
      {loading ? (
        <LoadingSpinner />
      ) : (
        <AttendanceTable 
          students={students} 
          onStatusChange={updateAttendance} 
        />
      )}
    </div>
  );
};
```

Esta separación de responsabilidades facilita las pruebas unitarias y mejora la mantenibilidad del código al aislar claramente los diferentes aspectos de la aplicación.

## Componentes principales

### Módulo de autenticación

El módulo de autenticación gestiona el acceso de usuarios al sistema, implementando un flujo seguro de registro, inicio de sesión y recuperación de contraseña adaptado a los diferentes roles.

#### Componentes clave

- **LoginForm**: Permite a los usuarios autenticarse con correo y contraseña
- **RegisterForm**: Facilita el registro de nuevos usuarios
- **ProtectedRoute**: HOC que verifica la autenticación antes de permitir acceso a rutas protegidas

#### Implementación técnica

La autenticación se basa en el servicio de autenticación de Supabase, con un flujo personalizado:

1. El usuario introduce sus credenciales en el formulario de inicio de sesión
2. La aplicación envía las credenciales a Supabase para validación
3. Si son correctas, Supabase devuelve un token JWT y datos básicos del usuario
4. El token se almacena en localStorage mediante el cliente de Supabase
5. El hook `useAuth` gestiona el estado global de autenticación

```typescript
// Ejemplo simplificado del hook useAuth
export const useAuth = () => {
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(true);
  
  useEffect(() => {
    // Recuperar sesión existente
    const { data: { session } } = supabase.auth.getSession();
    setUser(session?.user || null);
    
    // Escuchar cambios en el estado de autenticación
    const { subscription } = supabase.auth.onAuthStateChange((_, session) => {
      setUser(session?.user || null);
    });
    
    setLoading(false);
    return () => subscription.unsubscribe();
  }, []);
  
  const login = async (email, password) => {
    const { data, error } = await supabase.auth.signInWithPassword({
      email,
      password
    });
    
    if (error) throw error;
    return data;
  };
  
  const logout = async () => {
    const { error } = await supabase.auth.signOut();
    if (error) throw error;
  };
  
  return { user, loading, login, logout };
};
```

#### Seguridad implementada

El módulo implementa diversas medidas de seguridad:

- **Almacenamiento seguro**: Las contraseñas nunca se almacenan en texto plano
- **Protección contra ataques**: Limitación de intentos de inicio de sesión
- **Tokens JWT**: Para autenticación sin estado y verificación de identidad
- **Políticas RLS**: Restricciones a nivel de tabla basadas en el usuario autenticado

### Módulo de asistencia

El módulo de asistencia permite a los docentes registrar y gestionar la asistencia diaria de los estudiantes, proporcionando una interfaz intuitiva y herramientas eficientes para el seguimiento.

#### Componentes clave

- **AttendanceTable**: Muestra la lista de estudiantes con opciones de registro
- **DateAndFilters**: Permite seleccionar la fecha y filtrar estudiantes
- **QuickActions**: Proporciona acciones masivas para optimizar el registro

#### Flujo de trabajo

1. El docente selecciona una fecha para el registro de asistencia
2. La aplicación carga la lista de estudiantes y su estado actual de asistencia para esa fecha
3. El docente puede marcar la asistencia individualmente o utilizar acciones rápidas
4. Los cambios se sincronizan en tiempo real con la base de datos
5. El sistema genera notificaciones automáticas para padres en caso de ausencias

#### Implementación técnica

El módulo se implementa mediante componentes especializados y hooks que gestionan la lógica de negocio:

```typescript
// Hook para gestionar el estado del módulo de asistencia
export const useAttendanceState = () => {
  const [date, setDate] = useState<Date>(new Date());
  const [selectedGrade, setSelectedGrade] = useState<string>("all");
  const [selectedGroup, setSelectedGroup] = useState<string>("all");
  const [searchTerm, setSearchTerm] = useState<string>("");
  
  const filterStudents = (students: StudentWithAttendance[]) => {
    // Lógica de filtrado
  };
  
  return {
    date, setDate,
    selectedGrade, setSelectedGrade,
    selectedGroup, setSelectedGroup,
    searchTerm, setSearchTerm,
    filterStudents
  };
};
```

La persistencia de datos se realiza mediante el cliente Supabase:

```typescript
// Función para actualizar el estado de asistencia
const updateAttendanceStatus = async (studentId: string, status: string, date: string) => {
  // Verificar si ya existe un registro para este estudiante y fecha
  const { data: existingRecord } = await supabase
    .from('attendance_records')
    .select('*')
    .eq('student_id', studentId)
    .eq('date', date)
    .single();
    
  if (existingRecord) {
    // Actualizar registro existente
    return supabase
      .from('attendance_records')
      .update({ status })
      .eq('id', existingRecord.id);
  } else {
    // Crear nuevo registro
    return supabase
      .from('attendance_records')
      .insert({
        student_id: studentId,
        date,
        status
      });
  }
};
```

#### Optimizaciones implementadas

El módulo incluye varias optimizaciones para mejorar la experiencia de usuario y el rendimiento:

- **Caché de datos**: React Query almacena en caché los registros para reducir solicitudes al servidor
- **Actualizaciones optimistas**: La interfaz se actualiza inmediatamente antes de confirmar los cambios
- **Procesamiento por lotes**: Las acciones masivas se procesan en lotes para reducir la carga del servidor
- **Vista responsive**: Diseño adaptable a diferentes dispositivos, optimizado para uso en tablets

### Módulo de permisos de recogida

El módulo de permisos de recogida permite a los padres solicitar autorizaciones para que terceras personas recojan a sus hijos, con un flujo seguro de documentación y aprobación.

#### Componentes clave

- **PermissionForm**: Formulario para solicitar nuevos permisos
- **FileUpload**: Componente para adjuntar documentos de identidad
- **PermissionsTable**: Vista para docentes que muestra las solicitudes pendientes

#### Flujo de trabajo

1. Un padre selecciona la fecha y persona autorizada
2. Adjunta documento de identidad (cédula, pasaporte, etc.)
3. Envía la solicitud al sistema
4. Los docentes reciben notificación de nueva solicitud
5. El docente revisa la solicitud y el documento
6. El docente aprueba o rechaza la solicitud
7. El padre recibe notificación del resultado

#### Implementación técnica

El módulo utiliza un esquema de validación riguroso implementado con Zod:

```typescript
// Esquema de validación para permisos de recogida
export const permissionSchema = z.object({
  studentId: z.string().min(1, "Seleccione un estudiante"),
  date: z.date({
    required_error: "Seleccione una fecha",
  }),
  pickupPerson: z.string().min(1, "Ingrese el nombre de la persona autorizada"),
  relationship: z.string().min(1, "Indique la relación con el estudiante"),
  identificationFile: z.string().min(1, "Adjunte un documento de identificación"),
  reason: z.string().min(1, "Indique el motivo del permiso")
});
```

La gestión de archivos se realiza a través del servicio de almacenamiento de Supabase:

```typescript
// Hook para gestionar la carga de documentos
export const useFileUpload = () => {
  const [file, setFile] = useState<File | null>(null);
  const [uploading, setUploading] = useState(false);
  const [fileUrl, setFileUrl] = useState<string>("");
  const [error, setError] = useState<string | null>(null);
  
  const uploadFile = async () => {
    if (!file) return;
    
    setUploading(true);
    setError(null);
    
    try {
      // Generar nombre de archivo único
      const fileName = `${uuidv4()}-${file.name}`;
      const filePath = `identification/${fileName}`;
      
      // Subir archivo a Supabase Storage
      const { error } = await supabase.storage
        .from('permission-documents')
        .upload(filePath, file);
        
      if (error) throw error;
      
      // Obtener URL pública
      const { data } = supabase.storage
        .from('permission-documents')
        .getPublicUrl(filePath);
        
      setFileUrl(data.publicUrl);
    } catch (err) {
      console.error("Error al subir archivo:", err);
      setError("Error al subir el archivo. Intente nuevamente.");
    } finally {
      setUploading(false);
    }
  };
  
  return { file, setFile, uploading, fileUrl, error, uploadFile };
};
```

### Módulo de reportes de desarrollo motriz

Este módulo proporciona herramientas avanzadas para evaluar y hacer seguimiento del desarrollo motriz de los estudiantes, incluyendo integración con inteligencia artificial para análisis y recomendaciones.

#### Componentes clave

- **ActivityFormList**: Muestra los formularios de evaluación disponibles
- **GroupEvaluationTable**: Facilita la evaluación de múltiples estudiantes
- **AIAssistant**: Proporciona sugerencias basadas en IA para actividades
- **StudentPerformanceAnalysis**: Muestra análisis del progreso del estudiante

#### Implementación técnica

El módulo implementa un sistema flexible de formularios dinámicos:

```typescript
// Estructura de un formulario de actividad motriz
interface MotorActivityForm {
  id: string;
  title: string;
  description: string;
  form_data: {
    fields: {
      id: string;
      type: 'select' | 'text' | 'checkbox';
      label: string;
      options?: string[];
      required: boolean;
    }[];
    groups: {
      id: string;
      name: string;
      fieldIds: string[];
    }[];
  };
  teacher_id: string;
  created_at: string;
  updated_at: string;
}
```

El componente de evaluación grupal permite evaluar múltiples estudiantes eficientemente:

```tsx
// Implementación simplificada del componente GroupEvaluationTable
const GroupEvaluationTable = ({ 
  students, 
  options, 
  selectedOptions, 
  onOptionSelect 
}) => {
  const { isMobile } = useIsMobile();
  
  // Agrupar estudiantes por grado y grupo
  const studentsByGroup = useMemo(() => {
    return students.reduce((acc, student) => {
      const key = `${student.grade} ${student.group_name}`;
      if (!acc[key]) acc[key] = [];
      acc[key].push(student);
      return acc;
    }, {});
  }, [students]);
  
  return (
    <div className="overflow-x-auto">
      <TooltipProvider>
        <table>
          <TableHeader options={options} isMobile={isMobile} />
          <tbody>
            {Object.entries(studentsByGroup).map(([groupName, groupStudents]) => (
              <React.Fragment key={groupName}>
                <GroupRow groupName={groupName} />
                {groupStudents.map(student => (
                  <StudentRow
                    key={student.id}
                    student={student}
                    options={options}
                    selectedOption={selectedOptions[student.id] || ''}
                    onSelect={onOptionSelect}
                  />
                ))}
              </React.Fragment>
            ))}
          </tbody>
        </table>
      </TooltipProvider>
    </div>
  );
};
```

#### Integración con inteligencia artificial

El módulo incorpora análisis y sugerencias basadas en IA para apoyar el trabajo docente:

```typescript
// Hook para obtener sugerencias de IA
export const useAISuggestions = () => {
  const [suggestions, setSuggestions] = useState<string>("");
  const [loading, setLoading] = useState<boolean>(false);
  const [error, setError] = useState<string | null>(null);
  
  const generateSuggestions = async (observations: string, activityType: string) => {
    setLoading(true);
    setError(null);
    
    try {
      // Invocar función serverless de Supabase para IA
      const { data, error } = await supabase.functions.invoke("get_ai_suggestion", {
        body: {
          observations,
          activityType
        }
      });
      
      if (error) throw error;
      setSuggestions(data.suggestions);
    } catch (err) {
      console.error("Error al obtener sugerencias:", err);
      setError("No se pudieron generar sugerencias en este momento.");
    } finally {
      setLoading(false);
    }
  };
  
  return { suggestions, loading, error, generateSuggestions };
};
```

### Módulo de gestión de usuarios

Este módulo permite a los administradores gestionar usuarios, asignar roles y mantener la información institucional actualizada.

#### Componentes clave

- **UserManagement**: Interfaz principal de gestión de usuarios
- **UserTable**: Muestra listado de usuarios con acciones
- **CreateUserDialog**: Formulario para crear nuevos usuarios
- **EditUserDialog**: Formulario para editar usuarios existentes

#### Implementación técnica

La gestión de usuarios se realiza mediante operaciones controladas en Supabase:

```typescript
// Hook para gestión de usuarios (simplificado)
export const useUsers = () => {
  const [users, setUsers] = useState<User[]>([]);
  const [loading, setLoading] = useState<boolean>(true);
  
  const fetchUsers = async () => {
    setLoading(true);
    
    try {
      const { data, error } = await supabase
        .from('user_credentials')
        .select(`
          *,
          user_profiles(*)
        `);
        
      if (error) throw error;
      setUsers(data || []);
    } catch (error) {
      console.error("Error al cargar usuarios:", error);
    } finally {
      setLoading(false);
    }
  };
  
  const createUser = async (userData: CreateUserData) => {
    // Implementación de creación de usuario
  };
  
  const updateUser = async (userId: string, userData: UpdateUserData) => {
    // Implementación de actualización de usuario
  };
  
  const deleteUser = async (userId: string) => {
    // Implementación de eliminación de usuario
  };
  
  useEffect(() => {
    fetchUsers();
  }, []);
  
  return { users, loading, createUser, updateUser, deleteUser, fetchUsers };
};
```

## Integración con APIs externas

EduApp integra servicios de inteligencia artificial para enriquecer las funcionalidades del sistema, principalmente en el área de análisis de desarrollo motriz y generación de sugerencias educativas.

### Configuración de API OpenAI

La integración con OpenAI permite generar sugerencias personalizadas para actividades motrices basadas en las observaciones de los docentes.

#### Implementación técnica

La integración se realiza a través de una Edge Function de Supabase, que actúa como intermediaria segura entre el frontend y la API de OpenAI:

```typescript
// supabase/functions/get_ai_suggestion/index.ts
import { serve } from "https://deno.land/std@0.168.0/http/server.ts";
import { OpenAI } from "https://esm.sh/openai@4.11.0";

const openai = new OpenAI({
  apiKey: Deno.env.get("OPENAI_API_KEY")
});

const corsHeaders = {
  "Access-Control-Allow-Origin": "*",
  "Access-Control-Allow-Headers": "authorization, x-client-info, apikey, content-type",
};

serve(async (req) => {
  if (req.method === "OPTIONS") {
    return new Response("ok", { headers: corsHeaders });
  }
  
  try {
    const { observations, activityType } = await req.json();
    
    if (!observations || !activityType) {
      return new Response(
        JSON.stringify({
          error: "Se requieren observaciones y tipo de actividad"
        }),
        {
          status: 400,
          headers: { ...corsHeaders, "Content-Type": "application/json" }
        }
      );
    }
    
    // Crear prompt para OpenAI
    const prompt = `
      Como especialista en desarrollo motriz infantil, analiza las siguientes observaciones 
      de un estudiante preescolar realizando actividades de tipo "${activityType}" y proporciona:
      
      1. 3-5 sugerencias específicas de actividades para fortalecer las habilidades observadas
      2. Recomendaciones para docentes sobre cómo apoyar al estudiante
      3. Consejos para compartir con los padres
      
      Observaciones del docente: "${observations}"
      
      Responde en español, con formato y lenguaje apropiado para docentes.
    `;
    
    // Llamar a la API de OpenAI
    const response = await openai.completions.create({
      model: "gpt-3.5-turbo-instruct",
      prompt,
      max_tokens: 800,
      temperature: 0.7
    });
    
    return new Response(
      JSON.stringify({ suggestions: response.choices[0].text }),
      {
        headers: { ...corsHeaders, "Content-Type": "application/json" }
      }
    );
  } catch (error) {
    console.error("Error al procesar solicitud:", error);
    
    return new Response(
      JSON.stringify({ error: "Error al procesar la solicitud" }),
      {
        status: 500,
        headers: { ...corsHeaders, "Content-Type": "application/json" }
      }
    );
  }
});
```

#### Configuración y uso en el frontend

En el frontend, la integración se utiliza a través del hook `useAISuggestions`:

```typescript
// src/pages/teacher/motor-skills/hooks/reports/useAISuggestions.ts
export const useAISuggestions = () => {
  const [suggestions, setSuggestions] = useState<string>("");
  const [isLoading, setIsLoading] = useState<boolean>(false);
  const [error, setError] = useState<string | null>(null);
  
  const generateSuggestions = async (observations: string, activityType: string) => {
    if (!observations.trim() || !activityType) {
      setError("Se requieren observaciones y tipo de actividad");
      return;
    }
    
    setIsLoading(true);
    setError(null);
    
    try {
      // Llamar a la Edge Function
      const { data, error } = await supabase.functions.invoke("get_ai_suggestion", {
        body: { observations, activityType }
      });
      
      if (error) throw new Error(error.message);
      setSuggestions(data.suggestions || "");
    } catch (err) {
      console.error("Error al obtener sugerencias:", err);
      setError("No se pudieron generar sugerencias en este momento.");
    } finally {
      setIsLoading(false);
    }
  };
  
  return { suggestions, isLoading, error, generateSuggestions };
};
```

#### Gestión de la clave API

La clave de API de OpenAI se almacena de forma segura como variable de entorno en Supabase, sin exponerla en el frontend. Las solicitudes siempre pasan por la Edge Function, que maneja la autenticación con la API externa.

### Configuración de API Perplexity

La integración con Perplexity AI se utiliza para la búsqueda y análisis de instituciones educativas durante el proceso de registro.

#### Implementación técnica

La integración se implementa mediante una Edge Function dedicada:

```typescript
// supabase/functions/search_institutions/perplexity.ts
const PERPLEXITY_API_KEY = Deno.env.get("PERPLEXITY_API_KEY");

export async function searchInstitutionsWithPerplexity(zone: string) {
  if (!PERPLEXITY_API_KEY) {
    throw new Error("PERPLEXITY_API_KEY not set");
  }
  
  const prompt = `
    Actúa como un asistente especializado en información educativa. Necesito información sobre 
    instituciones preescolares o jardines infantiles en la zona: "${zone}". 
    
    Por favor, proporciona una lista de al menos 5 instituciones educativas con la siguiente información:
    1. Nombre de la institución
    2. Breve descripción (1-2 oraciones)
    3. Zona/ubicación específica
    
    Formatea la respuesta como un array JSON con esta estructura:
    [
      {
        "name": "Nombre de la institución",
        "description": "Descripción breve",
        "zone": "Zona específica"
      }
    ]
    
    Incluye SOLAMENTE el JSON en tu respuesta, sin texto adicional.
  `;
  
  try {
    const response = await fetch("https://api.perplexity.ai/chat/completions", {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
        "Authorization": `Bearer ${PERPLEXITY_API_KEY}`
      },
      body: JSON.stringify({
        model: "llama-3-sonar-small-32k-online",
        messages: [
          { role: "system", content: "You are a helpful assistant specialized in educational information." },
          { role: "user", content: prompt }
        ],
        max_tokens: 1024
      })
    });
    
    if (!response.ok) {
      const errorText = await response.text();
      throw new Error(`Perplexity API error: ${response.status} - ${errorText}`);
    }
    
    const data = await response.json();
    const content = data.choices[0].message.content;
    
    // Extraer JSON de la respuesta
    try {
      const jsonMatch = content.match(/\[[\s\S]*\]/);
      const jsonString = jsonMatch ? jsonMatch[0] : content;
      return JSON.parse(jsonString);
    } catch (parseError) {
      console.error("Error parsing JSON from response:", parseError);
      // Intento de fallback para extraer JSON
      return JSON.parse(content);
    }
  } catch (error) {
    console.error("Error querying Perplexity API:", error);
    throw error;
  }
}
```

#### Configuración y uso en el frontend

La integración se utiliza en el módulo de registro para ayudar a los nuevos usuarios a encontrar su institución educativa:

```typescript
// src/components/auth/institution-search/useInstitutionSearchLogic.ts
export const useInstitutionSearchLogic = () => {
  const [zone, setZone] = useState<string>("");
  const [searchResults, setSearchResults] = useState<Institution[]>([]);
  const [analysis, setAnalysis] = useState<string>("");
  const [isSearching, setIsSearching] = useState<boolean>(false);
  const [error, setError] = useState<string | null>(null);
  
  const searchInstitutions = async () => {
    if (!zone.trim()) {
      setError("Ingrese una zona para buscar instituciones");
      return;
    }
    
    setIsSearching(true);
    setError(null);
    
    try {
      // Llamar a la Edge Function
      const { data, error } = await supabase.functions.invoke("search_institutions", {
        body: { zone }
      });
      
      if (error) throw new Error(error.message);
      
      setSearchResults(data.institutions || []);
      setAnalysis(data.analysis || "");
    } catch (err) {
      console.error("Error en búsqueda de instituciones:", err);
      setError("No se pudieron encontrar instituciones. Intente nuevamente.");
    } finally {
      setIsSearching(false);
    }
  };
  
  return { 
    zone, setZone,
    searchResults,
    analysis,
    isSearching,
    error,
    searchInstitutions
  };
};
```

#### Consideraciones para cambios en la configuración

Si es necesario modificar la configuración de integración con Perplexity AI:

1. Acceder al panel de administración de Supabase
2. Navegar a la sección "Functions"
3. Seleccionar la función "search_institutions"
4. Actualizar el código según sea necesario
5. Si se requiere cambiar el modelo de IA, modificar el parámetro "model" en la solicitud

#### Seguridad y consideraciones de costo

La integración con APIs externas incluye medidas para gestionar costos y seguridad:

- **Limitación de uso**: Se implementan verificaciones para evitar abuso o uso excesivo
- **Almacenamiento en caché**: Los resultados de búsquedas comunes se almacenan para reducir llamadas repetidas
- **Validación de entradas**: Todas las entradas de usuario se validan antes de enviarlas a las APIs externas
- **Manejo de errores**: Sistema robusto de manejo de errores para degradación elegante en caso de fallos de la API

## Optimización y rendimiento

### Estrategias de optimización implementadas

EduApp implementa diversas estrategias para optimizar el rendimiento y la experiencia de usuario:

#### División de código (Code Splitting)

La aplicación utiliza importaciones dinámicas para cargar componentes solo cuando son necesarios:

```typescript
// Ejemplo de carga dinámica de componentes
const MotorSkillsPage = React.lazy(() => import('./pages/teacher/motor-skills/MotorSkillsPage'));
```

Esta técnica reduce el tamaño del bundle inicial y mejora los tiempos de carga inicial.

#### Memoización de componentes y cálculos

Se utilizan React.memo y hooks de memoización para evitar renderizados innecesarios:

```typescript
// Memoización de componentes
const MemoizedAttendanceTable = React.memo(AttendanceTable);

// Memoización de cálculos
const filteredStudents = useMemo(() => {
  return students.filter(student => {
    // Lógica de filtrado
  });
}, [students, filters]);
```

#### Renderizado condicional para dispositivos móviles

La aplicación adapta su interfaz según el dispositivo mediante el hook `useIsMobile`:

```typescript
const { isMobile } = useIsMobile();

return (
  <div>
    {isMobile ? (
      <MobileComponent />
    ) : (
      <DesktopComponent />
    )}
  </div>
);
```

#### Lazy loading de imágenes

Las imágenes se cargan de forma diferida para mejorar los tiempos de carga inicial:

```typescript
<img 
  src={imageUrl} 
  alt="Descripción" 
  loading="lazy" 
  className="h-auto w-full object-cover"
/>
```

#### Optimización de consultas a la base de datos

Las consultas a Supabase se optimizan para reducir la cantidad de datos transferidos:

```typescript
// Selección específica de columnas
const { data } = await supabase
  .from('students')
  .select('id, first_name, last_name, grade, group_name')
  .eq('teacher_id', teacherId);
```

#### Compresión de imágenes antes de la carga

Las imágenes se comprimen en el cliente antes de subirlas al servidor:

```typescript
import imageCompression from 'browser-image-compression';

const compressImage = async (file: File): Promise<File> => {
  const options = {
    maxSizeMB: 1,
    maxWidthOrHeight: 1920,
    useWebWorker: true
  };
  
  return imageCompression(file, options);
};
```

### Consideraciones de rendimiento

#### Monitoreo de rendimiento

La aplicación incluye herramientas para monitorear el rendimiento en producción:

- **Console logs estratégicos**: Para seguimiento de operaciones críticas
- **Captura de errores**: Sistema para registro y notificación de errores

#### Estrategias para dispositivos de bajo rendimiento

Para garantizar una experiencia adecuada en dispositivos con recursos limitados:

- **Paginación**: Las listas largas se dividen en páginas para reducir la carga de renderizado
- **Virtualización**: Para listas muy largas, solo se renderizan los elementos visibles en pantalla
- **Limitación de efectos visuales**: En dispositivos detectados como de bajo rendimiento

## Proceso de despliegue

### Despliegue en entorno de desarrollo

El proceso de configuración del entorno de desarrollo sigue estos pasos:

1. **Clonar el repositorio**:
   ```bash
   git clone https://github.com/SatanaeShadow/eduapp.git
   cd eduapp
   ```

2. **Instalar dependencias**:
   ```bash
   npm install
   ```

3. **Configurar variables de entorno**:
   - Crear un archivo `.env.local` en la raíz del proyecto
   - Configurar las variables necesarias:
     ```
     VITE_SUPABASE_URL=https://mucdwmcxdaosxivkowfq.supabase.co
     VITE_SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
     ```

4. **Iniciar servidor de desarrollo**:
   ```bash
   npm run dev
   ```

### Despliegue en entorno de producción

El despliegue en producción se realiza a través de Netlify:

1. **Preparar la aplicación para producción**:
   ```bash
   npm run build
   ```

2. **Configurar Netlify**:
   - Conectar el repositorio de GitHub
   - Configurar el comando de construcción: `npm run build`
   - Configurar el directorio de publicación: `dist`
   - Configurar variables de entorno en el panel de Netlify

3. **Configurar redirecciones para SPA**:
   - Crear un archivo `_redirects` en la carpeta `public`:
     ```
     /* /index.html 200
     ```

4. **Activar despliegue continuo**:
   - Configurar despliegue automático desde la rama principal
   - Opcionalmente, configurar ambientes de vista previa para pull requests

## Seguridad implementada

### Prácticas de seguridad aplicadas

#### Políticas de seguridad a nivel de fila (RLS)

Supabase implementa políticas RLS que restringen el acceso a datos según el usuario autenticado:

```sql
-- Ejemplo de política RLS para la tabla students
CREATE POLICY "Students viewable by their teacher or parent"
ON public.students
FOR SELECT
USING (
  auth.uid() = teacher_id OR
  auth.uid() = parent_id OR
  auth.uid() IN (
    SELECT user_id FROM administrators WHERE institution_id = (
      SELECT institution_id FROM user_credentials WHERE id = auth.uid()
    )
  )
);
```

#### Protección contra ataques CSRF

La aplicación implementa tokens de autenticación JWT con validación adecuada para prevenir ataques CSRF.

#### Sanitización de entradas

Todas las entradas de usuario son validadas y sanitizadas antes de su procesamiento:

```typescript
// Validación con Zod
const schema = z.object({
  name: z.string().min(2).max(100),
  email: z.string().email(),
  role: z.enum(["admin", "teacher", "parent"])
});

const parsed = schema.safeParse(formData);
if (!parsed.success) {
  // Manejo de error de validación
}
```

#### Almacenamiento seguro de contraseñas

Las contraseñas se almacenan utilizando algoritmos de hash seguros, gestionados por Supabase Auth.

### Medidas de protección de datos

#### Encriptación de datos sensibles

Los datos sensibles se almacenan encriptados en la base de datos:

```typescript
// Ejemplo conceptual de almacenamiento encriptado
const storeEncryptedData = async (userId: string, sensitiveData: string) => {
  // Generar clave de encriptación única por usuario
  const { data: key } = await supabase.rpc('get_encryption_key', { user_id: userId });
  
  // Encriptar datos
  const encryptedData = await encryptWithKey(sensitiveData, key);
  
  // Almacenar datos encriptados
  return supabase
    .from('sensitive_info')
    .insert({ user_id: userId, data: encryptedData });
};
```

#### Gestión de acceso a documentos

El acceso a documentos (como identificaciones para permisos de recogida) se controla mediante políticas específicas:

```typescript
// Verificación de acceso a documentos
const canAccessDocument = async (documentId: string, userId: string) => {
  const { data, error } = await supabase
    .from('pickup_permissions')
    .select('parent_id, student_id')
    .eq('identification_file', documentId)
    .single();
    
  if (error || !data) return false;
  
  // Verificar si el usuario es el padre o el docente del estudiante
  if (data.parent_id === userId) return true;
  
  const { data: student } = await supabase
    .from('students')
    .select('teacher_id')
    .eq('id', data.student_id)
    .single();
    
  return student?.teacher_id === userId;
};
```

## Guía de mantenimiento

### Procedimientos de actualización

#### Actualización de dependencias

Para mantener la aplicación segura y actualizada:

1. **Verificar dependencias obsoletas**:
   ```bash
   npm outdated
   ```

2. **Actualizar dependencias**:
   ```bash
   npm update
   ```

3. **Para actualizaciones mayores**:
   ```bash
   npx npm-check-updates -u
   npm install
   ```

4. **Verificación después de actualización**:
   ```bash
   npm run build
   npm test
   ```

#### Migración de esquema de base de datos

Para aplicar cambios en el esquema de la base de datos:

1. **Crear archivo de migración SQL**:
   ```sql
   -- Ejemplo: 20250601_add_device_tokens.sql
   ALTER TABLE user_profiles
   ADD COLUMN device_tokens JSONB DEFAULT '[]';
   ```

2. **Aplicar migración desde Supabase Studio**:
   - Navegar a la sección SQL Editor
   - Ejecutar el script SQL
   - Documentar el cambio en el registro de migraciones

### Solución a problemas comunes

#### Problemas de autenticación

Si los usuarios reportan problemas de inicio de sesión:

1. **Verificar estado de Supabase Auth**:
   - Revisar el panel de estado de Supabase
   - Verificar logs de autenticación

2. **Soluciones comunes**:
   - Limpiar localStorage en el navegador del usuario
   - Verificar que el correo electrónico esté confirmado
   - Resetear la contraseña si es necesario

#### Errores en la carga de datos

Si la aplicación muestra errores al cargar datos:

1. **Verificar conexión con Supabase**:
   ```typescript
   const testConnection = async () => {
     const { data, error } = await supabase
       .from('health_check')
       .select('*')
       .limit(1);
       
     if (error) {
       console.error("Error de conexión:", error);
     } else {
       console.log("Conexión exitosa:", data);
     }
   };
   ```

2. **Verificar políticas RLS**:
   - Revisar que el usuario tenga los permisos correctos
   - Verificar si las políticas están correctamente configuradas

3. **Soluciones comunes**:
   - Refrescar la sesión del usuario
   - Verificar que el rol del usuario sea el correcto
   - Comprobar si existen restricciones de red

## Referencias bibliográficas

1. Documentación oficial de React: https://react.dev/
2. Documentación oficial de TypeScript: https://www.typescriptlang.org/docs/
3. Documentación de Supabase: https://supabase.com/docs
4. Documentación de Tailwind CSS: https://tailwindcss.com/docs
5. Documentación de Shadcn/UI: https://ui.shadcn.com/docs
6. Documentación de Tanstack Query: https://tanstack.com/query/latest/docs/react
7. Documentación de OpenAI API: https://platform.openai.com/docs/api-reference
8. Documentación de Perplexity API: https://docs.perplexity.ai/
9. Howell, K. (2023). *Modern Frontend Development with React*. O'Reilly Media.
10. Smith, J. (2024). *Building Apps with Supabase*. Packt Publishing.
11. García, M. (2023). *Desarrollo Motriz en la Educación Preescolar*. Editorial Educativa.
12. Johnson, R. (2024). *Edge Functions and Serverless Architecture*. Wiley.
13. López, A. (2023). *Diseño de Interfaces Educativas*. Editorial Técnica.

---

**Nota:** Este manual técnico está sujeto a actualizaciones periódicas para reflejar cambios en la implementación o mejoras en el sistema. La versión más reciente estará disponible en el repositorio oficial del proyecto.
