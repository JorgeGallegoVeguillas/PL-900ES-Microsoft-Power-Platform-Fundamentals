---
lab:
    title: 'Laboratorio: Modelado de datos'
    module: 'Módulo 2: Introducción a Common Data Service'
---

# Módulo 2: Introducción a Common Data Service
## Laboratorio: Modelado de datos


# Escenario
    
Bellows College es una institución educativa que tiene un campus con varios edificios. Actualmente se guarda un registro físico de las visitas al campus. La información no se recaba de manera coherente y los datos sobre las visitas de todo el campus no se puede recopilar ni analizar. 

La administración del campus querría modernizar el sistema de registro de visitantes de los edificios cuyo acceso esté controlado por el personal de seguridad y en los que los anfitriones deban anotar con antelación las visitas y dejar constancia de ellas.

A lo largo de este curso, creará aplicaciones y realizará la automatización para permitir que el personal de administración y seguridad de Bellows College administre y controle el acceso a los edificios en el campus. 

En este laboratorio, deberá acceder a su entorno, crear una base de datos de Common Data Service (CDS) y crear una solución para realizar un seguimiento de sus cambios. También creará un modelo de datos que cumpla con los siguiente requisitos:

-   R1: Hacer un seguimiento de las ubicaciones (edificios) del campus en las que se producen las visitas
-   R2: Registrar información básica para identificar y hacer un seguimiento de los visitantes 
-   R3 – Programar, registrar y administrar visitas 

Finalmente, importará los datos de muestra a Common Data Service.

# Pasos de alto nivel del laboratorio

Para preparar sus entornos de aprendizaje tendrá que:

* crear una solución y un publicador
* añadir los componentes nuevos y existentes que se necesitan para cumplir con los requisitos de la aplicación. Consulte la descripción de los metadatos (entidades y relaciones) en el [documento del modelo de datos](https://github.com/MicrosoftLearning/PL-900-Microsoft-Power-Platform-Fundamentals/raw/master/Allfiles/Labs/Campus%20Management.png). Puede mantener presionada la tecla CTRL y hacer clic o hacer clic con el botón derecho en el vínculo para abrir el documento del modelo de datos en una nueva ventana.

Su solución contendrá varias entidades al completar todas las personalizaciones:

-   Contacto
-   Edificio
-   Visita

## Requisitos previos:

* Finalización del **Módulo 0 Laboratorio 0: Validación del entorno de laboratorio**

## Cuestiones que tener en cuenta antes de comenzar:

* Convención de nomenclatura
* Tipos de datos, restricciones (por ejemplo, la longitud máxima de un nombre)
* Formato de datetime para facilitar la localización

# Ejercicio n.° 1: Creación de la solución

**Objetivo:** En este ejercicio, preparará el entorno y creará una solución que sea compatible con el proceso de modelado de datos. 

## Tarea 1: Creación de la solución y el publicador

1.  Creación de la solución

    -   Inicie sesión en <https://make.powerapps.com>. Es posible que deba volver a autenticarse; si es necesario, haga clic en **Iniciar sesión** y siga las instrucciones.

    -   Seleccione su entorno. Para ello, haga clic en **Entorno** en la esquina superior derecha de la pantalla y elija su entorno en el menú desplegable.

    -   Seleccione **Soluciones** en el menú de la izquierda y haga clic en **Nueva solución**.

    -   Escriba [sus apellidos] **Administración del campus** en **Nombre para mostrar**.

2.  Cree un publicador

    -   Haga clic en el menú desplegable **Publicador** y seleccione **Publicador**.

    -   En la ventana emergente, escriba **Bellows College** en **Nombre para mostrar** y **bc** en **Prefijo**.

    -   Haga clic en **Guardar y cerrar**. 
    
    -   Haga clic en **Listo** en la ventana emergente.

3.  Complete la creación de la solución.

    -   Luego, haga clic en el menú desplegable **Publicador** y seleccione el publicador **Bellows College**
        que acaba de crear.

    -   Valide que **Versión** esté establecido en **1.0.0.0** 
    
    -   Haga clic en **Crear**.

## Tarea 2: Agregar una entidad existente

1.  Haga clic para abrir la solución **Administración del campus** que acaba de crear.
2.  Haga clic en **Agregar existente** y seleccione **Entidad**.
3.  Busque **Contacto** y selecciónelo.
4.  Haga clic en **Siguiente**.
5.  Haga clic en **Seleccionar componentes**.
6.  Seleccione la pestaña **Vistas** y elija la vista **Contactos activos**. Haga clic en
    **Añadir**:
7.  Haga clic nuevamente en **Seleccionar componentes**.
8.  Seleccione la pestaña **Formulario** y elija el formulario **Contacto**.
9.  Haga clic en **Agregar**.
10. Debería tener **1 vista** y **1 formulario** seleccionados. Haga clic en **Agregar**.
    Al hacerlo, la entidad Contacto se agregará con la vista y el formulario seleccionados a la solución recién creada. 
11.  Su solución ahora debería tener una entidad: Contacto.

# Ejercicio n.° 2: Crear entidades y relaciones

**Objetivo:** En este ejercicio creará entidades y agregará relaciones
entre ellas.

## Tarea n.° 1: Crear entidad de creación y campos

1.  El explorador debería seguir abierto con la solución Administración del campus. De lo contrario, ábrala siguiendo estos pasos:
    * Regístrese en <https://make.powerapps.com> (si aún no lo ha hecho)
    * Seleccione **Soluciones** y haga clic para abrir la solución **Administración del campus**
          que acaba de crear.
2.  Crear una entidad de edificio

    -   Haga clic en **Nuevo** y seleccione **Entidad**.
    -   Escriba **Edificio** en **Nombre para mostrar**. 
    -   Haga clic en **Listo**. Esto hará que la entidad
            comience a aprovisionarse en segundo plano y usted podrá comenzar a añadir
            otras entidades y campos.

## Tarea n.°2: Crear Campos y Entidad de visita

La entidad **Visita** contendrá información sobre las visitas al campus, como el edificio, el visitante, la hora programada y la hora real de cada visita. 

Nos gustaría asignar a cada visita un número único que el visitante pueda ingresar e interpretar fácilmente cuando se le solicite durante el proceso de registro de la visita.

> [NOTA]
> Utilizamos el comportamiento de **Zona horaria independiente** para registrar información de la fecha y hora, ya que el horario de una visita es *siempre* local para la ubicación del edificio y no debe cambiar cuando se ve desde una zona horaria diferente. 

1.  Seleccione la solución **Administración del campus**.
2. Crear Entidad de visita

   * Haga clic en **Nuevo** y seleccione **Entidad**.
   * Escriba **Visita** para **Nombre para mostrar**. 
   * Haga clic en **Listo**. Esto iniciará el aprovisionamiento de la entidad en segundo plano y podrá comenzar a agregar otros campos.

3. Crear el campo Inicio programado

   * Asegúrese de tener la pestaña **Campos** seleccionada y haga clic en **Agregar campo**.
   * Escriba **Inicio programado** para **Nombre para mostrar**.
   * Seleccione **Fecha y hora** para **Tipo de datos**.
   * En el campo **Obligatorio**, seleccione **Obligatorio**.
   * Expanda la sección **Opciones avanzadas**.
   * En el campo **Comportamiento**, seleccione **Independiente de la zona horaria**.
   * Haga clic en **Listo**.

4.  Crear el campo Fin programado

    * Haga clic en **Agregar campo**.
    * Introduzca **Fin programado** en **Nombre para mostrar**.
    * Seleccione **Fecha y hora** para **Tipo de datos**.
    * En el campo **Obligatorio**, seleccione **Obligatorio**.
    * Expanda la sección **Opciones avanzadas**.
    * En el campo **Comportamiento**, seleccione **Independiente de la zona horaria**.
    * Haga clic en **Listo**.
    
6.  Crear campo de Inicio real

    * Haga clic en **Agregar campo**.
    * Introduzca **Inicio real** para el **Nombre para mostrar**.
    * Seleccione **Fecha y hora** para **Tipo de datos**.
    * Expanda la sección **Opciones avanzadas**.
    * En el campo **Comportamiento**, seleccione **Independiente de la zona horaria**.
    * Haga clic en **Listo**.
    
7.  Crear campo de Fin real

    * Haga clic en **Agregar campo**.
    * Introduzca **Fin real** para **Nombre para mostrar**.
    * Seleccione **Fecha y hora** para **Tipo de datos**.
    * Expanda la sección **Opciones avanzadas**.
    * En el campo **Comportamiento**, seleccione **Independiente de la zona horaria**.
    * Haga clic en **Listo**.
    
7.  Crear campo de Código

    * Haga clic en **Agregar campo**.
    * Introduzca **Código** para **Nombre para mostrar**.
    * Seleccione **Autonumeración** para **Tipo de datos**.
    * Seleccione **Número prefijado de fecha** para **Tipo de autonumeración**.
    * Haga clic en **Listo**.
    
8.  Haga clic en **Guardar entidad**

## Tarea n.° 3: Crear relaciones

1.  Asegúrese de que todavía se muestra la entidad **Visita** de la solución **Administración del campus**. De lo contrario, diríjase hasta ella.
2.  Crear una relación de visita a contacto
    * Seleccione la pestaña **Relaciones**.
    * Haga clic en **Añadir relación** y seleccione **Varios a uno**.
    * Seleccione **Contacto** para **Relacionados (uno)**. 
    * Introduzca **Visitante** para **Nombre para mostrar del campo de búsqueda** 
    * Haga clic en **Listo**.
3.  Crear relación de visita a edificio
    * Haga clic en **Añadir relación** y seleccione **Varios a uno**.
    * Seleccione **Edificio** para **Relacionados (uno)**. 
    * Haga clic en **Listo**.
4.  Haga clic en **Guardar entidad**.
5.  Seleccione **Soluciones** en el menú superior y haga clic en **Publicar todas las personalizaciones**.

# Ejercicio 3: Importar datos

**Objetivo:** En este ejercicio importará datos de muestra a la base de datos de Common Data Service.

## Tarea n.° 1: Importar asignación de datos

1. Descargue [CampusDataMap.xml](../../Allfiles/Labs/CampusDataMap.xml) si aún no lo ha hecho.
2. Vaya al Centro de administración de Power Platform en <https://admin.powerplatform.microsoft.com> e inicie sesión.
3. Seleccione su entorno de Bellows College.
4. Haga clic en **Configuración** en la parte superior.
5. Expanda la sección **Administración de datos**, luego seleccione **Asignaciones de datos**. Esto abrirá la pantalla de importar asignación en una nueva pestaña del explorador.
6. Haga clic en **Importar**, luego haga clic en **Elegir archivo**. Localice y seleccione **CampusDataMap.xml** descargado anteriormente y luego presione **Aceptar**. 
7. El archivo de asignación de datos del campus debe importarse correctamente. Si se produce un error, vuelva y valide que se hayan creado todas las entidades y campos requeridos en las tareas anteriores.
8. Seleccione **Soluciones** en el menú superior y haga clic en **Publicar todas las personalizaciones**.

## Tarea 2: Importar datos  

1. Descargue [CampusData.zip](../../Allfiles/Labs/CampusData.zip).
2. Diríjase al Centro de administración de Power Platform en <https://admin.powerplatform.microsoft.com>.
3. Seleccione su entorno de Bellows College.
4. Haga clic en **Configuración** en la parte superior.
5. Expanda la sección **Administración de datos** y, luego, seleccione **Asistente para la importación de datos**.
6. Presione **IMPORTAR DATOS**.
7. Haga clic en **Elegir archivo**, luego localice y seleccione el archivo **CampusData.zip** descargado anteriormente.
8. Presione **Siguiente**, luego vuelva a presionar **Siguiente**.
9. Seleccione **CampusImportDataMap**, presione **Siguiente**.
10. Revise el resumen de la asignación, luego presione **Siguiente**y después presione **Enviar**.
11. Presione **Finalizar**.
12. Se iniciará la importación de datos. Ahora puede usar el botón Actualizar que se encuentra en el lado derecho de la pantalla **Mis importaciones** para actualizar la tabla hasta que las cuatro importaciones presenten una razón para el estado de **Completado**. Este proceso puede durar unos minutos.

## Tarea 3: Verificar la importación de datos

1. Seleccione la solución **Administración del campus**. Si aún no la ha abierto, vaya a make.powerapps.com y haga clic en Soluciones en el panel izquierdo para buscar la solución.*
2. Seleccione la entidad **Visita** y, luego, seleccione la pestaña **Datos**.
3. Haga clic **Visitas activas** en la esquina superior derecha para mostrar el selector de vistas y, luego, seleccione **Todos los campos**.
4. Si la importación se realizó correctamente, debería ver una lista de las entradas de visitas.
5. Haga clic en cualquier valor de la columna **Edificio** y confirme que el formulario Edificio se abre en una ventana separada.
6. Haga clic en cualquier valor de la columna **Visitante** (es posible que deba desplazar la vista hacia la derecha) y confirme que el formulario Contacto se abre en una ventana separada.

# Desafíos

* ¿Se plantearía usar una actividad de citas como parte de la solución? ¿Qué cambiaría?
* ¿Cómo hacer cumplir el final programado después del inicio programado? 
* Agregue soporte técnico para múltiples reuniones durante una sola visita.
* Asegure el acceso al edificio no solo para los contactos externos, sino también para el personal interno.
* Las visitas a ciertos edificios requieren la aprobación de la gerencia. ¿Qué cambiaría el proceso de aprobación en el modelo de datos?

