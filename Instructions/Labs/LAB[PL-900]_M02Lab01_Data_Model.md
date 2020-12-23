---
lab:
    title: 'Laboratorio 1: Modelado de datos'
    module: 'Módulo 2: Introducción a Common Data Service'
---

# Módulo 2: Introducción a Common Data Service
## Laboratorio: Modelado de datos


# Escenario

Bellows College es una institución educativa que tiene un campus con varios edificios. Actualmente se guarda un registro físico de las visitas al campus. La información no se recaba de manera uniforme y no hay forma de recopilar y analizar los datos sobre las visitas de todo el campus. 

La administración del campus querría modernizar el sistema de registro de visitantes de los edificios cuyo acceso esté controlado por el personal de seguridad y en los que los anfitriones deban anotar con antelación las visitas y dejar constancia de ellas.

A lo largo de este curso, creará aplicaciones y realizará la automatización para permitir que el personal de administración y seguridad de Bellows College administre y controle el acceso a los edificios en el campus. 

En este laboratorio, accederá a su entorno, creará una base de datos de Common Data Service (CDS) y diseñará una solución para realizar un seguimiento de sus cambios. También creará un modelo de datos que cumpla con los siguiente requisitos:

-   R1: Hacer un seguimiento de las ubicaciones (edificios) del campus en las que se producen las visitas
-   R2: Registrar información básica para identificar y hacer un seguimiento de los visitantes 
-   R3 – Programar, registrar y administrar visitas 

Por último, importará los datos de ejemplo en Common Data service.

# Pasos de alto nivel del laboratorio

Para preparar sus entornos de aprendizaje tendrá que:

* crear una solución y un publicador
* añadir los componentes nuevos y existentes que se necesitan para cumplir con los requisitos de la aplicación. Consulte la descripción de los metadatos (entidades y relaciones) en el [documento del modelo de datos](../../Allfiles/Campus%20Management.png). Puede mantener presionada la tecla CTRL y hacer clic o hacer clic con el botón derecho en el vínculo para abrir el documento del modelo de datos en una nueva ventana.

Su solución contendrá varias entidades al completar todas las personalizaciones:

-   Contacto
-   Edificio
-   Visita

## Requisitos previos:

* Finalización del **Módulo 0 Laboratorio 0: Validación del entorno de laboratorio**

## Cuestiones a tener en cuenta antes de comenzar:

* Convención de nomenclatura

* Tipos de datos, restricciones (por ejemplo, la longitud máxima de un nombre)

* Formato de datetime para facilitar la localización

# Ejercicio 1: Creación de la solución

## Tarea 1: Creación de la solución y el publicador

1.  Creación de la solución

    -   Vaya a<https://make.powerapps.com>. Es posible que deba volver a autenticarse: haga clic en **Iniciar sesión** y siga las instrucciones si es necesario.

    -   Seleccione su entorno haciendo clic en **Entorno**, en la esquina superior derecha de la pantalla, y elija su entorno en el menú desplegable.

    -   Seleccione **Soluciones** en el menú de la izquierda y haga clic en **Nueva solución**.

    -   Escriba **[Su apellido] Administración del campus** en **Nombre para mostrar**.

2.  Cree un publicador

    -   Haga clic en el menú desplegable **Publicador** y seleccione **Publicador**.

    -   En la ventana emergente, escriba **Bellows College** en **Nombre para mostrar**. 
    
    -   Escriba **bc** en **Prefijo**.

    -   Haga clic en **Guardar y cerrar**.
    
    -   Haga clic en **Listo** en la ventana emergente.

3.  Complete la creación de la solución.

    -   Luego, haga clic en el menú desplegable **Publicador** y seleccione el publicador **Bellows College**
        que acaba de crear.

    -   Compruebe que la **Versión** está establecida en **1.0.0.0** 
    
    -   Haga clic en **Crear**.

## Tarea 2: Agregar una entidad existente

1.  Haga clic para abrir la solución **Administración del campus** que acaba de crear.

2.  Haga clic en **Agregar existente** y seleccione **Entidad**.

3.  Localice **Contacto** y selecciónelo.

4.  Haga clic en **Siguiente**.

5.  Haga clic en **Seleccionar componentes** debajo de Contacto.

6.  Seleccione la pestaña **Vistas** y elija la vista **Contactos activos**. Haga clic en
    **Añadir**:
    
7.  Haga clic nuevamente en **Seleccionar componentes**.

8.  Seleccione la pestaña **Formulario** y elija el formulario **Contacto**.
    
9.  Haga clic en **Agregar**.

    > Debería tener **1 vista** y **1 formulario** seleccionados. 
    
10.  Vuelva a hacer clic en **Añadir**. Esto agregará la entidad de contacto con la vista y el formulario seleccionados a la solución recientemente creada. 
    
11.  Su solución ahora debería tener una entidad: Contacto.

# Ejercicio 2: Crear entidades y relaciones

**Objetivo:** En este ejercicio creará entidades y agregará relaciones
entre ellas.

## Tarea 1: Crear entidad de creación y campos

1.  Debe mantener su explorador abierto en su solución de Administración del campus. De lo contrario, abra la solución Administración del campus siguiendo estos pasos:

    * Regístrese en <https://make.powerapps.com> (si aún no lo ha hecho)
    
    * Seleccione **Soluciones** y haga clic para abrir la solución **[su apellido] Administración del campus**
          que acaba de crear.
          
2.  Crear una entidad de edificio

    -   Haga clic en **Nuevo** y seleccione **Entidad**.
    
    -   Escriba **Edificio** en **Nombre para mostrar**. 
    
    -   Haga clic en **Listo**. Esto iniciará el aprovisionamiento de la entidad en segundo plano y podrá comenzar a agregar otras entidades y campos.

## Tarea 2: Crear Campos y Entidad de visita

La entidad **Visita** contendrá información sobre las visitas al campus, incluyendo el edificio, el visitante, la hora programada y la hora real de cada visita. 

Nos gustaría asignar a cada visita un número único que el visitante pueda ingresar e interpretar fácilmente cuando se le solicite durante el proceso de registro de la visita.

> Usamos el comportamiento de **Independiente de la zona horaria** para registrar información de la fecha y hora, ya que el horario de una visita es siempre local para la ubicación del edificio y no debe cambiar cuando se consulta desde una zona horaria diferente. 

1.  Seleccione la solución **Administración del campus**.

2. Crear Entidad de visita

   * Haga clic en **Nuevo** y seleccione **Entidad**.
   
   * Escriba **Visita** en **Nombre para mostrar**. 
   
   * Haga clic en **Listo**. Esto iniciará el aprovisionamiento de la entidad en segundo plano y podrá comenzar a agregar otros campos.

3. Crear el campo Inicio programado

   * Asegúrese de tener la pestaña **Campos** seleccionada y haga clic en **Agregar campo**.
   
   * Escriba **Inicio programado** para **Nombre para mostrar**.
   
   * Seleccione **Fecha y hora** para **Tipo de datos**.
   
   * En el campo **Necesario**, seleccione **Necesario**.
   
   * Expanda la sección **Opciones avanzadas**.
   
   * En el campo **Comportamiento**, seleccione **Independiente de la zona horaria**.
   
   * Haga clic en **Listo**.

4.  Crear el campo Fin programado

    * Haga clic en **Agregar campo**.
    
    * Introduzca **Fin programado** en **Nombre para mostrar**.
    
    * Seleccione **Fecha y hora** para **Tipo de datos**.
    
    * En el campo **Necesario**, seleccione **Necesario**.
    
    * Expanda la sección **Opciones avanzadas**.
    
    * En el campo **Comportamiento**, seleccione **Independiente de la zona horaria**.
    
    * Haga clic en **Listo**.
    
5.  Crear campo de Inicio real

    * Haga clic en **Agregar campo**.
    
    * Introduzca **Inicio real** para el **Nombre para mostrar**.
    
    * Seleccione **Fecha y hora** para **Tipo de datos**.
    
    * En el campo **Necesario**, déjelo como **Opcional**.
    
    * Expanda la sección **Opciones avanzadas**.
    
    * En el campo **Comportamiento**, seleccione **Independiente de la zona horaria**.
    
    * Haga clic en **Listo**.
    
6.  Crear campo de Fin real

    * Haga clic en **Agregar campo**.
    
    * Introduzca **Fin real** para **Nombre para mostrar**.
    
    * Seleccione **Fecha y hora** para **Tipo de datos**.
    
    * En el campo **Necesario**, déjelo como **Opcional**.
    
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

## Tarea 3: Crear relaciones

1.  Asegúrese de que todavía está viendo la entidad **Visita** de su solución de **Administración del campus**. De lo contrario, vaya hacia allí.

2.  Crear una relación de visita a contacto

    * Seleccione la pestaña **Relaciones**.
    
    * Haga clic en **Añadir relación** y seleccione **Varios a uno**.
    
    * Seleccione **Contacto** para **Relacionados (uno)**. 
    
    * Introduzca **Visitante** para **Nombre para mostrar del campo de búsqueda** 
    
    * Haga clic en **Listo**.
    
3.  Crear relación de visita a edificio

    * Haga clic en **Añadir relación** y seleccione **Varios a uno**.
    
    * Seleccione **Edificio** en **Relacionados (uno)**. 
    
    * Haga clic en **Listo**.
    
4.  Haga clic en **Guardar entidad**.

5.  Seleccione **Soluciones** en el menú superior y haga clic en **Publicar todas las personalizaciones**.

# Ejercicio 3: Importar datos

**Objetivo:** En este ejercicio importará datos de muestra a la base de datos de Common Data Service.

## Tarea 1: Importar solución

En esta tarea, importará una solución que contiene el flujo de Power Automate necesario para completar la importación de datos.

1. Debería tener el archivo **DataImport_managed.zip** almacenado en su escritorio. Si no, descargue la [Solución de importación de datos](../../Allfiles/DataImport_managed.zip).

2. Conéctese a <https://make.powerapps.com>.

3. Seleccione su entorno ***mis iniciales* Práctica** en la parte superior derecha, si aún no está seleccionado.

4. Seleccione **Soluciones** en el panel de navegación izquierdo.

5. Haga clic en **Importar** y luego en **Examinar**. Examine y seleccione **DataImport_managed.zip** desde su escritorio y luego presione **Siguiente**.

>   Puede recibir el siguiente mensaje:
>
>   Faltan dependencias. Instale las siguientes soluciones antes de instalar esta...
>
>   Ese mensaje indica que el modelo de datos no está completo, el
>   prefijo del editor no es **bc** o los nombres de las entidades **Edificio** y **Visita**
>   difieren de los nombres enumerados en los pasos anteriores.

6. Presione **Siguiente**. Se le pedirá que restablezca las conexiones. 

7. Expanda el desplegable **Seleccionar una conexión** y seleccione **Nueva conexión**.

8. Se abre una nueva ventana o pestaña del explorador. Seleccione **Crear** cuando se le solicite que cree una conexión de Common Data Service. Conéctese si es necesario para completar la creación de la conexión.

9. Vuelva a la pestaña anterior donde estaba importando la solución.

10. Haga clic en **Actualizar** para actualizar la lista de conexiones. 

11. Asegúrese de que la conexión que acaba de crear esté seleccionada.

12. Presione **Importar**.

13. Espere hasta que se complete la importación.

## Tarea 2: Importar datos  

1. Abra la solución **Importar datos**.

2. Compruebe el **Estado** del flujo **Datos de importación**.

3. Si el **Estado** está **Desactivado**, seleccione [...] junto a **Importación de datos** y, luego, seleccione **Activar**.

   > **Importante:** Si recibe un mensaje de error, compruebe que las entidades y los campos que creó coincidan con las instrucciones anteriores.

4. Abra el componente **Importación de datos**. Power Automate se abrirá en una nueva pestaña. 

5. Haga clic en **Comenzar** si se muestra en una ventana emergente. 

6. Haga clic en **Ejecutar** luego en **Ejecutar flujo** cuando se le solicite.

7. Haga clic en **Listo**.

8. Espere hasta que la instancia de flujo complete la ejecución. Puede actualizar la tabla **Historial de ejecución de 28 días** para ver cuándo se ha ejecutado el flujo. 

    > El propósito de este flujo era generar datos de ejemplo para los próximos laboratorios. En la siguiente tarea, comprobará que la importación de datos se haya realizado correctamente. 

## Tarea 3: Verificar la importación de datos

1. Vuelva a la pestaña anterior de Power Apps. Haga clic en la ventana emergente **Listo**. Seleccione **Soluciones** en la barra de navegación izquierda y abra su solución **Administración del campus**.

2. Haga clic para abrir la entidad **Visita**, luego seleccione la pestaña **Datos**.

3. Haga clic en **Visitas activas** en la esquina superior derecha para mostrar el selector de vista, luego seleccione **Todos los campos**. Esto cambiará la vista que se está utilizando para mostrar los datos de la visita. 

    > Si no ve **Visitas activas** debido a que la resolución es más pequeña, debería ver un icono con forma de ojo en la misma ubicación.

    > Si la importación se realizó correctamente, debería ver una lista de las entradas de visitas.

4. Haga clic en cualquier valor en la columna **Edificio** y confirme que el formulario del edificio se abra en otra ventana. 

5. Cierre la ventana abierta recientemente.

6. Haga clic en cualquier valor en la columna **Visitante** (es posible que deba desplazar la vista hacia la derecha), confirme que el formulario de contacto se abra en una ventana separada.

7. Cierre la ventana abierta recientemente.

# Desafíos

* ¿Consideraría usar la actividad de *cita* como parte de la solución? ¿Qué cambiaría?
* ¿Cómo hacer que el final programado tenga lugar después del inicio programado? 
* ¿Cómo agregar la compatibilidad para múltiples reuniones durante una sola visita?
* ¿Cómo asegurar el acceso al edificio no solo para los contactos externos, sino también para el personal interno?
* ¿Cómo hacer que las visitas a determinados edificios requieran la aprobación de la dirección? ¿Qué cambiaría el proceso de aprobación en el modelo de datos?

