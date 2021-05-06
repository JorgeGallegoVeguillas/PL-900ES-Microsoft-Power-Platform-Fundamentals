---
lab:
    title: 'Laboratorio 1: Modelado de datos'
    module: 'Módulo 2: Introducción a Microsoft Dataverse'
---

# Módulo 2: Introducción a Microsoft Dataverse
## Laboratorio: Modelado de datos

### Aviso importante (vigente a partir de noviembre de 2020):
Se ha cambiado el nombre de Common Data Service a Microsoft Dataverse. Parte de la terminología de Microsoft Dataverse se ha actualizado. Por ejemplo, ahora las entidades se llaman tablas. A partir de ahora, los campos y los registros de las bases de datos de Dataverse se denominarán columnas y filas.

Las aplicaciones están actualizando la experiencia del usuario, pero algunas referencias a la terminología de Microsoft Dataverse, como entidad (de ahora en delante **tabla**), campo (de ahora en adelante **columna**) y registro (de ahora en adelante **fila**) pueden no estar actualizadas. Tenga esto en cuenta cuando trabaje en los laboratorios.

Si desea obtener más información y consultar la lista completa de los términos afectados, visite [¿Qué es Microsoft Dataverse?](https://docs.microsoft.com/es-es/powerapps/maker/common-data-service/data-platform-intro#terminology-updates).

# Escenario

Bellows College es una institución educativa que tiene un campus con varios edificios. Actualmente se guarda un registro físico de las visitas al campus. La información no se recaba de manera coherente y no hay forma de recopilar y analizar los datos sobre las visitas de todo el campus. 

La administración del campus querría modernizar el sistema de registro de visitantes de los edificios cuyo acceso esté controlado por el personal de seguridad y en los que los anfitriones deban anotar con antelación las visitas y dejar constancia de ellas.

A lo largo de este curso, creará aplicaciones e implementará la automatización para permitir que el personal de administración y seguridad de Bellows College administre y controle el acceso a los edificios en el campus. 

En este laboratorio, accederá a su entorno, creará una base de datos de Microsoft Dataverse y diseñará una solución para realizar un seguimiento de sus cambios. También creará un modelo de datos que cumpla con los siguiente requisitos:

-   R1 – hacer un seguimiento de las ubicaciones (edificios) del campus en las que se producen las visitas
-   R2 – registrar información básica para identificar y hacer un seguimiento de los visitantes 
-   R3 – programar, registrar y administrar visitas 

Por último, importará los datos de ejemplo en Microsoft Dataverse.

# Pasos de alto nivel del laboratorio

Para preparar sus entornos de aprendizaje tendrá que hacer lo siguiente:

* Crear una solución y un editor
* Agregar los componentes nuevos y existentes que se necesitan para cumplir con los requisitos de la aplicación. Consulte la descripción de los metadatos (tablas y relaciones) en el [documento del modelo de datos](https://raw.githubusercontent.com/MicrosoftLearning/PL-900-Microsoft-Power-Platform-Fundamentals/update-march-2021/Allfiles/Campus%20Management.png). Puede mantener presionada la tecla CTRL y hacer clic o clicar con el botón derecho en el vínculo para abrir el documento del modelo de datos en una nueva ventana.

Su solución contendrá varias tablas al completar todas las personalizaciones:

-   Contacto
-   Edificio
-   Visita

## Requisitos previos:

* Haber finalizado el **Módulo 0, Laboratorio 0: Validación del entorno de laboratorio**

## Cuestiones que conviene tener en cuenta antes de comenzar:

* Convención de la nomenclatura

* Tipos de datos, restricciones (por ejemplo, la longitud máxima de un nombre)

* Formato de datetime para facilitar la localización

# Ejercicio 1: Cree la solución

## Tarea 1: Crear la solución y el editor

1.  Cree la solución

    -   Vaya a <https://make.powerapps.com>. Es posible que deba volver a autenticarse: haga clic en **Iniciar sesión** y siga las instrucciones en caso de que sea necesario.

    -   Haga clic en **Entorno**, en la esquina superior derecha de la pantalla, y elija su entorno en el menú desplegable.

    -   Seleccione **Soluciones** en el menú de la izquierda y haga clic en **Nueva solución**.

    -   Escriba **[Su apellido] Administración del campus** en **Nombre para mostrar**.

2.  Cree el editor

    -   Haga clic en la lista desplegable **Editor** y seleccione **+ Editor**

    -   En la ventana emergente, escriba **Bellows College** en **Nombre para mostrar** 
    
    -   Escriba **bc** en **Prefijo**

    -   Haga clic en **Guardar y cerrar**
    
    -   Haga clic en **Listo** en la ventana emergente.

3.  Complete la creación de la solución.

    -   Luego, haga clic en el menú desplegable **Editor** y seleccione el editor **Bellows College**
        que acaba de crear.

    -   Compruebe que la **Versión** está establecida como **1.0.0.0** 
    
    -   Haga clic en **Crear**.

# Ejercicio 2: Agregar tablas existentes y crear tablas nuevas

**Objetivo:** en este ejercicio, agregará la Tabla de contactos estándar y creará tablas personalizadas nuevas para Edificios y Visitas en la solución. 

## Tarea 1: Agregar una tabla existente

1.  Haga clic para abrir la solución **Administración del campus** que acaba de crear.

2.  Haga clic en **Agregar existente** y seleccione **Tabla**.

3.  Busque **Contacto** y selecciónela.

4.  Haga clic en **Siguiente**.

5.  Haga clic en **Seleccionar componentes** debajo de Contacto.

6.  Seleccione la pestaña **Vistas** y elija la vista **Contactos activos**. Haga clic en
    **Agregar**.
    
7.  Haga clic de nuevo en **Seleccionar componentes**.

8.  Seleccione la pestaña **Formularios** y elija el formulario **Contacto**.
    
9.  Haga clic en **Agregar**.

    > Debería tener **1 vista** y **1 formulario** seleccionados. 
    
10.  Vuelva a hacer clic en **Agregar**. Esto agregará la tabla de contactos con la vista y el formulario seleccionados a la solución que acaba de crear. 
    
> Su solución ahora debería tener la siguiente tabla: Contacto.

## Tarea 2: Crear la tabla Edificio

1.  Debe mantener su explorador abierto en su solución Administración del campus. De lo contrario, abra la solución Administración del campus y siga estos pasos:

    * Regístrese en <https://make.powerapps.com> (si aún no lo ha hecho).
    
    * Seleccione **Soluciones** y haga clic para abrir la solución **[su apellido] Administración del campus**
          que acaba de crear.
          
2.  Crear la tabla Edificio

    -   Haga clic en **Nuevo** y seleccione **Tabla**.
    
    -   Escriba **Edificio** en **Nombre para mostrar**. 
    
    -   Haga clic en **Crear**. Esto iniciará el aprovisionamiento de la tabla en segundo plano y podrá comenzar a agregar otras tablas y columnas.

## Tarea 3: Crear la tabla Visita con columnas

La tabla **Visita** contendrá información sobre las visitas al campus, incluidos el edificio, el visitante, la hora programada y la hora real de cada visita. 

Nos gustaría asignar a cada visita un número único que el visitante pueda escribir e interpretar fácilmente cuando se le pida durante el proceso de registro de la visita.

> Usamos el comportamiento **Independiente de la zona horaria** para registrar información de la fecha y hora, ya que el horario de una visita es siempre local según la ubicación del edificio y no debe cambiar cuando se consulta desde una zona horaria diferente. 

1.  Seleccione la solución **Administración del campus**.

2. Crear la tabla Visita

   * Haga clic en **Nuevo** y seleccione **Tabla**.
   
   * Escriba **Visita** en **Nombre para mostrar**. 
   
   * Haga clic en **Crear**. Esto iniciará el aprovisionamiento de la tabla en segundo plano y podrá comenzar a agregar otras columnas.

3. Crear la columna Inicio programado

   * Asegúrese de haber seleccionado la pestaña **Columnas** y haga clic en **Agregar columna**.
   
   * Especifique **Inicio programado** en **Nombre para mostrar**.
   
   * Seleccione **Fecha y hora** en **Tipo de datos**.
   
   * En **Obligatorio**, seleccione **Obligatorio**.
   
   * Expanda la sección **Opciones avanzadas**.
   
   * En **Comportamiento**, seleccione **Independiente de la zona horaria**.
   
   * Haga clic en **Listo**.

4.  Crear la columna Fin programado

    * Haga clic en **Agregar columna**.
    
    * Especifique **Fin programado** en **Nombre para mostrar**.
    
    * Seleccione **Fecha y hora** en **Tipo de datos**.
    
    * En **Obligatorio**, seleccione **Obligatorio**.
    
    * Expanda la sección **Opciones avanzadas**.
    
    * En **Comportamiento**, seleccione **Independiente de la zona horaria**.
    
    * Haga clic en **Listo**.
    
5.  Crear la columna Inicio real

    * Haga clic en **Agregar columna**.
    
    * Especifique **Inicio real** en **Nombre para mostrar**.
    
    * Seleccione **Fecha y hora** en **Tipo de datos**.
    
    * En el campo **Obligatorio**, déjelo como **Opcional**.
    
    * Expanda la sección **Opciones avanzadas**.
    
    * En **Comportamiento**, seleccione **Independiente de la zona horaria**.
    
    * Haga clic en **Listo**.
    
6.  Crear la columna Fin real

    * Haga clic en **Agregar columna**.
    
    * Especifique **Fin real** en **Nombre para mostrar**.
    
    * Seleccione **Fecha y hora** en **Tipo de datos**.
    
    * En el campo **Obligatorio**, déjelo como **Opcional**.
    
    * Expanda la sección **Opciones avanzadas**.
    
    * En **Comportamiento**, seleccione **Independiente de la zona horaria**.
    
    * Haga clic en **Listo**.
    
7.  Crear la columna Código

    * Haga clic en **Agregar columna**.
    
    * Especifique **Código** en **Nombre para mostrar**.
    
    * Seleccione **Autonumeración** en **Tipo de datos**.
    
    * Seleccione **Número prefijado de fecha** en **Tipo de autonumeración**.
    
    * Haga clic en **Listo**.
    
8.  Haga clic en **Guardar tabla**.

# Ejercicio 3: Crear Relaciones

**Objetivo:** en este ejercicio agregará relaciones entre las tablas.

## Tarea 1: Crear Relaciones

1.  Asegúrese de que todavía puede ver la tabla **Visita** de su solución de **Administración del campus**. De lo contrario, vaya allí.

2.  Crear una relación entre Visita y Contacto

    * Seleccione la pestaña **Relaciones**.
    
    * Haga clic en **Agregar relación** y seleccione **Varios a uno**.
    
    * Seleccione **Contacto** en **Relacionados (uno)**. 
    
    * Especifique **Visitante** en **Nombre para mostrar en la columna de búsqueda**. 
    
    * Haga clic en **Listo**.
    
3.  Crear una relación entre Visita y Edificio

    * Haga clic en **Agregar relación** y seleccione **Varios a uno**.
    
    * Seleccione **Edificio** en **Relacionados (uno)**. 
    
    * Haga clic en **Listo**.
    
4.  Haga clic en **Guardar tabla**.

5.  Seleccione **Soluciones** en el menú superior y haga clic en **Publicar todas las personalizaciones**.

# Ejercicio 4: Importar datos

**Objetivo:** en este ejercicio importará datos de ejemplo a la base de datos de Dataverse.

## Tarea 1: Importar una solución

En esta tarea, importará una solución que contenga el flujo de Power Automate necesario para completar la importación de datos.

1. Debería tener el archivo **DataImport_managed.zip** almacenado en su Escritorio. De lo contrario, descargue la [Solución de importación de datos](https://github.com/MicrosoftLearning/PL-900-Microsoft-Power-Platform-Fundamentals/blob/update-march-2021/Allfiles/DataImport_managed.zip?raw=true).

2. Inicie sesión en <https://make.powerapps.com>.

3. Seleccione su Entorno **de práctica [mis iniciales]** en la parte superior derecha, si aún no está seleccionado.

4. Seleccione **Soluciones** en el panel de navegación izquierdo.

5. Haga clic en **Importar** y luego en **Examinar**. Examine y seleccione **DataImport_managed.zip** desde su Escritorio y luego pulse **Siguiente**.

>   Es posible que reciba el siguiente mensaje:
>
>   Faltan dependencias. Instale las siguientes soluciones antes de instalar esta...
>
>   Este mensaje indica que el modelo de datos no está completo, el
>   prefijo del editor no es **bc** o los nombres de las tablas **Edificio** y **Visita**
>   difieren de los nombres indicados en los pasos anteriores.

6. Pulse **Siguiente**. Se le pedirá que restablezca las conexiones. 

7. Abra el desplegable **Seleccionar una conexión** y seleccione **+Nueva conexión**.

8. Se abrirá una nueva ventana o pestaña del explorador. Seleccione **Crear** cuando se le pida para crear la conexión. Conéctese en caso de que sea necesario para completar la creación de la conexión.

9. Cierre la pestaña actual para volver a la tabla anterior **Importación de una solución**.

10. Asegúrese de que la conexión que acaba de crear esté seleccionada. Si no ve la conexión, haga clic en **Actualizar** para actualizar la lista de conexiones. 

11. Pulse **Importar**.

12. Espere hasta que se complete la importación.

## Tarea 2: Importar datos  

1. Abra la solución **Importar datos**.

2. Compruebe el **Estado** del flujo **Datos de importación**.

3. Si el **Estado** está **Desactivado**, seleccione **...** junto a **Importación de datos** y, luego, seleccione **Activar**.

   > **Importante:** Si recibe un mensaje de error, compruebe que las tablas y los campos que creó coinciden con las instrucciones anteriores.

4. Abra el componente **Importación de datos**. Power Automate se abrirá en una nueva pestaña. 

5. Haga clic en **Comenzar** si se muestra en una ventana emergente. 

6. Haga clic en **Ejecutar** y luego en **Ejecutar flujo** cuando se le pida.

7. Haga clic en **Listo**.

8. Espere hasta que la instancia de flujo complete la ejecución. Puede actualizar la tabla **Historial de ejecución de 28 días** para ver cuándo se ha ejecutado el flujo. 

    > El propósito de este flujo era generar datos de ejemplo para los próximos laboratorios. En la siguiente tarea, comprobará que la importación de datos se ha realizado correctamente. 

## Tarea 3: Comprobar la importación de datos

1. Vuelva a la pestaña anterior de Power Apps. Haga clic en la ventana emergente **Listo**. 

2. Seleccione **Soluciones** en la barra de navegación izquierda y abra su solución de **Administración del campus**.

2. Haga clic para abrir la tabla **Visita** y luego seleccione la pestaña **Datos**.

3. Haga clic en **Visitas activas** en la esquina superior derecha para mostrar el selector de vistas y después seleccione **Todas las columnas**. Esto cambiará la vista que muestra los datos de la visita. 

    > Si no ve **Visitas activas** debido a que la resolución es más baja, debería poder ver un icono con forma de ojo en la misma ubicación.

    > Si la importación se realizó correctamente, debería poder ver una lista de las filas de visitas.

4. Haga clic en cualquier valor de la columna **Edificio** y confirme que el formulario Edificio se abre en otra ventana. 

5. Cierre la ventana que acaba de abrir.

6. Haga clic en cualquier valor de la columna **Visitante** (es posible que deba desplazar la vista hacia la derecha) y confirme que el formulario Contacto se abre en otra ventana.

7. Cierre la ventana que acaba de abrir.

# Retos

* ¿Consideraría usar la actividad *cita* como parte de la solución? ¿Qué cambiaría?
* ¿Cómo haría que el fin programado tenga lugar después del inicio programado? 
* ¿Cómo agregaría la compatibilidad para múltiples reuniones durante una sola visita?
* ¿Cómo garantizaría el acceso al edificio tanto para los contactos externos como para el personal interno?
* ¿Cómo haría que las visitas a determinados edificios requieran la aprobación de la dirección? ¿Qué cambiaría el proceso de aprobación en el modelo de datos?

