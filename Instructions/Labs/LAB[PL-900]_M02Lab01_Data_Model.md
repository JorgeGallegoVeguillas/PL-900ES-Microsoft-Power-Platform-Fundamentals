---
lab:
    title: 'Laboratorio: Modelado de datos'
    module: 'Módulo 2: Introducción a Common Data Service'
---

# Módulo 2: Introducción a Common Data Service
## Laboratorio: Modelado de datos


Escenario
========
    
Bellows College es una institución educativa que tiene un campus con varios edificios. Actualmente se guarda un registro físico de las visitas al campus. La información no se recaba de manera uniforme y no hay forma de recopilar y analizar los datos sobre las visitas de todo el campus. 

La administración del campus querría modernizar el sistema de registro de visitantes de los edificios cuyo acceso esté controlado por el personal de seguridad y en los que los anfitriones deban anotar con antelación las visitas y dejar constancia de ellas.

A lo largo de este curso creará aplicaciones y realizará la automatización para permitir que el personal de administración y seguridad de Bellows College administre y controle el acceso a los edificios del campus. 

En este laboratorio, deberá configurar un entorno, crear una base de datos de Common Data Service (CDS) y diseñar una solución para realizar un seguimiento de los cambios. También creará un modelo de datos que cumpla con los siguientes requisitos:

-   R1: Hacer un seguimiento de las ubicaciones (edificios) del campus en las que se producen las visitas
-   R2: Registrar información básica para identificar y hacer un seguimiento de los visitantes 
-   R3: Programar, registrar y administrar visitas 

Por último, importará los datos de muestra en Common Data Service.

Pasos de alto nivel del laboratorio
======================

Para preparar sus entornos de aprendizaje tendrá que:

* crear una solución y un publicador
* agregar los componentes nuevos y existentes que se necesitan para cumplir con los requisitos de la aplicación. Consulte la descripción de los metadatos (entidades y relaciones) en el [documento del modelo de datos](https://github.com/MicrosoftLearning/PL-900-Microsoft-Power-Platform-Fundamentals/raw/master/Allfiles/Labs/Campus%20Management.png). Puede mantener presionada la tecla CTRL y hacer clic o hacer clic con el botón derecho en el vínculo para abrir el documento del modelo de datos en una nueva ventana.

Su solución contendrá varias entidades al completar todas las personalizaciones:

-   Contacto
-   Edificio
-   Visita

## Requisitos previos:

* Ninguno

Cuestiones que tener en cuenta antes de comenzar:
-----------------------------------

* Convención de nomenclatura
* Tipos de datos, restricciones (por ejemplo, la longitud máxima de un nombre)
* Formato de datetime para facilitar la localización

Ejercicio 1: Crear el entorno y la solución
==================================================

**Objetivo:** En este ejercicio, preparará el entorno y creará una solución que admita los procesos de modelado de datos. 

Tarea 1: Crear un entorno
-----------------------------

En esta tarea creará un nuevo entorno de trabajo si todavía no lo tiene ni lo ha recibido antes del ejercicio. De lo contrario, puede pasar a la siguiente tarea.

1.  Inicie sesión en <https://aka.ms/ppac>

2.  Seleccione **Entornos** y haga clic en **Nuevo** en el menú superior. Esto hará que se abra
    un menú a la derecha de la ventana.

3.  Escriba **Bellows College [Su apellido]** en **Nombre**,

4.  Seleccione **Producción** en el menú desplegable **Tipo.**

5.  Seleccione su **Región**

6.  Introduzca el **Propósito** para crear este entorno (opcional). 
    
7.  Habilite el **botón de alternancia** con el fin de **crear una base de datos para este entorno** si
    desea crear una base de datos en este paso; si no, podrá hacerlo cuando
    haya configurado el entorno.

8.  Haga clic en **Siguiente**.

9.  Seleccione el **Idioma** y la **Divisa**. Para estos laboratorios, los
    entornos tienen seleccionados **Inglés** y **Dólares estadounidenses** (USD).

10. Para estos laboratorios, deshabilite la opción **Habilitar aplicaciones de Dynamics 365**.
    .

11. Para estos laboratorios, deshabilite la opción **Implementar aplicaciones y datos de ejemplo**
    .

12. Haga clic en **Guardar**.

13. El aprovisionamiento del entorno podría tardar unos minutos. Puede hacer clic en el botón **Actualizar** para actualizar la lista. Cuando se haya aprovisionado el entorno, el **Estado** cambiará a Listo.

14. Si no creó previamente su base de datos, seleccione su entorno y haga clic en **Crear mi base de datos**. De lo contrario, omita este paso.

    - Seleccione **Divisa** e **Idioma**. Para estos laboratorios, los
    entornos tienen seleccionados **Dólares estadounidenses** (USD) e **Inglés**.

    - Haga clic en **Crear mi base de datos**.

Tarea 2: Crear la solución y el editor
---------------------------------------

1.  Cree la solución

    -   Inicie sesión en <https://make.powerapps.com>

    -   Seleccione su entorno haciendo clic en **Ambiente** en la esquina superior derecha de la pantalla y elija su entorno en el menú desplegable.

    -   Seleccione **Soluciones** en el menú de la izquierda y haga clic en **Nueva solución**.

    -   Escriba **Administración del campus** en **Nombre para mostrar**.

2.  Cree un editor

    -   Haga clic en el menú desplegable **Editor** y seleccione **+ Editor**.

    -   En la ventana que aparece, introduzca **Bellows College** en **Nombre para mostrar** y **bc** en **Prefijo**

    -   Haga clic en **Guardar y cerrar**. 
    
    -   Haga clic en **Listo** en la ventana emergente.

3.  Complete la creación de la solución.

    -   Luego, haga clic en el menú desplegable **Editor** y seleccione el publicador **Bellows College**
        que acaba de crear.

    -   Valide que la **Versión** esté establecida en **1.0.0.0** 
    
    -   Haga clic en **Crear**.

Tarea 3: Agregar una entidad existente
-----------------------------

1.  Haga clic para abrir la solución **Administración del campus** que acaba de crear.
2.  Haga clic en **Agregar existente** y seleccione **Entidad**.
3.  Localice el **Contacto** y selecciónelo.
4.  Haga clic en **Siguiente**.
5.  Haga clic en **Seleccionar componentes**.
6.  Seleccione la pestaña **Vistas** y elija la vista **Contactos activos**. Haga clic en
    **Agregar**.
7.  Haga clic nuevamente en **Seleccionar componentes**.
8.  Seleccione la pestaña **Formulario** y elija el formulario **Contacto**.
9.  Haga clic en **Agregar**.
10. Debería tener **1 vista** y **1 formulario** seleccionados. Haga clic en **Agregar**.
    Esto agregará la entidad de contacto con la vista y el formulario seleccionados a la solución recién creada. 
11.  Su solución ahora debería tener una entidad: Contacto.

Ejercicio 2: Crear entidades y relaciones
========================================

**Objetivo:** En este ejercicio creará entidades y agregará relaciones
entre ellas.

Tarea 1: Crear entidad y campos de edificios
-----------------------------------------

1.  Aún debe tener su explorador abierto a la solución Campus Management. De lo contrario, abra la solución Campus Management siguiendo estos pasos:
    * Regístrese en <https://make.powerapps.com> (si aún no lo ha hecho)
    * Seleccione **Soluciones** y haga clic para abrir la solución **Administración del campus**
          que acaba de crear.
2.  Cree una entidad de edificio

    -   Haga clic en **Nuevo** y seleccione **Entidad**.
    -   Introduzca **Edificio** para **Nombre para mostrar**. 
    -   Haga clic en **Listo**. Esto hará que
            comience a aprovisionarse en segundo plano y podrá comenzar a agregar
            otras entidades y campos.

## Tarea 2: Crear entidad y campos de visita

La entidad **Visita** contendrá información sobre las visitas al campus, incluyendo el edificio, el visitante, la hora programada y la hora real de cada visita. 

Nos gustaría asignar a cada visita un número único que el visitante pueda ingresar e interpretar fácilmente cuando se le solicite durante el proceso de registro de la visita.

> [NOTA]
> Utilizamos el comportamiento de **Zona horaria independiente** para registrar información de la fecha y hora, ya que el horario de una visita es *siempre* local para la ubicación del edificio y no debe cambiar cuando se ve desde una zona horaria diferente. 

1. Seleccione solución **Administración del campus**
2. Cree una entidad Visita

   * Haga clic en **Nuevo** y seleccione **Entidad**.
   * Especifique **Visita** para **Nombre para mostrar**. 
   * Haga clic en **Listo**. Esto iniciará el aprovisionamiento de la entidad en segundo plano y podrá comenzar a agregar otros campos.

3. Cree el campo Inicio programado

   * Asegúrese de tener la pestaña **Campos** seleccionada y haga clic en **Agregar campo**.
   * Escriba **Inicio programado** para **Nombre para mostrar**.
   * Seleccione **Fecha y hora** para **Tipo de datos**.
   * En el campo **Requerido**, seleccione **Requerido**.
   * Expanda la sección **Opciones avanzadas**.
   * En el campo **Comportamiento**, seleccione **Zona horaria independiente**.
   * Haga clic en **Listo**.

4.  Cree el campo Fin programado

    * Haga clic en **Agregar campo**.
    * Especifique **Fin programado** en **Nombre para mostrar**.
    * Seleccione **Fecha y hora** para **Tipo de datos**.
    * En el campo **Requerido**, seleccione **Requerido**.
    * Expanda la sección **Opciones avanzadas**.
    * En el campo **Comportamiento**, seleccione **Zona horaria independiente**.
    * Haga clic en **Listo**.
    
6.  Cree el campo Inicio real

    * Haga clic en **Agregar campo**.
    * Especifique **Inicio real** para el **Nombre para mostrar**.
    * Seleccione **Fecha y hora** para **Tipo de datos**.
    * Expanda la sección **Opciones avanzadas**.
    * En el campo **Comportamiento**, seleccione **Zona horaria independiente**.
    * Haga clic en **Listo**.
    
7.  Cree el campo Fin real

    * Haga clic en **Agregar campo**.
    * Especifique **Fin real** para **Nombre para mostrar**.
    * Seleccione **Fecha y hora** para **Tipo de datos**.
    * Expanda la sección **Opciones avanzadas**.
    * En el campo **Comportamiento**, seleccione **Zona horaria independiente**.
    * Haga clic en **Listo**.
    
7.  Cree el campo Código

    * Haga clic en **Agregar campo**.
    * Especifique **Código** para **Nombre para mostrar**.
    * Seleccione **Autonumeración** para **Tipo de datos**.
    * Seleccione **Número prefijado de fecha** para **Tipo de autonumeración**.
    * Haga clic en **Listo**.
    
8.  Haga clic en **Guardar entidad**

Tarea 3: Crear relaciones
------------------------------

1.  Asegúrese de que todavía está viendo la entidad **Visita** de la solución **Gestión del campus**. Si no es así, desplácese hasta allí.
2.  Cree una relación de visita a contacto
    * Seleccione la pestaña **Relaciones**.
    * Haga clic en **Agregar relación** y seleccione **Varios a uno**.
    * Seleccione **Contacto** para **Relacionados (uno)** 
    * Especifique **Visitante** para **Nombre para mostrar del campo de búsqueda** 
    * Haga clic en **Listo**.
3.  Cree la relación de visita a edificio
    * Haga clic en **Agregar relación** y seleccione **Varios a uno**.
    * Seleccione **Edificio** para **Relacionados (uno)** 
    * Haga clic en **Listo**.
4.  Haga clic en **Guardar entidad**.
5.  Seleccione **Soluciones** desde el menú superior y haga clic en **Publicar todas las personalizaciones**.

# Ejercicio 3: Importar datos

**Objetivo:** En este ejercicio importará datos de muestra a la base de datos de Common Data Service.

## Tarea 1: Importar asignación de datos

1. Descargue [CampusDataMap.xml](../../Allfiles/Labs/CampusDataMap.xml) si aún no lo ha hecho.
2. Vaya al Centro de administración de Power Platform en <https://admin.powerplatform.microsoft.com> e inicie sesión.
3. Seleccione su entorno de Bellows College.
4. Haga clic en **Configuraciones** en la parte superior.
5. Expanda la sección **Administración de datos**, luego seleccione **Asignaciones de datos**. Esto abrirá la pantalla de importar asignación en una nueva pestaña del explorador.
6. Haga clic en **Importar**, luego haga clic en **Elegir archivo**. Localice y seleccione **CampusDataMap.xml** descargado anteriormente y luego presione **Aceptar**. 
7. Se debe importar correctamente el archivo del mapa de datos del campus. Si encuentra un error, regrese y valide todas las entidades que ha creado y los campos requeridos de las tareas anteriores.
8. Seleccione **Soluciones** desde el menú superior y haga clic en **Publicar todas las personalizaciones.**

## Tarea 2: Importar datos  

1. Descargue [CampusData.zip](../../Allfiles/Labs/CampusData.zip).
2. Vaya al Centro de administración de Power Platform en <https://admin.powerplatform.microsoft.com>.
3. Seleccione su entorno de Bellows College.
4. Haga clic en **Configuraciones** en la parte superior.
5. Expanda la sección **Administración de datos**, luego seleccione **Asistente para la importación de datos**.
6. Presione **IMPORTAR DATOS**.
7. Haga clic en **Elegir archivo**, luego localice y seleccione el archivo **CampusData.zip** descargado anteriormente.
8. Presione **Siguiente**, luego vuelva a presionar **Siguiente**.
9. Seleccione **CampusImportDataMap**, presione **Siguiente**.
10. Revise el resumen de la asignación, luego presione **Siguiente** y después presione **Enviar**.
11. Presione **Finalizar**.
12. La importación de datos comenzará ahora. Ahora puede usar el botón Actualizar en el lado derecho de la pantalla Mis importaciones para actualizar la tabla hasta que las cuatro importaciones tengan un **Motivo de estado** de **Completadas**. Este proceso puede durar unos minutos.

## Tarea 3: Verificar la importación de datos

1. Seleccione la solución **Administración del campus**. Si aún no lo tiene abierto, vaya a make.powerapps.com y haga clic en soluciones en el panel izquierdo para ubicar su solución.*
2. Seleccione entidad **Visita** y luego la pestaña **Datos**.
3. Haga clic en **Visitas activas** en la esquina superior derecha para mostrar el selector de vista, luego seleccione **Todos los campos**
4. Si la importación se realizó correctamente, debería ver una lista de las entradas de visitas.
5. Haga clic en cualquier valor en la columna **Edificio**, confirme que el formulario de edificio se abre en una ventana separada.
6. Haga clic en cualquier valor en la columna **Visitante** (es posible que deba desplazar la vista hacia la derecha), confirme que el formulario de contacto se abra en una ventana separada.

# Desafíos

* ¿Consideraría usar la actividad de *cita* como parte de la solución? ¿Qué cambiaría?
* ¿Cómo hacer cumplir el final programado después del inicio programado? 
* Agregue soporte técnico para múltiples reuniones durante una sola visita.
* Asegure el acceso al edificio no solo para los contactos externos, sino también para el personal interno.
* Las visitas a ciertos edificios requieren la aprobación de la gerencia. ¿Qué cambiaría el proceso de aprobación en el modelo de datos?

