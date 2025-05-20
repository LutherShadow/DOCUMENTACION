
# Manual Técnico - EduApp 

## Índice
1. [Introducción](#introducción)
2. [Arquitectura](#arquitectura)
3. [Estructura del Proyecto](#estructura-del-proyecto)
4. [Componentes Principales](#componentes-principales)
5. [Gestión de Estado](#gestión-de-estado)
6. [Autenticación](#autenticación)
7. [Integración con Supabase](#integración-con-supabase)
8. [Módulos Funcionales](#módulos-funcionales)
   - [Asistencia](#módulo-de-asistencia)
   - [Permisos de Recogida](#módulo-de-permisos-de-recogida)
   - [Reportes de Desarrollo Motriz](#módulo-de-reportes-de-desarrollo-motriz)
   - [Gestión de Usuarios](#módulo-de-gestión-de-usuarios)
9. [Utilidades y Helpers](#utilidades-y-helpers)
10. [Estilos y UI](#estilos-y-ui)
11. [Rendimiento y Optimización](#rendimiento-y-optimización)
12. [Buenas Prácticas Implementadas](#buenas-prácticas-implementadas)

## Introducción

EduApp es un sistema de gestión escolar para preescolares, desarrollado con React, TypeScript, Vite y Supabase. Está diseñado siguiendo una arquitectura de componentes modular que separa claramente la lógica de negocio de la presentación.

La aplicación implementa un conjunto de funcionalidades clave para facilitar la gestión escolar:

- Registro y seguimiento de asistencia de estudiantes
- Gestión de permisos de recogida
- Evaluación y seguimiento del desarrollo motriz
- Administración de usuarios (docentes, padres, administradores)

Este manual técnico explica detalladamente la implementación de cada uno de estos aspectos.

## Arquitectura

La aplicación sigue una arquitectura basada en componentes con una clara separación de responsabilidades:

- **Componentes de presentación (UI)**: Gestionan la interfaz de usuario y eventos de usuario
- **Hooks personalizados**: Encapsulan la lógica de negocio y estado
- **Servicios**: Manejan interacciones con APIs externas (principalmente Supabase)
- **Utilidades**: Proporcionan funciones auxiliares reutilizables

La comunicación con el backend se realiza a través de la API de Supabase, que proporciona servicios de:
- Autenticación
- Base de datos
- Almacenamiento
- Funciones serverless

## Estructura del Proyecto

El proyecto sigue una estructura organizada por características y roles:

```
/src
  /components        # Componentes compartidos reutilizables
  /hooks             # Hooks personalizados para lógica compartida
  /lib               # Bibliotecas y utilidades
    /supabase        # Cliente y tipos de Supabase
  /pages             # Páginas por rol de usuario
    /admin           # Interfaces para administradores
    /parent          # Interfaces para padres
    /teacher         # Interfaces para docentes
  /contexts          # Contextos de React para estado global
  /utils             # Funciones utilitarias
  /integrations      # Código para integraciones externas
```

## Componentes Principales

### Estructura de Componentes

La aplicación implementa un enfoque basado en componentes con las siguientes categorías:

1. **Componentes de página**: Representan páginas completas (ejemplo: `AttendancePage.tsx`)
2. **Componentes de características**: Implementan funcionalidades específicas (ejemplo: `AttendanceTable.tsx`)
3. **Componentes UI reutilizables**: Elementos UI compartidos (ejemplo: componentes de shadcn/ui)
4. **Componentes contenedores**: Manejan la lógica de obtención de datos y la pasan a componentes de presentación

### Sistema de Componentes

Los componentes siguen un patrón donde la lógica se separa de la presentación:

```tsx
// Ejemplo de componente de presentación (src/components/attendance/AttendanceTable.tsx)
const AttendanceTable = ({ students, onStatusChange }: AttendanceTableProps) => {
  // Maneja solo la representación y eventos de usuario
  return (
    <Table>
      {/* Renderizado de componentes UI */}
    </Table>
  );
};

// Ejemplo de hook con lógica de negocio (src/pages/teacher/attendance/hooks/useAttendanceState.ts)
export const useAttendanceState = () => {
  const [date, setDate] = useState<Date | undefined>(new Date());
  const [selectedGrade, setSelectedGrade] = useState<string>("all");
  // Lógica de filtrado y estado
  
  return {
    // Valores y funciones exportadas
  };
};
```

## Gestión de Estado

### Hooks Personalizados

Los hooks personalizados encapsulan la lógica de negocio y la gestión de estado:

```typescript
// src/pages/teacher/motor-skills/hooks/useFormState.ts
export const useFormState = () => {
  const [reportType, setReportType] = useState<"individual" | "group">("individual");
  const [selectedStudent, setSelectedStudent] = useState("");
  // Más estado y lógica
  
  return {
    // Valores y funciones exportadas
  };
};
```

Esta implementación sigue el patrón de hooks personalizados para:
1. **Encapsular lógica compleja**: Toda la lógica relacionada se mantiene en un solo lugar
2. **Facilitar la reutilización**: El mismo hook puede usarse en múltiples componentes 
3. **Mejorar la testabilidad**: La lógica puede probarse de forma aislada

### Contextos

Para estado global compartido entre componentes no relacionados directamente, se utilizan contextos:

```tsx
// Ejemplo conceptual de un contexto de autenticación (no presente en el código actual)
const AuthContext = createContext<AuthContextType | undefined>(undefined);

export const AuthProvider = ({ children }: { children: React.ReactNode }) => {
  const [user, setUser] = useState<User | null>(null);
  
  // Lógica de autenticación...
  
  return (
    <AuthContext.Provider value={{ user, login, logout }}>
      {children}
    </AuthContext.Provider>
  );
};
```

## Autenticación

La aplicación utiliza el sistema de autenticación de Supabase mediante JWT (JSON Web Tokens).

### Flujo de Autenticación

1. **Inicio de sesión**: El usuario ingresa credenciales, que se envían a Supabase
2. **Validación de token**: Supabase autentica y devuelve un token JWT
3. **Almacenamiento local**: El token se almacena en localStorage mediante el cliente de Supabase
4. **Autorización de solicitudes**: El token se incluye automáticamente en las cabeceras de solicitudes subsiguientes

### Implementación

El archivo `src/hooks/useAuth.ts` (no mostrado en el código proporcionado) típicamente gestiona:
- Inicio/cierre de sesión
- Persisntencia de sesión
- Cambios de estado de autenticación

```typescript
// Ejemplo conceptual de hook de autenticación
export const useAuth = () => {
  const [user, setUser] = useState<User | null>(null);
  
  useEffect(() => {
    // Recuperar sesión existente
    supabase.auth.getSession().then(({ data: { session } }) => {
      setUser(session?.user ?? null);
    });
    
    // Suscribirse a cambios de sesión
    const { data: { subscription } } = supabase.auth.onAuthStateChange(
      (event, session) => {
        setUser(session?.user ?? null);
      }
    );
    
    return () => subscription.unsubscribe();
  }, []);
  
  // Funciones de inicio/cierre de sesión
  
  return { user, login, logout };
};
```

## Integración con Supabase

Supabase proporciona la infraestructura backend para la aplicación.

### Cliente de Supabase

El cliente se configura en `src/integrations/supabase/client.ts`:

```typescript
// Configuración del cliente Supabase
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

### Operaciones con la Base de Datos

Las interacciones con la base de datos se realizan a través del cliente Supabase:

```typescript
// Ejemplo de operación de lectura
const { data, error } = await supabase
  .from('students')
  .select('*')
  .eq('teacher_id', userId);

// Ejemplo de operación de escritura
const { error } = await supabase
  .from('motor_activity_responses')
  .insert({
    form_id: selectedForm,
    student_id: selectedStudent,
    response_data: {
      values: formResponses,
      observations: observations,
      ai_suggestions: aiSuggestions
    }
  });
```

### Cabeceras de Autenticación

La aplicación utiliza funciones auxiliares para aplicar cabeceras de autenticación a las peticiones:

```typescript
// src/lib/supabase/client/headers-utils.ts (conceptual)
export const applyAuthHeaders = async (query: any) => {
  const headers = getAuthHeaders();
  return query.headers(headers);
};
```

Estas funciones garantizan que:
1. Todas las solicitudes incluyan las credenciales necesarias
2. El usuario solo pueda acceder a los datos autorizados según las políticas RLS
3. Se mantenga una forma consistente de autenticación en toda la aplicación

## Módulos Funcionales

### Módulo de Asistencia

El módulo de asistencia permite a los docentes gestionar la asistencia diaria de los estudiantes.

#### Componentes Principales

1. **AttendanceTable**: (`src/components/attendance/AttendanceTable.tsx`) - Muestra la tabla de estudiantes con su estado de asistencia.

```tsx
// Componente que renderiza la tabla de asistencia
const AttendanceTable = ({ students, onStatusChange }: AttendanceTableProps) => {
  // Implementación que muestra una tabla interactiva para registrar asistencia
}
```

2. **DateAndFilters**: (`src/components/attendance/DateAndFilters.tsx`) - Proporciona un selector de fecha y filtros.

3. **QuickActions**: (`src/components/attendance/QuickActions.tsx`) - Ofrece acciones rápidas de registro masivo e individual.

#### Lógica de Negocio

La lógica de filtrado y manipulación de estado se gestiona en `src/pages/teacher/attendance/hooks/useAttendanceState.ts`:

```typescript
export const useAttendanceState = () => {
  const [date, setDate] = useState<Date | undefined>(new Date());
  const [selectedGrade, setSelectedGrade] = useState<string>("all");
  const [selectedGroup, setSelectedGroup] = useState<string>("all");
  const [searchTerm, setSearchTerm] = useState("");

  // Implementación de lógica de filtrado
  const filterStudents = (students: StudentWithAttendance[]) => {
    return students.filter((student) => {
      const matchesGrade = selectedGrade === "all" || student.grade === selectedGrade;
      const matchesGroup = selectedGroup === "all" || student.group_name === selectedGroup;
      const matchesSearch = `${student.first_name} ${student.last_name}`
        .toLowerCase()
        .includes(searchTerm.toLowerCase());
      return matchesGrade && matchesGroup && matchesSearch;
    });
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

#### Flujo de Datos

1. El usuario selecciona una fecha y filtros (grado, grupo, búsqueda)
2. El hook `useAttendanceState` filtra los estudiantes según los criterios
3. Los estudiantes filtrados se pasan al componente `AttendanceTable`
4. El usuario puede cambiar el estado de asistencia a través de selectores
5. Las acciones de registro masivo o individual se ejecutan mediante `QuickActions`

### Módulo de Permisos de Recogida

Este módulo permite a los padres solicitar permisos para recoger a sus hijos y a los docentes gestionarlos.

#### Componentes Principales

1. **PermissionCard**: (`src/components/permissions/PermissionCard.tsx`) - Muestra un permiso individual.
2. **FileUpload**: (`src/components/permissions/FileUpload.tsx`) - Gestiona la carga de documentos de identificación.
3. **StudentSelect**: (`src/components/permissions/StudentSelect.tsx`) - Selector de estudiantes para los permisos.

#### Lógica de Formularios

La validación de formularios se implementa mediante Zod (`src/components/permissions/schema.ts`):

```typescript
// Esquema conceptual para validación de formularios de permiso
export const permissionSchema = z.object({
  studentId: z.string().min(1, "Seleccione un estudiante"),
  date: z.date({
    required_error: "Seleccione una fecha",
  }),
  time: z.string().min(1, "Ingrese una hora"),
  identificationFile: z.string().min(1, "Suba un documento de identificación"),
});
```

#### Flujo de Datos

1. El padre completa un formulario con detalles del permiso (estudiante, fecha, hora)
2. Sube un documento de identificación mediante `FileUpload`
3. El formulario se valida con Zod antes del envío
4. Los datos se envían a Supabase para su almacenamiento
5. Los docentes ven las solicitudes pendientes y pueden aprobarlas o rechazarlas

### Módulo de Reportes de Desarrollo Motriz

Este módulo permite a los docentes registrar evaluaciones del desarrollo motriz de los estudiantes.

#### Componentes y Hooks

1. **useReportForm**: (`src/pages/teacher/motor-skills/hooks/reports/useReportForm.ts`) - Gestiona el estado del formulario de reporte.

```typescript
export const useReportForm = () => {
  // Uso del hook de estado del formulario
  const {
    reportType, setReportType,
    selectedStudent, setSelectedStudent,
    // Más estado del formulario...
  } = useFormState();

  // Uso de hooks para obtención de campos y envío
  const { fetchFormFields } = useFormFieldsFetcher(setFormFields, setFormResponses);
  const { saveFormResponses } = useFormSubmission(setIsSaving, setFormResponses, setObservations);

  // Función para manejar el guardado del formulario
  const handleSaveForm = async (aiSuggestions: string, selectedStudents: string[] = []) => {
    return saveFormResponses(
      reportType,
      selectedForm,
      selectedStudent,
      selectedStudents,
      observations,
      formResponses,
      aiSuggestions
    );
  };

  return {
    // Valores y funciones exportadas
  };
};
```

2. **useFormSubmission**: (`src/pages/teacher/motor-skills/hooks/reports/useFormSubmission.ts`) - Maneja la lógica de envío de formularios.

3. **useAISuggestions**: (`src/pages/teacher/motor-skills/hooks/reports/useAISuggestions.ts`) - Integra funcionalidad de IA para sugerencias.

#### Flujo de Trabajo

La lógica de los reportes de desarrollo motriz se distribuye en varios hooks especializados:

1. **Gestión de estado**: `useFormState` mantiene el estado del formulario (estudiante seleccionado, tipo de reporte, etc.)
2. **Obtención de campos**: `useFormFieldsFetcher` carga la estructura de campos del formulario desde Supabase
3. **Generación de sugerencias**: `useAISuggestions` obtiene sugerencias de IA basadas en las observaciones del docente
4. **Envío de datos**: `useFormSubmission` maneja la persistencia de las respuestas en Supabase

El flujo completo es:
1. El docente selecciona un tipo de reporte (individual o grupal)
2. Selecciona un estudiante o grupo de estudiantes
3. Selecciona un formulario de actividad
4. Completa las respuestas y observaciones
5. Opcionalmente solicita sugerencias de IA
6. Guarda el formulario, que se procesa mediante `saveFormResponses`

### Módulo de Gestión de Usuarios

Este módulo permite la gestión de perfiles de usuario y la vinculación entre padres e hijos.

#### Componentes y Hooks

1. **useLinkChild**: (`src/components/parent/hooks/useLinkChild.ts`) - Permite a los padres vincularse con sus hijos.

```typescript
export const useLinkChild = (parentId: string, onChildAdded: (child: Child) => void, onClose: () => void) => {
  const handleLinkChild = async (student: Student) => {
    try {
      // Actualizar el estudiante para asignarle el padre
      const { error } = await supabase
        .from("students")
        .update({ parent_id: parentId })
        .eq("id", student.id);

      if (error) throw error;

      // Informar al componente padre sobre el éxito
      onChildAdded({
        id: student.id,
        name: `${student.first_name} ${student.last_name}`,
        grade: student.grade,
        group: student.group_name
      });
      
      toast.success(`${student.first_name} ${student.last_name} añadido como hijo/a`);
      onClose();
    } catch (error) {
      console.error("Error al vincular estudiante:", error);
      toast.error("Error al añadir hijo/a");
    }
  };

  return { handleLinkChild };
};
```

2. **useStudentSearch**: (`src/components/parent/hooks/useStudentSearch.ts`) - Permite buscar estudiantes para vincular.

3. **FileUploadWithPreview**: (`src/components/shared/FileUploadWithPreview.tsx`) - Gestiona la carga de imágenes de perfil.

#### Flujo de Vinculación Padre-Hijo

1. El padre accede a la opción de vincular hijo
2. Utiliza `useStudentSearch` para buscar al estudiante por nombre, grado o grupo
3. Selecciona al estudiante de la lista filtrada
4. `useLinkChild` actualiza la relación en la base de datos mediante Supabase
5. La interfaz se actualiza para mostrar al nuevo hijo vinculado

## Utilidades y Helpers

### Cliente de Supabase Mejorado

El archivo `src/integrations/supabase/client.ts` proporciona una configuración mejorada del cliente Supabase:

```typescript
// Configuración del cliente Supabase con opciones avanzadas
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

// Funciones auxiliares para la gestión de autenticación
export const getClientAuthHeaders = () => {
  const email = localStorage.getItem('auth_email');
  const userId = localStorage.getItem('auth_user_id');
  
  const headers: Record<string, string> = {
    'Content-Type': 'application/json',
    'Accept-Profile': 'public',
    'apikey': SUPABASE_PUBLISHABLE_KEY
  };
  
  if (email) {
    headers['X-Auth-Email'] = email;
  }
  
  if (userId) {
    headers['X-Auth-User-Id'] = userId;
    headers['Authorization'] = `Bearer ${SUPABASE_PUBLISHABLE_KEY}`;
  }
  
  return headers;
};
```

### Manejo de Archivos

La función `useFileUpload` en `src/components/shared/upload/hooks/useFileUpload.ts` (no mostrada en el código proporcionado) gestiona la carga de archivos al almacenamiento de Supabase, ofreciendo:

- Validación de tipos de archivo
- Compresión de imágenes
- Manejo de errores
- Feedback de progreso

### Detección de Dispositivo Móvil

El hook `useIsMobile` en `src/hooks/use-mobile.ts` (no mostrado en el código proporcionado) permite adaptar la interfaz según el dispositivo:

```typescript
// Implementación conceptual del hook useIsMobile
export const useIsMobile = () => {
  const [isMobile, setIsMobile] = useState(false);
  
  useEffect(() => {
    const checkMobile = () => {
      setIsMobile(window.innerWidth < 768);
    };
    
    checkMobile();
    window.addEventListener('resize', checkMobile);
    return () => window.removeEventListener('resize', checkMobile);
  }, []);
  
  return isMobile;
};
```

## Estilos y UI

### Componentes de Shadcn UI

La aplicación utiliza componentes de shadcn/ui para mantener una interfaz coherente:

```tsx
// Ejemplo de componentes de UI utilizados
import { Button } from "@/components/ui/button";
import { Dialog, DialogContent, DialogHeader, DialogTitle } from "@/components/ui/dialog";
import { Form } from "@/components/ui/form";
```

Estos componentes facilitan:
1. **Consistencia visual**: Todos los elementos de la interfaz comparten el mismo estilo
2. **Accesibilidad**: Los componentes incluyen soporte para lectores de pantalla y navegación por teclado
3. **Responsividad**: Adaptación automática a diferentes tamaños de pantalla

### Personalización con Tailwind CSS

Los componentes se personalizan mediante Tailwind CSS:

```tsx
<Button 
  className="w-full bg-emerald-400 hover:bg-emerald-500 transition-all duration-300 hover:scale-[1.02] text-black"
  disabled={isSubmitting}
>
  <UserPlus className="mr-2 h-4 w-4" />
  {isSubmitting ? "Agregando..." : "Agregar Estudiante"}
</Button>
```

### Adaptación Móvil

La aplicación implementa diseños responsivos que se adaptan a diferentes dispositivos:

```tsx
// Ejemplo de uso de utilidades responsive de Tailwind
<div className="flex flex-col md:flex-row justify-between items-start md:items-center gap-4">
  {/* El contenido se organiza en columna en móviles y en fila en desktop */}
</div>

// Uso del hook useIsMobile para renderizado condicional
{isMobile ? (
  <Drawer open={isOpen} onClose={onClose}>
    {/* Versión móvil con drawer */}
  </Drawer>
) : (
  <Dialog open={isOpen} onOpenChange={onClose}>
    {/* Versión desktop con dialog */}
  </Dialog>
)}
```

## Rendimiento y Optimización

### División de Código

La aplicación implementa división de código mediante:

1. **Componentes modulares**: Cada funcionalidad se divide en componentes pequeños y enfocados
2. **Lazy loading**: Carga diferida de componentes según sea necesario
3. **Code splitting**: División del bundle por rutas

### Manejo de Estado Eficiente

La gestión de estado se optimiza mediante:

1. **Estado localizado**: El estado se mantiene lo más cercano posible a donde se utiliza
2. **Hooks personalizados**: Encapsulan lógica compleja y minimizan re-renders
3. **Memoización**: Uso de `useMemo` y `useCallback` para evitar cálculos innecesarios

## Buenas Prácticas Implementadas

### Separación de Responsabilidades

1. **Componentes de presentación**: Se enfocan exclusivamente en la UI y delegan la lógica a hooks
2. **Hooks personalizados**: Encapsulan la lógica de negocio y el estado
3. **Servicios**: Manejan la comunicación con APIs externas

### Manejo de Errores

La aplicación implementa un manejo de errores robusto:

```typescript
try {
  // Operación que podría fallar
  const { error } = await supabase.from("students").insert({/*...*/});
  
  if (error) throw error;
  
  // Notificación de éxito
  toast.success("Estudiante agregado correctamente");
} catch (error) {
  // Registro y notificación del error
  console.error("Error al agregar estudiante:", error);
  toast.error("Error al agregar el estudiante. Por favor, intente nuevamente.");
} finally {
  // Limpieza que siempre se ejecuta
  setIsSubmitting(false);
}
```

### Tipos TypeScript

El uso de TypeScript garantiza la seguridad de tipos en toda la aplicación:

```typescript
// Definición de tipos
interface AttendanceTableProps {
  students: StudentWithAttendance[];
  onStatusChange: (studentId: string, newStatus: AttendanceStatus) => void;
}

// Uso de tipos en componentes
const AttendanceTable = ({ students, onStatusChange }: AttendanceTableProps) => {
  // Implementación con tipos verificados
};
```

### Consistencia de Estilo

1. **Nombres descriptivos**: Variables y funciones con nombres que indican claramente su propósito
2. **Estructura consistente**: Organización similar para componentes, hooks y servicios
3. **Comentarios explicativos**: Documentación de código compleja o no obvia

---

Este manual técnico proporciona una visión detallada de la arquitectura, componentes y patrones utilizados en EduApp. Los desarrolladores pueden utilizarlo como referencia para entender el funcionamiento del sistema y realizar modificaciones o extensiones.
