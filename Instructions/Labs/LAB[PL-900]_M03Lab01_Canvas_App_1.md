---
lab:
    title: 'Laboratorio: Aplicación de lienzo, parte 1'
    module: 'Módulo 3: Comenzar con Power Apps'
---

# Módulo 3: Comenzar con Power Apps
## Laboratorio: Aplicación de lienzo, parte 1

Escenario
========

Bellows College es una institución educativa que tiene un campus con varios edificios. Actualmente se guarda un registro físico de las visitas al campus. La información no se recaba de manera uniforme y no hay forma de recopilar y analizar los datos sobre las visitas de todo el campus. 

La administración del campus querría modernizar el sistema de registro de visitantes de los edificios cuyo acceso esté controlado por el personal de seguridad y en los que los anfitriones deban anotar con antelación las visitas y dejar constancia de ellas.

A lo largo de este curso, creará aplicaciones y realizará la automatización para permitir que el personal de administración y seguridad de Bellows College administre y controle el acceso a los edificios en el campus.  

En la parte 1 de este laboratorio, creará una aplicación de lienzo de Power Apps que el personal de la universidad pueda usar para administrar las visitas de sus invitados.

Pasos de alto nivel del laboratorio
======================

Seguiremos el siguiente esquema para diseñar la aplicación de lienzo:

-   Crear la aplicación a partir de datos utilizando la plantilla de factor de forma del teléfono
-   Configurar una página de detalles con información de las visitas
-   Configurar una página de edición para crear en las visitas
-   Configurar un control de galería para mostrar las visitas
-   Agregar filtros en el origen de datos de la galería para mostrar solo visitas futuras

## Requisitos previos

* Finalización del laboratorio 1: modelado de datos

Cuestiones que tener en cuenta antes de comenzar
-----------------------------------

-   ¿Cuál es el factor de forma más frecuente para el público objetivo?
-   Estimar el número de registros en el sistema 
-   Cómo reducir los registros seleccionados para mejorar el rendimiento de la aplicación y la adopción del usuario


Ejercicio 1: Creación de una aplicación de lienzo del personal
===============================

**Objetivo:** en este ejercicio creará una aplicación de lienzo a partir de una plantilla y, luego, la modificará para incluir los datos requeridos.

Tarea n.° 1: Creación de una aplicación de lienzo
---------------------------

En esta tarea creará una aplicación de lienzo utilizando la plantilla de diseño del teléfono basada en Common Data Service. Usando Visitas como una entidad seleccionada de Common Data Service, la plantilla generará la aplicación Galería - Ver - Editar aplicación para administrar las visitas al campus.

1.  Abra la solución de Administración del campus.

    -   Inicie sesión en <https://make.powerapps.com>

    -   Seleccione su **entorno** en la parte superior derecha, si aún no está configurado en su entorno de Bellows College.

    -   Seleccione **Aplicaciones**.

2.  Cree nueva aplicación de lienzo

    -   Haga clic en **Nueva aplicación** y seleccione **Lienzo**.
    
    -   Seleccione **Diseño del teléfono** debajo de **Common Data Service**.
    
-   Seleccione conexión **Common Data Service** y, luego, haga clic en **Crear**.

    -   Seleccione la tabla **Visitas**
    
    -   Haga clic en **Conectar**
    
    -   Puede aparecer la ventana **Bienvenido a Power Apps Studio**. Haga clic en **Omitir**.
    
3.  Guardar aplicación

    1.  Haga clic en **Archivo > Guardar**.
    
    2.  Escriba el nombre de la aplicación como **Personal del campus**
    
    3.  Presione **Guardar**.

Tarea n.° 2: Configurar el formulario de detalles de visitas
--------------------------------

En esta tarea, configurará un formulario de detalles para ver información sobre el registro de las visitas individuales.

1.  Seleccione la flecha Atrás en la esquina superior izquierda para volver a la definición de la aplicación.
2. Expanda **DetailScreen1** debajo de **Vista de árbol**
3.  Seleccione **DetailForm1**
4.  Seleccione **Editar campos** al lado de **Campos** del panel del lado derecho.
5.  Haga clic en **Agregar campo**
6.  Seleccione los siguientes campos:
    * Final real
    * Comienzo real
    * Edificio 
    * Código
    * Final programado
    * Inicio programado
    * Visitante
7.  Haga clic en **Agregar**
8.  Reorganice los campos del panel **Campos** arrastrando y soltando los nombres de campo hacia arriba o hacia abajo. El orden recomendado es:
    * Código, Nombre, Edificio, Visitante, Inicio programado, Final programado, Inicio real, Final real
9.  Para conservar el trabajo en curso, haga clic en **Archivo** y, a continuación, haga clic en **Guardar**. Use la flecha hacia atrás para volver a la aplicación.

## Tarea n.° 3: Configurar el formulario de edición de visitas 

En esta tarea, configurará un formulario para editar información sobre el registro de visitas individuales.

1.  Expanda **EditScreen1** debajo de **Vista de árbol**
2.  Seleccione **EditForm1**
3.  Seleccione el campo **Creado en** y presione la tecla **Supr** para quitar el campo
4.  Seleccione **Editar campos** en el panel de propiedades
5.  Haga clic en **Agregar campo**
6.  Seleccione los siguientes campos
    * Edificio 
    * Final programado
    * Inicio programado
    * Visitante
7.  Haga clic en **Agregar**
8.  Reorganice los campos del panel **Campos** arrastrando y soltando los nombres de campo hacia arriba o hacia abajo. El orden recomendado es:
    * Nombre, Edificio, Visitante, Inicio programado, Fin programado
9.  Para conservar el trabajo en curso, haga clic en **Archivo** y, a continuación, haga clic en **Guardar**. Use la flecha hacia atrás para volver a la aplicación.

Tarea n.° 4: Configurar la galería de visitas
---------------------------------------

En esta tarea, configurará la galería pregenerada para mostrar el título, las fechas de inicio y la finalización de la visita. 

1.  Expandir **BrowseScreen1** debajo de **Vista de árbol**
2.  Seleccione **BrowseGallery1**
3.  Seleccione la propiedad **TemplateSize** del menú desplegable de propiedades
4.  Reemplace la expresión con lo siguiente `Min(150, BrowseGallery1.Height - 60)`. Eso asegurará suficiente espacio para información adicional.
5.  Edite la galería presionando el ícono del lápiz en la esquina superior izquierda de la galería (desplace el cursor sobre la vista previa de la aplicación y haga clic en el ícono del lápiz).
6.  Seleccione el campo Fecha Hora.
7.  En la barra de fórmulas en la parte superior, cambie `ThisItem.'Created On'` a `ThisItem.'Scheduled Start'`
8.  Seleccione el campo de nuevo
9.  Presione `CTRL-C` y, luego, `CTRL-V` para crear una copia del campo.
10.  Con el ratón o el teclado, mueva el control copiado hacia abajo y alinéelo con los otros controles de la galería, debajo del otro campo de Fecha Hora.
11.  En la barra de fórmulas en la parte superior, cambie `ThisItem.'Scheduled Start'` a `ThisItem.'Scheduled End'`
12.  Para conservar el trabajo en curso, haga clic en **Archivo** y, a continuación, haga clic en **Guardar**. Use la flecha hacia atrás para volver a la aplicación.

## Tarea n.° 5: Agregar filtros de fecha

Debido a que el número de visitas crece continuamente, los usuarios necesitan una función para filtrar la galería de visitas. Por ejemplo, el usuario puede querer ver solo las visitas futuras. En esta tarea, agregará la capacidad de mostrar visitas solo después de la fecha seleccionada por el usuario.

1. Seleccione el menú **Insertar** en la parte superior.

2. Haga clic en **Entrada** y seleccione **Selector de fechas**.

3. Usando el teclado o el mouse, coloque el control debajo del cuadro de búsqueda.

4. Seleccione **BrowseGallery1** 

5. Cambie el tamaño y mueva el control de la galería para que se encuentre debajo del selector de fecha y cubra la pantalla. Puede hacer esto haciendo clic en el icono de cambio de tamaño en el centro superior del control de la galería y cambiando el tamaño del control para comenzar después del selector de fecha.

6. Mientras sigue seleccionando **BrowseGallery1**, haga clic en la pestaña **Avanzado** del panel Propiedades y busque la propiedad **Artículos**.

7. En la expresión, ubique `[@Visits]` y reemplácelos con `Filter(Visits,'Scheduled End' >= DatePicker1.SelectedDate)`. La expresión debería tener la siguiente apariencia:

   ```
   SortByColumns(
   	Search(
        Filter(
        	Visits,
            'Scheduled End' >= DatePicker1.SelectedDate
           ),
           TextSearchBox1.Text,
       	"bc_code","bc_name"
       ),
     "bc_code",
     If(SortDescending1, Descending, Ascending)
   )
   ```
   
8. Para conservar el trabajo en curso, haga clic en **Archivo** y, a continuación, haga clic en **Guardar**. Use la flecha hacia atrás para volver a la aplicación.

# Ejercicio 2: Completar la aplicación

En este ejercicio probará la aplicación y, una vez que tenga éxito, la agregará a su solución.

Tarea n.° 1: Probar aplicación
--------------------------

1.  Inicie la aplicación

    -   Seleccione el **BrowseScreen1** y presione **F5**, o haga clic en el icono Reproducir en la esquina superior derecha para obtener una vista previa de la aplicación.
    -   La aplicación debe cargar y mostrar una lista de visitas. 
    -   Pruebe el filtro seleccionando diferentes fechas en el control del selector de fechas
    -   Seleccione una visita y compruebe que el formulario de visualización funcione correctamente
    -   Regrese a la galería y presione + para crear una nueva visita. Compruebe que el formulario de edición contenga los campos obligatorios, incluidos los visitantes, el edificio y las fechas de inicio y finalización programadas.
    -   Rellene la información y envíela. Compruebe que el nuevo registro aparezca en la galería.
    -   Presione la tecla **ESC** para cerrar la aplicación

2.  Guarde y publique la aplicación

    -   Haga clic en **Archivo** y luego en **Guardar**.

    -   Haga clic en Publicar.

    -   Haga clic en **Publicar esta versión**.

    -   Haga clic en la flecha hacia atrás para volver a la aplicación.

    -   Cierre la ventana o pestaña del explorador **Diseñador**.

    -   Haga clic en **Salir** si se le solicita cuando intenta cerrar la ventana del explorador.


## Tarea n.°2: Agregar aplicación a la solución y publicar 

1. Abra la solución de Administración del campus.
   * Inicie sesión en <https://make.powerapps.com>
   * Si el entorno que se muestra en la esquina superior derecha no es su entorno de Bellows College, seleccione su **Entorno**. 
   * Seleccione **Soluciones**.
   * Haga clic para abrir la solución de **Administración del campus**.
2. Seleccione **Agregar existente**, luego haga clic en **App** y luego haga clic en **Aplicación de lienzo**.
3. Seleccione la pestaña **Soluciones externas**.
4. Seleccione la aplicación **Personal del campus**, haga clic en **Agregar**.
5. Seleccione **Publicar todas las personalizaciones**.

# Desafíos

* Vista del calendario de todas las visitas y filtrado por intervalo de fechas
* Capacidad para crear y administrar contactos como parte de la aplicación
* Cómo mostrar varias reuniones durante una sola visita

