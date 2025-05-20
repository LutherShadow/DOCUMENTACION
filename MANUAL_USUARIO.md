
# Manual de Usuario - EduApp 

## Índice
1. [Introducción](#introducción)
2. [Requerimientos del Sistema](#requerimientos-del-sistema)
3. [Acceso al Sistema](#acceso-al-sistema)
   - [Inicio de Sesión](#inicio-de-sesión)
   - [Recuperación de Contraseña](#recuperación-de-contraseña)
   - [Registro de Usuario](#registro-de-usuario)
4. [Navegación General](#navegación-general)
5. [Módulos por Rol de Usuario](#módulos-por-rol-de-usuario)
   - [Administradores](#administradores)
   - [Docentes](#docentes)
   - [Padres de Familia](#padres-de-familia)
6. [Gestión de Asistencia](#gestión-de-asistencia)
7. [Permisos de Recogida](#permisos-de-recogida)
8. [Reportes de Desarrollo Motriz](#reportes-de-desarrollo-motriz)
9. [Perfil de Usuario](#perfil-de-usuario)
10. [Notificaciones](#notificaciones)
11. [Preguntas Frecuentes](#preguntas-frecuentes)
12. [Solución de Problemas](#solución-de-problemas)
13. [Contacto y Soporte](#contacto-y-soporte)

## Introducción

Bienvenido a EduApp, un sistema integral de gestión escolar para preescolares diseñado para facilitar la comunicación entre docentes, padres de familia y administradores. Esta plataforma permite gestionar eficientemente la asistencia de estudiantes, solicitudes de permisos, reportes de desarrollo motriz y académico, entre otras funcionalidades.

EduApp nace como respuesta a las necesidades específicas de las instituciones preescolares modernas, donde la comunicación efectiva entre escuela y familia es fundamental para el desarrollo óptimo de los estudiantes. Nuestra plataforma digitaliza y centraliza procesos que tradicionalmente consumían tiempo valioso de docentes y administrativos, permitiéndoles enfocarse en lo más importante: la educación y bienestar de los niños.

Este manual le guiará paso a paso en el uso de todas las características disponibles según su rol dentro del sistema, garantizando una experiencia fluida y productiva. Cada sección está diseñada pensando en las necesidades específicas de cada tipo de usuario, con instrucciones claras y detalladas.

## Requerimientos del Sistema

Para utilizar EduApp de manera óptima, se requiere:

- **Navegador web actualizado**: 
  - Chrome (versión 90 o superior)
  - Firefox (versión 88 o superior)
  - Edge (versión 90 o superior) 
  - Safari (versión 14 o superior)
  
  Los navegadores desactualizados pueden presentar problemas de compatibilidad con algunas funcionalidades.

- **Conexión a Internet**: 
  - Mínimo recomendado: 1 Mbps
  - Óptimo para uso con carga de archivos: 5 Mbps o superior
  - La estabilidad de la conexión es tan importante como la velocidad

- **Dispositivos compatibles**:
  - **Computadoras**:
    - Windows (8.1, 10 o 11)
    - macOS (Catalina 10.15 o superior)
    - Linux (distribuciones principales con soporte actual)
  - **Tablets**:
    - iOS (versión 12 o superior)
    - Android (versión 8.0 o superior)
    - Pantalla mínima recomendada: 7 pulgadas
  - **Smartphones**:
    - iOS (versión 12 o superior)
    - Android (versión 8.0 o superior)

La aplicación es totalmente responsiva, adaptándose a diferentes tamaños de pantalla para garantizar una experiencia fluida en cualquier dispositivo. El diseño de la interfaz se ajusta automáticamente según la resolución de pantalla, optimizando la visualización en dispositivos móviles, tablets o computadoras de escritorio.

Para la carga y descarga de documentos (como identificaciones para permisos, reportes PDF, etc.), se recomienda una conexión estable y una capacidad de almacenamiento disponible de al menos 500MB en su dispositivo.

## Acceso al Sistema

### Inicio de Sesión

La pantalla de inicio de sesión es la puerta de entrada a EduApp, diseñada para ser intuitiva y segura:

1. Ingrese a la URL proporcionada por su institución educativa (generalmente tiene el formato: `https://[nombre-de-su-institución].eduapp.com`)
2. En la pantalla principal, localice el botón "Iniciar Sesión" ubicado en la esquina superior derecha
3. Se abrirá un formulario donde deberá ingresar:
   - Su correo electrónico institucional o personal registrado
   - Su contraseña personal
4. Active la opción "Recordarme" si desea que el sistema guarde su información de acceso (recomendado solo en dispositivos personales)
5. Presione el botón "Ingresar"

![Interfaz de inicio de sesión](https://[url-de-la-imagen-de-login])

El sistema verificará sus credenciales y, si son correctas, será redirigido automáticamente al panel correspondiente a su rol (administrador, docente o padre de familia). Por motivos de seguridad, después de tres intentos fallidos consecutivos, el sistema implementará un tiempo de espera antes de permitir nuevos intentos.

Si utiliza un dispositivo público o compartido, recomendamos cerrar sesión al finalizar su uso para proteger su información personal y la de los estudiantes.

### Recuperación de Contraseña

Si ha olvidado su contraseña, EduApp ofrece un método seguro y eficiente para recuperar el acceso a su cuenta:

1. En la pantalla de inicio de sesión, haga clic en el enlace "¿Olvidó su contraseña?" ubicado debajo del botón de ingreso
2. Se abrirá una nueva pantalla donde deberá:
   - Ingresar el correo electrónico asociado a su cuenta en el sistema
   - Ingresar el número de teléfono registrado en el sistema para verificar su identidad
3. Presione el botón "Verificar Identidad"
4. Si la información proporcionada es correcta, el sistema le mostrará inmediatamente en pantalla una contraseña temporal que podrá utilizar para acceder
5. Una vez dentro del sistema, se recomienda cambiar inmediatamente esta contraseña temporal por una nueva de su elección desde la sección "Mi Perfil" > "Seguridad"

![Interfaz de recuperación de contraseña](https://[url-de-la-imagen-de-recuperacion])

Es importante destacar que este proceso de recuperación **no envía correos electrónicos ni mensajes SMS**. La contraseña temporal se muestra directamente en la pantalla tras verificar exitosamente su identidad mediante el correo y teléfono registrados. Este enfoque garantiza un acceso inmediato sin depender de la recepción de mensajes externos.

La contraseña temporal tiene una validez de 24 horas. Si no la utiliza durante este período, deberá solicitar una nueva.

### Registro de Usuario

El proceso de registro varía según el tipo de usuario que desee crear. EduApp implementa verificaciones específicas para cada rol, garantizando la seguridad de la información y la legitimidad de las cuentas:

**Padres de Familia**:

1. En la pantalla principal, haga clic en el botón "Crear cuenta nueva"
2. Seleccione el rol "Padre/Madre de Familia" en las opciones disponibles
3. Complete el formulario con sus datos personales:
   - Nombre completo
   - Correo electrónico (será su nombre de usuario)
   - Número telefónico (utilizado para verificaciones y recuperación de cuenta)
   - Dirección (opcional)
   - Contacto de emergencia
4. Cree una contraseña segura (debe contener al menos 8 caracteres, incluyendo mayúsculas, minúsculas y números)
5. Acepte los términos y condiciones de uso
6. Envíe el formulario para su revisión
7. Espere la aprobación por parte del administrador, que recibirá automáticamente mediante una notificación

![Interfaz de registro de padres](https://[url-de-la-imagen-de-registro-padres])

**Docentes**:

1. En la pantalla principal, haga clic en "Crear cuenta nueva"
2. Seleccione el rol "Docente" en las opciones disponibles
3. Complete el formulario con sus datos personales y profesionales:
   - Nombre completo
   - Correo electrónico institucional (preferentemente)
   - Información de contacto
   - Grados o grupos a su cargo
   - Especialidad o área de enseñanza
4. Adjunte los documentos solicitados:
   - Identificación oficial (INE, pasaporte, cédula profesional)
   - Título profesional o documento que acredite su formación
   - Carta de nombramiento o contrato (si aplica)
5. Cree una contraseña segura
6. Envíe el formulario para su revisión
7. Espere la aprobación por parte del administrador

![Interfaz de registro de docentes](https://[url-de-la-imagen-de-registro-docentes])

**Administradores**:

Para solicitar una cuenta de administrador, debe seguir un proceso especial con verificaciones adicionales:

1. En la pantalla principal, haga clic en "Crear cuenta nueva"
2. Seleccione el rol "Administrador" en las opciones disponibles
3. Complete el formulario con sus datos personales y profesionales:
   - Nombre completo
   - Correo electrónico institucional (obligatorio)
   - Cargo dentro de la institución
   - Información de contacto
4. Adjunte la documentación requerida que acredite su cargo en la institución:
   - Identificación oficial
   - Nombramiento o designación como administrador
   - Documentación legal de la institución educativa (si es una nueva institución)
5. El sistema enviará un enlace de verificación a su correo institucional
6. Complete el proceso de verificación siguiendo las instrucciones del correo
7. Su solicitud será revisada por el equipo de soporte de EduApp, quienes verificarán la autenticidad de la documentación y la institución
8. Una vez aprobada, recibirá credenciales temporales para acceder a su cuenta

![Interfaz de registro de administradores](https://[url-de-la-imagen-de-registro-admin])

Todas las solicitudes de registro son evaluadas por los administradores del sistema antes de ser aprobadas. Este proceso puede tomar entre 24 y 48 horas hábiles, dependiendo del volumen de solicitudes. El administrador puede solicitar información adicional si lo considera necesario.

## Navegación General

La interfaz de EduApp está diseñada siguiendo principios de usabilidad y experiencia de usuario, para ser intuitiva y fácil de usar incluso para personas con limitada experiencia tecnológica.

### Elementos Comunes de Navegación

Independientemente de su rol en el sistema, encontrará estos elementos de navegación persistentes:

- **Barra de Menú Principal**: 
  - Ubicada en la parte lateral izquierda en pantallas grandes o en la parte superior en dispositivos móviles
  - Proporciona acceso a los diferentes módulos y funcionalidades del sistema
  - Se adapta automáticamente según su rol (administrador, docente o padre de familia)
  - Puede ser colapsada para maximizar el espacio de trabajo

- **Panel de Control (Dashboard)**: 
  - Es la página de inicio que se muestra después de iniciar sesión
  - Presenta un resumen personalizado de la información relevante para cada rol
  - Incluye accesos rápidos a las funciones más utilizadas
  - Muestra notificaciones pendientes y recordatorios importantes

- **Breadcrumbs (Migas de Pan)**: 
  - Ubicados en la parte superior de la pantalla, debajo del encabezado
  - Muestran la ruta de navegación actual (ejemplo: Inicio > Asistencia > Registro)
  - Permiten regresar fácilmente a secciones anteriores con un solo clic
  - Ayudan a mantener la orientación dentro de la estructura del sistema

- **Botones de Acción**: 
  - Claramente identificados con colores distintivos según su función
    - Verde: acciones de creación o aprobación
    - Azul: acciones de información o navegación
    - Rojo: acciones de eliminación o rechazo
    - Gris: acciones secundarias o de cancelación
  - Incluyen iconos intuitivos además de texto para mejorar la comprensión

- **Filtros y Búsquedas**: 
  - Presentes en todas las vistas con listas o tablas de datos
  - Permiten buscar por texto libre o filtrar por categorías predefinidas
  - Se actualiza la información en tiempo real mientras se escriben los términos de búsqueda
  - Incluyen opciones avanzadas para filtrado multivariable

![Interfaz de navegación principal](https://[url-de-la-imagen-de-navegacion])

### Adaptabilidad a Dispositivos

EduApp se adapta automáticamente al dispositivo que esté utilizando:

- **En computadoras de escritorio**:
  - Menú lateral expandido y siempre visible
  - Mayor cantidad de información visible simultáneamente
  - Tablas de datos completas con todas las columnas disponibles

- **En tablets**:
  - Menú lateral colapsable con botón de expansión
  - Vista optimizada para interacción táctil
  - Elementos de interfaz ligeramente más grandes para facilitar la interacción

- **En smartphones**:
  - Menú convertido en hamburguesa desplegable desde la parte superior
  - Diseño en formato de tarjetas para mejor visualización de datos
  - Funcionalidades adaptadas para pantallas pequeñas sin sacrificar capacidades

Para cambiar entre vistas o personalizar su experiencia, busque el icono de configuración (⚙️) en la esquina superior derecha de la pantalla.

## Módulos por Rol de Usuario

EduApp ofrece diferentes módulos y funcionalidades según el rol del usuario, garantizando que cada persona tenga acceso solo a las herramientas necesarias para su función específica:

### Administradores

El panel de administrador es el centro de control general de la institución educativa, brindando acceso a todas las funcionalidades de configuración y supervisión del sistema:

- **Gestión de Usuarios**: 
  - Crear, editar y eliminar cuentas de usuarios (docentes, padres, administradores)
  - Asignar roles y permisos específicos
  - Revisar y aprobar solicitudes de registro pendientes
  - Reiniciar contraseñas en caso de problemas de acceso
  - Ver historial de actividad de los usuarios

- **Gestión de Grupos**: 
  - Crear y administrar grupos de estudiantes por grado, sección o criterios personalizados
  - Asignar docentes responsables a cada grupo
  - Transferir estudiantes entre grupos cuando sea necesario
  - Configurar calendario académico por grupo
  - Generar listas y reportes por grupo

- **Configuración del Sistema**: 
  - Establecer parámetros generales del sistema (horarios, calendarios, períodos académicos)
  - Personalizar formularios de evaluación y reportes
  - Definir políticas de asistencia y justificaciones
  - Configurar notificaciones automáticas
  - Personalizar la apariencia institucional (logotipos, colores)

- **Reportes Generales**: 
  - Generar reportes consolidados de asistencia
  - Analizar tendencias de desempeño académico por grupo, grado o institución
  - Exportar datos estadísticos en múltiples formatos (Excel, PDF, CSV)
  - Visualizar gráficos interactivos de indicadores clave
  - Programar generación automática de reportes periódicos

![Panel de administrador](https://[url-de-la-imagen-de-panel-admin])

El administrador tiene acceso a herramientas avanzadas de análisis y configuración que permiten adaptar el sistema a las necesidades específicas de la institución educativa, garantizando el cumplimiento de normativas y facilitando la toma de decisiones basada en datos.

### Docentes

El panel docente está diseñado para optimizar las tareas diarias de los educadores, proporcionando herramientas especializadas para la gestión educativa:

- **Gestión de Asistencia**: 
  - Registrar y consultar la asistencia diaria de los estudiantes con opciones de presente, ausente, tardanza o justificado
  - Visualizar patrones de asistencia por estudiante o por grupo
  - Generar reportes de asistencia por períodos personalizables
  - Enviar notificaciones automáticas a padres en caso de ausencias
  - Registrar justificaciones médicas o personales

- **Permisos de Recogida**: 
  - Revisar y aprobar/rechazar solicitudes de permisos de recogida
  - Ver historial de permisos por estudiante
  - Consultar la documentación adjunta para verificar identidades
  - Registrar comentarios o condiciones especiales para los permisos
  - Recibir notificaciones de nuevas solicitudes en tiempo real

- **Reportes de Desarrollo Motriz**: 
  - Registrar y consultar el desarrollo motriz de los estudiantes mediante formularios personalizables
  - Utilizar herramientas de evaluación estandarizadas
  - Crear actividades de seguimiento recomendadas
  - Generar visualizaciones del progreso individual y grupal
  - Recibir sugerencias basadas en IA para actividades de refuerzo

- **Comunicación con Padres**: 
  - Enviar mensajes y notificaciones individuales o grupales a los padres de familia
  - Programar recordatorios de eventos o actividades
  - Compartir archivos y recursos educativos
  - Solicitar autorización para actividades especiales
  - Agendar reuniones virtuales o presenciales

![Panel de docente](https://[url-de-la-imagen-de-panel-docente])

Los docentes cuentan con herramientas especializadas para planificación educativa, evaluación continua y comunicación efectiva, permitiéndoles enfocarse en el desarrollo integral de sus estudiantes mientras el sistema se encarga de automatizar tareas administrativas.

### Padres de Familia

El panel de padres está optimizado para proporcionar información clara sobre el desarrollo y actividades de sus hijos, facilitando la comunicación con la institución:

- **Consulta de Asistencia**: 
  - Ver el registro detallado de asistencia de sus hijos
  - Recibir notificaciones automáticas sobre ausencias no justificadas
  - Consultar histórico de asistencia por períodos
  - Enviar justificaciones electrónicas para ausencias
  - Visualizar estadísticas de asistencia mensual y trimestral

- **Solicitud de Permisos**: 
  - Enviar solicitudes de permisos de recogida con antelación
  - Adjuntar documentación de identificación de personas autorizadas
  - Ver el estado de las solicitudes (pendiente, aprobada, rechazada)
  - Recibir notificaciones sobre cambios de estado
  - Consultar historial de permisos solicitados

- **Reportes de Desarrollo Motriz**: 
  - Consultar los reportes detallados de desarrollo motriz de sus hijos
  - Ver el progreso a través del tiempo con gráficas intuitivas
  - Acceder a recomendaciones personalizadas para refuerzo en casa
  - Descargar informes en formato PDF para consulta offline
  - Consultar actividades sugeridas para estimulación motriz

- **Comunicación con Docentes**: 
  - Recibir mensajes y notificaciones de los docentes
  - Solicitar reuniones o consultas personalizadas
  - Consultar calendario de actividades escolares
  - Acceder a recursos educativos compartidos
  - Configurar preferencias de notificación (app, correo electrónico)

![Panel de padres](https://[url-de-la-imagen-de-panel-padres])

El diseño del panel para padres prioriza la claridad y facilidad de uso, proporcionando acceso rápido a la información más relevante sobre sus hijos y facilitando la participación activa en su proceso educativo sin necesidad de conocimientos técnicos avanzados.

## Gestión de Asistencia

El módulo de gestión de asistencia es una herramienta fundamental para el seguimiento diario de los estudiantes, diseñado principalmente para el uso de los docentes, con funcionalidades de consulta para administradores y padres de familia.

### Registro de Asistencia (Docentes)

La interfaz de registro está optimizada para ser rápida y eficiente, ideal para la rutina diaria del aula:

1. **Selección de fecha**:
   - Utilice el calendario interactivo para seleccionar la fecha deseada
   - Por defecto, se muestra la fecha actual
   - Puede registrar o modificar asistencia hasta 7 días en el pasado (configurable por el administrador)
   - Las fechas futuras están deshabilitadas para registro directo

2. **Selección de grupo**:
   - Elija el grupo o grado correspondiente del menú desplegable
   - Si tiene asignado un solo grupo, este se seleccionará automáticamente
   - La lista muestra el total de estudiantes y el porcentaje de asistencia actual

3. **Registro individual**:
   - La tabla principal muestra la lista de estudiantes con fotografía, nombre completo y opciones de asistencia
   - Para cada estudiante, seleccione el estado correspondiente:
     - Presente (verde): Asistió normalmente
     - Ausente (rojo): No asistió a la jornada
     - Justificado (azul): Ausente con justificación previa
     - Tardanza (amarillo): Asistió con retraso (opcional: registrar hora de entrada)
   - Puede añadir notas individuales haciendo clic en el icono de comentario
   - Los cambios se guardan automáticamente al seleccionar cada estado

4. **Acciones masivas**:
   - Utilice los botones de acción rápida para marcar a todos los estudiantes como:
     - Todos presentes
     - Todos ausentes
   - Función de "asistencia habitual" que aplica el patrón de asistencia más común del último mes
   - Confirmación final necesaria para aplicar cambios masivos

![Interfaz de registro de asistencia](https://[url-de-la-imagen-de-asistencia])

### Consulta de Asistencia

La visualización de datos de asistencia varía según el rol del usuario:

**Para docentes**:
- Visualización diaria, semanal, mensual o por periodo personalizado
- Filtros por estudiante específico, estado de asistencia o patrón de ausencias
- Generación de reportes en formato Excel o PDF
- Identificación automática de patrones de ausencias consecutivas o recurrentes
- Estadísticas de asistencia por grupo con gráficos comparativos

**Para administradores**:
- Visión general de asistencia por grupo, grado o toda la institución
- Alertas de grupos con bajo porcentaje de asistencia
- Reportes consolidados para períodos específicos
- Exportación de datos para análisis en sistemas externos
- Tableros de control con indicadores clave de asistencia

**Para padres**:
- Historial de asistencia de sus hijos con código de colores intuitivo
- Notificaciones automáticas en caso de ausencias no justificadas
- Opción para enviar justificaciones electrónicas con documentación adjunta
- Vista de calendario mensual con resumen de asistencia
- Comparativa del estudiante con el promedio de asistencia del grupo (anónima)

La plataforma mantiene un registro histórico completo de la asistencia, permitiendo análisis a largo plazo para identificar tendencias y tomar decisiones informadas sobre intervenciones necesarias.

## Permisos de Recogida

El módulo de permisos de recogida proporciona un sistema seguro y estructurado para gestionar las autorizaciones especiales para que personas diferentes a los tutores habituales puedan recoger a los estudiantes.

### Solicitud de Permisos (Padres)

La interfaz de solicitud está diseñada para garantizar claridad y seguridad en el proceso:

1. **Creación de solicitud**:
   - Acceda a la sección "Permisos de Recogida" en su panel
   - Haga clic en "Nueva Solicitud" para iniciar el proceso
   - Seleccione el estudiante para el cual solicita el permiso (si tiene varios hijos en la institución)

2. **Datos básicos del permiso**:
   - Ingrese la fecha para la que solicita el permiso (debe ser una fecha futura)
   - Especifique la hora aproximada de recogida utilizando el selector de hora
   - Indique el motivo del permiso especial (cita médica, emergencia familiar, etc.)
   - Seleccione si es un permiso para una ocasión única o si será recurrente

3. **Información de la persona autorizada**:
   - Ingrese el nombre completo de la persona que recogerá al estudiante
   - Especifique el parentesco o relación con el estudiante
   - Proporcione un número de contacto
   - Adjunte la documentación requerida:
     - Identificación oficial con fotografía (obligatorio)
     - Carta de autorización firmada (opcional, según política institucional)
     - Cualquier documento adicional requerido por la institución

4. **Previsualización y envío**:
   - Revise toda la información ingresada
   - Confirme que la documentación adjunta es legible y vigente
   - Lea los términos y condiciones específicos para permisos de recogida
   - Envíe la solicitud para revisión del docente o administrador

![Interfaz de solicitud de permisos](https://[url-de-la-imagen-de-solicitud-permiso])

### Aprobación/Rechazo de Permisos (Docentes)

Los docentes cuentan con una interfaz especializada para la gestión eficiente de solicitudes:

1. **Panel de solicitudes**:
   - Las nuevas solicitudes aparecen destacadas con indicador de "Pendiente"
   - Vista en forma de lista con información resumida o tarjetas detalladas
   - Filtros por fecha, estudiante o estado de la solicitud
   - Notificaciones en tiempo real de nuevas solicitudes recibidas

2. **Revisión detallada**:
   - Al seleccionar una solicitud, se muestra toda la información proporcionada
   - Visor integrado de documentos para examinar la identificación adjunta
   - Opción para ampliar imágenes para verificar detalles
   - Historial de permisos previos otorgados a la misma persona (si existe)

3. **Proceso de decisión**:
   - Verificación de la documentación adjunta
   - Comprobación de que la persona autorizada cumple con los requisitos institucionales
   - Consulta de notas especiales sobre el estudiante (si aplican restricciones)
   - Opción para añadir comentarios o condiciones especiales al permiso

4. **Acción sobre la solicitud**:
   - Aprobar: Confirma el permiso y genera un comprobante con código QR para verificación
   - Rechazar: Deniega la solicitud indicando el motivo del rechazo
   - Solicitar más información: Pausa el proceso y solicita documentación adicional
   - Transferir a administración: Escala la decisión a un nivel superior cuando es necesario

Al aprobar o rechazar una solicitud, el sistema envía automáticamente una notificación al padre/madre solicitante con el resultado y, en caso de aprobación, el comprobante digital que deberá presentar la persona autorizada.

![Interfaz de aprobación de permisos](https://[url-de-la-imagen-de-aprobacion-permiso])

### Verificación de Permisos

El día de la recogida, el proceso de verificación es simple y seguro:

1. La persona autorizada se presenta con su identificación oficial
2. El padre/madre puede mostrar el comprobante digital con código QR desde su aplicación
3. El personal encargado escanea el código QR o ingresa el código alfanumérico para verificar:
   - Identidad de la persona autorizada
   - Vigencia del permiso
   - Condiciones especiales si existieran
4. El sistema registra la hora exacta de la recogida y quien verificó el permiso
5. Se marca el permiso como "Utilizado" en el sistema para evitar reutilización

Este proceso garantiza la seguridad de los estudiantes y proporciona un registro auditable de todas las recogidas con permisos especiales.

## Reportes de Desarrollo Motriz

El módulo de reportes de desarrollo motriz es una herramienta especializada que permite a los docentes registrar y dar seguimiento al progreso físico y motriz de los estudiantes, facilitando la detección temprana de áreas de oportunidad y la comunicación efectiva con los padres.

### Registro de Reportes (Docentes)

La plataforma ofrece un sistema completo para evaluación y seguimiento:

1. **Selección de formulario de evaluación**:
   - EduApp incluye formularios prediseñados para diferentes áreas de desarrollo motriz:
     - Motricidad fina
     - Motricidad gruesa
     - Coordinación visomotora
     - Equilibrio y postura
     - Lateralidad
   - Opción para crear formularios personalizados según necesidades específicas
   - Posibilidad de adaptar los criterios de evaluación por edad o grupo

2. **Selección de estudiante y período**:
   - Elija al estudiante que desea evaluar de la lista de su grupo
   - Seleccione el período de evaluación (mensual, bimestral, etc.)
   - Revise evaluaciones anteriores para referencia (opcional)
   - Establezca una línea base comparativa si es la primera evaluación

3. **Completar el formulario**:
   - Para cada criterio de evaluación, seleccione el nivel de desarrollo:
     - Logrado completamente
     - En proceso de desarrollo
     - Requiere más atención
     - No evaluado
   - La interfaz utiliza un sistema de escala numérica complementario (1-5)
   - Posibilidad de adjuntar evidencias (fotos, videos cortos, archivos)
   - Campo para observaciones cualitativas específicas por criterio

4. **Asistente de IA para sugerencias**:
   - Basado en las evaluaciones ingresadas, el sistema sugiere:
     - Actividades de refuerzo para áreas con menor desarrollo
     - Ejercicios específicos para estimulación
     - Recomendaciones para trabajo en casa
   - El docente puede editar, complementar o descartar estas sugerencias
   - Opción para personalizar las recomendaciones según características del estudiante

5. **Finalización y guardado**:
   - Vista previa del reporte completo antes de guardar
   - Espacio para conclusiones generales y recomendaciones
   - Opción para establecer objetivos para la próxima evaluación
   - Guardado automático y generación de versión para padres

![Interfaz de registro de desarrollo motriz](https://[url-de-la-imagen-de-desarrollo])

### Consulta de Reportes

La visualización de los reportes está adaptada según el perfil de usuario:

**Para docentes**:
- Vista consolidada de todos los estudiantes con código de colores por nivel de desarrollo
- Gráficos de evolución individual para cada estudiante a lo largo del tiempo
- Comparativa de desarrollo por áreas específicas
- Identificación automática de estudiantes que requieren atención especial
- Exportación de datos para reuniones de seguimiento pedagógico

**Para padres**:
- Versión simplificada y visualmente clara del reporte de sus hijos
- Gráficos intuitivos de progreso por área de desarrollo
- Explicaciones de cada criterio evaluado y su importancia
- Sección destacada con recomendaciones para refuerzo en casa
- Opción para descargar el reporte en PDF o imprimirlo

**Para administradores**:
- Visión general del desarrollo motriz por grupos y grados
- Detección de tendencias o áreas que requieren intervención institucional
- Comparativa entre grupos del mismo grado
- Reportes estadísticos para evaluación de programas educativos
- Información para toma de decisiones curriculares

El sistema archiva todos los reportes creando un historial completo del desarrollo del estudiante durante su trayectoria en la institución, facilitando el seguimiento longitudinal y la detección de patrones de desarrollo.

## Perfil de Usuario

Todos los usuarios de EduApp cuentan con un perfil personalizable que centraliza su información y preferencias dentro del sistema. La gestión del perfil es intuitiva y permite a cada usuario mantener sus datos actualizados.

### Información de Perfil

Cada tipo de usuario puede visualizar y editar diferentes aspectos de su perfil:

**Información Común (todos los usuarios)**:
- Datos personales básicos (nombre, correo electrónico)
- Foto de perfil
- Preferencias de notificación
- Opciones de visualización y accesibilidad
- Configuración de seguridad

**Información Específica por Rol**:

*Padres de Familia*:
- Listado de hijos vinculados a su cuenta
- Información de contacto de emergencia
- Documentos de identificación registrados
- Preferencias de comunicación
- Registro de permisos solicitados

*Docentes*:
- Grupos asignados
- Especialidad o área de enseñanza
- Horario de atención a padres
- Logros y certificaciones
- Estadísticas de actividad en la plataforma

*Administradores*:
- Permisos y áreas de administración
- Registro de actividades administrativas
- Configuraciones institucionales
- Accesos a módulos especializados
- Opciones de configuración avanzada

### Edición de Perfil

El proceso de actualización de información personal es sencillo y seguro:

1. Acceda a la sección "Mi Perfil" en el menú principal:
   - En computadoras, a través del botón con su nombre o foto en la esquina superior derecha
   - En dispositivos móviles, desde el menú hamburguesa, opción "Mi Perfil"

2. En la pantalla de perfil, encontrará secciones claramente diferenciadas:
   - Información personal
   - Contacto
   - Seguridad
   - Preferencias
   - Vinculaciones (específico para padres)

3. Para modificar cualquier campo:
   - Haga clic en el botón "Editar" junto a la sección correspondiente
   - Realice los cambios necesarios en los campos habilitados
   - Algunos cambios críticos pueden requerir verificación adicional
   - Presione "Guardar" para confirmar los cambios

![Interfaz de perfil de usuario](https://[url-de-la-imagen-de-perfil])

### Cambio de Contraseña

La seguridad de las cuentas es prioritaria, y el proceso de cambio de contraseña está diseñado para ser seguro y directo:

1. Desde la sección "Mi Perfil", navegue a la pestaña "Seguridad"
2. Haga clic en el botón "Cambiar contraseña"
3. En el formulario que aparece:
   - Ingrese su contraseña actual (para verificación)
   - Ingrese su nueva contraseña
   - Confirme su nueva contraseña repitiendo la misma
4. El sistema verificará:
   - Que la contraseña actual sea correcta
   - Que la nueva contraseña cumpla con los requisitos de seguridad:
     - Mínimo 8 caracteres
     - Incluir al menos una mayúscula
     - Incluir al menos un número
     - Incluir al menos un carácter especial
   - Que ambas entradas de la nueva contraseña coincidan
5. Una vez validada la información, se aplicará el cambio inmediatamente

Por seguridad, después de cambiar la contraseña, el sistema enviará una notificación de confirmación y podría cerrar todas las sesiones activas requiriendo un nuevo inicio de sesión con la contraseña actualizada.

## Notificaciones

El sistema de notificaciones de EduApp mantiene a todos los usuarios informados sobre eventos relevantes, actualizaciones y acciones pendientes, garantizando una comunicación fluida entre todos los actores del proceso educativo.

### Tipos de Notificaciones

Las notificaciones se clasifican por importancia y tipo, permitiendo una gestión eficiente:

- **Notificaciones Críticas** (rojo):
  - Nuevas solicitudes de permisos de recogida pendientes de revisión
  - Alertas de ausencias no justificadas
  - Cambios importantes en el calendario escolar
  - Emergencias o comunicados prioritarios de la dirección
  - Problemas de seguridad o acceso a la cuenta

- **Notificaciones Importantes** (amarillo):
  - Aprobación/rechazo de permisos de recogida
  - Nuevos reportes de desarrollo motriz disponibles
  - Mensajes directos de docentes o padres
  - Recordatorios de eventos próximos (24h antes)
  - Actualizaciones en documentación requerida

- **Notificaciones Informativas** (azul):
  - Nuevos recursos educativos compartidos
  - Recordatorios generales de eventos futuros
  - Actualizaciones del sistema
  - Consejos y recomendaciones educativas
  - Confirmaciones de acciones realizadas en el sistema

### Gestión de Notificaciones

Cada usuario puede personalizar cómo recibe y gestiona sus notificaciones:

1. **Centro de notificaciones**:
   - Accesible desde el icono de campana en la barra superior
   - Muestra las notificaciones más recientes con código de colores por importancia
   - Permite marcar como leídas individualmente o todas a la vez
   - Ofrece filtros por tipo, fecha o estado (leídas/no leídas)
   - Mantiene historial de notificaciones anteriores

2. **Configuración de preferencias**:
   - Desde "Mi Perfil" > "Preferencias de notificación"
   - Permite seleccionar qué tipos de notificaciones recibir
   - Opciones de recepción:
     - En la aplicación (siempre activas para notificaciones críticas)
     - Correo electrónico
     - SMS (para algunas notificaciones críticas, según configuración institucional)
   - Horarios preferentes para notificaciones no críticas

3. **Notificaciones en tiempo real**:
   - Aparecen como pequeñas alertas en la esquina de la pantalla
   - Permanecen visibles brevemente y se almacenan en el centro de notificaciones
   - Incluyen acciones rápidas cuando es aplicable (aprobar, ver, responder)
   - Se sincronizan automáticamente entre dispositivos del mismo usuario

![Sistema de notificaciones](https://[url-de-la-imagen-de-notificaciones])

### Recordatorios y Alertas Automatizadas

El sistema genera automáticamente ciertas notificaciones basadas en eventos o condiciones:

- Recordatorios de eventos programados en el calendario
- Alertas por ausencias consecutivas de estudiantes
- Avisos de solicitudes pendientes de revisión
- Recordatorios de tareas administrativas periódicas
- Notificaciones de finalización de plazos

Los administradores pueden configurar notificaciones institucionales adicionales según las necesidades específicas del centro educativo.

## Preguntas Frecuentes

Esta sección responde a las dudas más comunes que pueden surgir durante el uso de EduApp:

### ¿Cómo recupero mi contraseña si la he olvidado?
No recibirá ningún correo o mensaje para recuperar su contraseña. El sistema le proporcionará una contraseña temporal directamente en la pantalla después de verificar su identidad mediante el correo electrónico y número de teléfono registrados en el sistema. Esta contraseña temporal debe cambiarse inmediatamente después de ingresar al sistema por motivos de seguridad. El proceso está diseñado para ser inmediato y no depende de la recepción de mensajes externos.

### ¿Cómo puedo crear una cuenta de administrador?
Las cuentas de administrador requieren un proceso especial de verificación. Debe completar el formulario seleccionando el rol de administrador y adjuntar documentación que acredite su cargo. El sistema enviará un enlace de verificación a su correo institucional para completar el proceso. Posteriormente, su solicitud será revisada por el equipo de soporte de EduApp antes de ser aprobada. Este proceso adicional garantiza la seguridad de la información institucional.

### ¿Puedo utilizar la aplicación en mi teléfono móvil?
Sí, EduApp está diseñada con un enfoque responsivo que se adapta a diferentes dispositivos. Puede acceder desde cualquier smartphone con un navegador actualizado y conexión a internet. La experiencia de usuario está optimizada para pantallas pequeñas, reorganizando los elementos para facilitar la navegación táctil. Todas las funcionalidades esenciales están disponibles en la versión móvil, aunque algunas características administrativas avanzadas pueden ser más cómodas de utilizar en pantallas más grandes.

### ¿Cómo vinculo a mi hijo/a con mi cuenta de padre/madre?
Como padre o madre, después de crear y verificar su cuenta, debe ir a la sección "Mis Hijos" en su panel de control y hacer clic en "Vincular Estudiante". Allí podrá buscar a su hijo/a por nombre o grupo, y solicitar la vinculación. Esta solicitud será revisada y aprobada por un administrador o docente, quienes verificarán la legitimidad de la relación parental. Una vez aprobada, podrá ver toda la información relevante de su hijo/a en su panel principal.

### ¿Los docentes pueden ver todos los estudiantes del centro educativo?
Los docentes solo tienen acceso a los estudiantes asignados a sus grupos o grados. No pueden ver información de estudiantes que no están bajo su responsabilidad directa. Esta restricción garantiza la confidencialidad de los datos y cumple con regulaciones de protección de información. Si un docente necesita acceder temporalmente a información de otro grupo (por sustituciones, evaluaciones especiales, etc.), un administrador puede otorgar permisos temporales específicos.

### ¿Cómo puedo reportar un problema técnico?
Si encuentra algún problema técnico, utilice la opción "Soporte Técnico" disponible en el menú principal. Describa detalladamente el problema, incluyendo los pasos que realizó antes de que ocurriera. También puede adjuntar capturas de pantalla que ayuden a identificar el problema. El equipo de soporte recibirá su reporte y se comunicará con usted a través del sistema de mensajes internos o por el correo electrónico registrado. Para problemas críticos que impidan el acceso, disponemos de un correo de soporte alternativo: soporte@eduapp.com.

### ¿Con qué frecuencia se actualizan los reportes de desarrollo motriz?
Los reportes de desarrollo motriz se actualizan según el cronograma establecido por cada institución educativa. Generalmente, se realizan evaluaciones mensuales o bimestrales. Los padres reciben notificaciones cuando hay nuevos reportes disponibles. La frecuencia exacta puede consultarse en el calendario académico visible en el panel de control. Si requiere una evaluación adicional fuera del cronograma regular, puede solicitarla directamente al docente a través del sistema de mensajes.

### ¿Puedo solicitar múltiples permisos de recogida para diferentes personas?
Sí, puede registrar múltiples personas autorizadas para recoger a su hijo/a. Cada permiso debe incluir la información completa de la persona y el documento de identidad correspondiente. Estos permisos pueden ser permanentes o para fechas específicas. El sistema permite gestionar una "lista blanca" de personas autorizadas recurrentes (como abuelos o tíos) para agilizar futuras solicitudes. Todas las personas autorizadas deben presentar identificación oficial al momento de la recogida para verificación.

### ¿Qué hago si no puedo cargar un documento o imagen en el sistema?
Si tiene problemas para cargar documentos, verifique lo siguiente:
1. El formato del archivo debe ser compatible (JPG, PNG o PDF en la mayoría de casos)
2. El tamaño no debe exceder 5MB por archivo
3. Su conexión a internet debe ser estable durante la carga
4. El navegador debe estar actualizado y con JavaScript habilitado

Si los problemas persisten, puede intentar comprimir el archivo, usar otro navegador o contactar al soporte técnico. Para documentos urgentes, consulte con la administración sobre métodos alternativos de entrega mientras se resuelve el problema técnico.

## Solución de Problemas

A continuación, se presentan soluciones a los problemas más comunes que pueden surgir al utilizar EduApp:

### Problemas de Inicio de Sesión

Si tiene dificultades para acceder al sistema, verifique los siguientes aspectos:

**Credenciales incorrectas**:
- Verifique que está utilizando el correo electrónico exacto con el que se registró.
- Las contraseñas distinguen entre mayúsculas y minúsculas; verifique que no tenga activado el bloqueo de mayúsculas.
- Si ha cambiado recientemente su contraseña, asegúrese de estar utilizando la nueva.
- Si ha olvidado su contraseña, utilice la opción "¿Olvidó su contraseña?" en la pantalla de inicio de sesión.

**Cuenta bloqueada**:
- Después de varios intentos fallidos consecutivos, las cuentas pueden bloquearse temporalmente por seguridad.
- Espere 30 minutos antes de intentar nuevamente o utilice la recuperación de contraseña.
- Si el bloqueo persiste, contacte al administrador de su institución.

**Problemas técnicos**:
- Limpie la caché y las cookies de su navegador.
- Intente acceder desde un navegador diferente o en modo incógnito.
- Verifique su conexión a internet intentando acceder a otros sitios web.
- Si utiliza redes corporativas o escolares, consulte si hay restricciones de firewall activas.

### Problemas de Navegación

Si encuentra dificultades para navegar por la aplicación:

**Interfaz incompleta o mal visualizada**:
- Utilice los breadcrumbs para regresar a secciones anteriores en caso de páginas incompletas.
- Verifique que su navegador esté actualizado a la versión más reciente.
- Ajuste el zoom de su navegador (Ctrl + o Ctrl -) para mejorar la visualización.
- En dispositivos móviles, asegúrese de visualizar la página en modo vertical para optimizar la experiencia.

**Elementos no funcionan correctamente**:
- Limpie la caché y las cookies de su navegador.
- Desactive temporalmente extensiones o complementos que puedan interferir.
- Intente recargar la página presionando F5 o el botón de recarga.
- Cierre sesión completamente y vuelva a iniciar sesión.

### Problemas de Visualización

Si los elementos visuales no se muestran correctamente:

**Problemas de carga**:
- Verifique que su conexión a internet sea estable (mínimo 1 Mbps).
- Espere unos segundos si las imágenes o gráficos tardan en cargar.
- Intente recargar la página para completar la carga de recursos visuales.
- Si usa conexiones móviles, verifique si tiene restricciones de datos activadas.

**Problemas de resolución**:
- Ajuste la resolución de su pantalla a los valores recomendados.
- En pantallas muy pequeñas, considere utilizar el modo horizontal para tablas y gráficos.
- Utilice la función de zoom del navegador para ajustar el tamaño de los elementos.
- En dispositivos táctiles, use los gestos de pellizcar para acercar áreas específicas.

### Problemas de Funcionalidad

Si alguna característica específica no funciona como se espera:

**Formularios que no se envían**:
- Verifique que todos los campos obligatorios estén completados.
- Revise los formatos requeridos (fechas, números de teléfono, etc.).
- Asegúrese de que los archivos adjuntos cumplan con las restricciones de tamaño y formato.
- Si persiste, tome nota del error exacto que aparece y contacte a soporte técnico.

**Reportes o tablas sin datos**:
- Verifique que haya seleccionado correctamente los filtros o parámetros.
- Confirme que existan datos para el período o criterios seleccionados.
- Intente ampliar el rango de fechas o modificar los filtros aplicados.
- Si está seguro de que deberían existir datos, contacte al administrador para verificar permisos.

## Contacto y Soporte

Si necesita ayuda adicional o tiene alguna pregunta que no ha sido respondida en este manual, puede contactar al equipo de soporte de EduApp a través de los siguientes medios:

### Canales de Soporte

- **Soporte en Aplicación**:
  - Acceda a "Ayuda y Soporte" desde el menú principal
  - Utilice el chat en vivo disponible en días hábiles de 9:00 AM a 5:00 PM
  - Envíe un ticket detallado a través del formulario de contacto integrado
  - Consulte la base de conocimientos y tutoriales disponibles

- **Correo Electrónico**:
  - Soporte general: soporte@eduapp.com
  - Soporte técnico: tecnico@eduapp.com
  - Facturación y licencias: facturacion@eduapp.com
  - Tiempo de respuesta habitual: 24-48 horas hábiles

- **Teléfono**:
  - Línea general: +1-555-123-4567
  - Soporte técnico prioritario: +1-555-987-6543
  - Horario: Lunes a viernes de 9:00 AM a 5:00 PM (hora local)

- **Recursos Adicionales**:
  - Centro de ayuda en línea: [ayuda.eduapp.com](https://ayuda.eduapp.com)
  - Videotutoriales: Canal oficial de YouTube "EduApp Tutoriales"
  - Webinars mensuales para nuevas características (previa inscripción)
  - Comunidad de usuarios: [comunidad.eduapp.com](https://comunidad.eduapp.com)

### Información Necesaria para Reportar Problemas

Para agilizar la resolución de problemas, tenga la siguiente información preparada:

1. **Datos de identificación**:
   - Nombre de usuario y correo electrónico
   - Rol en el sistema (administrador, docente, padre de familia)
   - Nombre de la institución educativa

2. **Detalles del problema**:
   - Descripción clara y concisa del problema
   - Pasos para reproducir el error
   - Fecha y hora exacta en que ocurrió
   - Sección o funcionalidad específica donde se presenta

3. **Información técnica**:
   - Dispositivo utilizado (computadora, tablet, smartphone)
   - Sistema operativo y versión
   - Navegador y versión
   - Capturas de pantalla o videos que muestren el problema (cuando sea posible)

El equipo de soporte está comprometido a brindarle la mejor asistencia posible, priorizando los casos según su impacto y urgencia. Para situaciones críticas que afecten la operación de toda la institución, disponemos de un protocolo de escalamiento para atención inmediata.

---

Este manual de usuario está diseñado para evolucionar junto con EduApp. Las actualizaciones y nuevas funcionalidades se documentarán oportunamente, y este manual se mantendrá al día para reflejar siempre las características más recientes del sistema.
