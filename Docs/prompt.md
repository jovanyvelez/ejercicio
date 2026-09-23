.# Preparación de un ejercicio educativo: edición de registros con FastAPI, Jinja2 y HTMX

## 1. Contexto y objetivo

Actúa como un desarrollador experto en FastAPI y como un docente especializado en la enseñanza de programación a estudiantes principiantes.

Debes preparar un proyecto educativo a partir de la estructura de archivos y el código que ya existen en el repositorio.

El objetivo pedagógico es que los estudiantes aprendan a **editar registros almacenados en una base de datos**, comprendiendo el proceso de cargar los datos actuales en un formulario, validar los cambios y guardar la actualización.

La aplicación debe ser sencilla, funcional y adecuada para estudiantes que están iniciándose en el desarrollo web con Python.

## 2. Inspección y adecuación del proyecto existente

Antes de realizar modificaciones:

1. Inspecciona la estructura actual de carpetas y archivos.
2. Revisa el código existente para identificar qué componentes pueden reutilizarse.
3. Conserva los archivos y las estructuras que sean útiles para el ejercicio.
4. Modifica o crea los archivos que sean necesarios.
5. Elimina únicamente los archivos que sean claramente innecesarios para el ejercicio y que no deban conservarse por compatibilidad o configuración del proyecto.

No reconstruyas todo desde cero si es posible aprovechar el trabajo existente.

Mantén una organización clara y sencilla. Evita introducir patrones, capas, abstracciones o dependencias que no sean necesarios para alcanzar el objetivo pedagógico.

## 3. Tecnologías y dependencias

Utiliza exclusivamente las siguientes tecnologías para implementar la funcionalidad principal:

* FastAPI, instalando el paquete `fastapi[standard]`.
* Jinja2 para la generación de las plantillas HTML.
* HTMX, utilizando su enfoque más sencillo posible.
* asyncpg para la conexión y las operaciones asíncronas con PostgreSQL.

No se requiere Loguru.

Evita incorporar bibliotecas adicionales, sistemas de autenticación, herramientas de frontend o funcionalidades ajenas al ejercicio, salvo que sean indispensables para que el proyecto funcione.

Para las consultas SQL, utiliza consultas parametrizadas y evita construirlas mediante concatenación de valores recibidos desde los formularios.

## 4. Base de datos

La aplicación trabajará con una base de datos PostgreSQL.

La variable de entorno de conexión es:

`DATABASE_URL="postgresql://neondb_owner:npg_qgvYbXeI78EM@ep-patient-math-apihp7g4-pooler.c-7.us-east-1.aws.neon.tech/neondb?sslmode=require&channel_binding=require"`

La tabla existente se denomina `productos` y contiene los siguientes campos:

| Campo         | Descripción              |
| ------------- | ------------------------ |
| `nombre`      | Nombre del producto      |
| `precio`      | Precio del producto      |
| `cantidad`    | Cantidad disponible      |
| `descripcion` | Descripción del producto |

Considera que la tabla ya existe.

No inventes credenciales ni incluyas datos de conexión reales en el código.

Si necesitas conocer los tipos de datos o la clave primaria de la tabla, inspecciona el proyecto existente. Si esa información no está disponible, identifica claramente las suposiciones necesarias y solicita los datos faltantes antes de implementar una solución que dependa de ellos.

## 5. Funcionalidad que deben desarrollar los estudiantes

El ejercicio debe centrarse exclusivamente en la edición de productos existentes.

### Requisitos funcionales

1. Mostrar una lista de productos almacenados en la base de datos.
2. Permitir seleccionar un producto para editarlo.
3. Cargar los valores actuales del producto seleccionado en un formulario HTML.
4. Permitir modificar los campos correspondientes.
5. Validar los valores recibidos antes de ejecutar la actualización.
6. Si existen errores de validación, mostrar mensajes comprensibles y conservar los valores ingresados para que el estudiante pueda corregirlos.
7. Si los datos son válidos, ejecutar una consulta SQL `UPDATE` sobre el registro seleccionado.
8. Informar al usuario si la actualización fue exitosa.
9. Reflejar los nuevos valores en la interfaz.

La edición debe identificar inequívocamente el registro que se va a modificar, utilizando la clave primaria real de la tabla.

No es necesario implementar funcionalidades de creación o eliminación de productos.

## 6. Uso de HTMX

Utiliza HTMX de la manera más sencilla posible, sin introducir complejidad innecesaria.

La interacción debe permitir que el estudiante comprenda cómo enviar un formulario al servidor y actualizar una parte de la página utilizando la respuesta HTML de FastAPI y Jinja2.

Evita introducir JavaScript personalizado si HTMX y las respuestas HTML de FastAPI permiten resolver la interacción.

## 7. Alcance pedagógico

El código debe ser fácil de leer, explicar y modificar en clase.

Prioriza:

* Rutas de FastAPI claramente identificables.
* Formularios HTML sencillos.
* Plantillas Jinja2 fáciles de comprender.
* Consultas SQL explícitas.
* Validaciones comprensibles.
* Una separación de responsabilidades que no exceda lo necesario para este ejercicio.

No introduzcas contenidos avanzados que no sean indispensables para la edición de registros.

## 8. Material para los estudiantes

Crea una carpeta `Docs/` y dentro de ella un archivo Markdown llamado `ejercicio_edicion_productos.md`.

El documento debe contener el enunciado del ejercicio dirigido directamente a los estudiantes.

Incluye:

1. Título y contexto.
2. Objetivo de aprendizaje.
3. Descripción del problema.
4. Tecnologías y dependencias que deben instalar.
5. Información de la base de datos y de la tabla.
6. Requisitos funcionales.
7. Instrucciones de trabajo paso a paso, sin revelar la solución completa.
8. Criterios de aceptación que permitan comprobar cuándo el ejercicio está terminado.
9. Indicaciones para ejecutar y probar la aplicación, de acuerdo con la estructura y configuración real del proyecto.

El documento debe estar redactado en español, con lenguaje claro, tono pedagógico y adecuado para estudiantes principiantes.

No incluyas la solución del profesor en este documento.

## 9. Solución completa para el profesor

Crea una carpeta denominada `solucion/` que contenga una implementación completa y funcional del ejercicio.

Debe incluir todos los archivos necesarios para ejecutar la solución de manera independiente, respetando las convenciones útiles del proyecto existente.

La solución debe contemplar:

* Conexión asíncrona a PostgreSQL mediante asyncpg.
* Consulta de productos.
* Carga de los datos actuales en el formulario de edición.
* Validación de los datos enviados.
* Ejecución segura de la consulta `UPDATE`.
* Manejo comprensible de errores.
* Respuestas HTML y actualización de la interfaz mediante HTMX.
* Plantillas Jinja2 necesarias.
* Instrucciones de instalación y ejecución.

Incluye comentarios pedagógicos breves en las partes del código que sean especialmente importantes para explicar el proceso de edición.

La carpeta `solucion/` debe contener la respuesta completa del ejercicio, no solamente fragmentos de código o una explicación teórica.

## 10. Verificación final

Antes de dar por terminado el trabajo:

1. Comprueba que la estructura de carpetas sea coherente.
2. Revisa que las rutas, formularios, nombres de campos y consultas SQL sean consistentes entre sí.
3. Comprueba que el formulario cargue los datos del producto seleccionado.
4. Verifica que los datos inválidos no produzcan una actualización.
5. Verifica que los datos válidos produzcan una actualización del registro correcto.
6. Comprueba que la interfaz refleje los cambios.
7. Revisa que las instrucciones de instalación correspondan a las dependencias realmente utilizadas.
8. Asegúrate de que el documento para estudiantes no revele la solución completa.

Si no puedes conectarte a la base de datos real, no afirmes que las operaciones SQL fueron probadas contra ella. Indica qué verificaciones pudiste realizar y cuáles requieren la conexión del docente.

## 11. Entregables

Al finalizar, presenta:

* La estructura final de carpetas y archivos.
* El código necesario para el ejercicio.
* El archivo `Docs/ejercicio_edicion_productos.md`.
* La solución completa dentro de `solucion/`.
* Un resumen breve de los archivos creados, modificados o eliminados.
* Las instrucciones para ejecutar el ejercicio y la solución.

**Restricción principal:** no amplíes el alcance del ejercicio. Todo el trabajo debe estar orientado a que los estudiantes comprendan y practiquen la edición de registros existentes mediante FastAPI, Jinja2, HTMX y PostgreSQL con asyncpg.
