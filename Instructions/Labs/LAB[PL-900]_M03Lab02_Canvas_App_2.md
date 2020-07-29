---
lab:
    title: 'Laboratorio: Aplicación de lienzo, Parte 2'
    module: 'Módulo 3: Comenzar con Power Apps'
---

# Módulo 3: Comenzar con Power Apps
## Laboratorio: Aplicación de lienzo, Parte 2

Escenario
========

Bellows College es una institución educativa que tiene un campus con varios edificios. Actualmente se guarda un registro físico de las visitas al campus. La información no se recaba de manera uniforme y no hay forma de recopilar y analizar los datos sobre las visitas de todo el campus. 

La administración del campus querría modernizar el sistema de registro de visitantes de los edificios cuyo acceso esté controlado por el personal de seguridad y en los que los anfitriones deban anotar con antelación las visitas y dejar constancia de ellas.

A lo largo de este curso, creará aplicaciones y realizará la automatización para permitir que el personal administrativo y de seguridad de Bellows College administre y controle el acceso a los edificios del campus. 

En la parte 2 de este laboratorio, creará, diseñará y compilará una aplicación de lienzo de Power Apps que el personal de seguridad usará en las entradas del edificio para confirmar y registrar rápidamente a los visitantes.

Pasos de alto nivel del laboratorio
======================

Seguirá el siguiente esquema para diseñar la aplicación de lienzo:

-   Crear la aplicación usando el factor de forma del teléfono
-   Conectarse a Common Data Service como un origen de datos
-   Capturar la entrada (código de visitante) y ubicar el registro de visitante
-   Configurar un control de visor de formularios para mostrar la información del visitante
-   Usar una vista de CDS para rellenar la galería
-   Manejar el proceso de entrada y salida para un visitante


## Requisitos previos

* Finalización del laboratorio 1: modelado de datos

Cuestiones que tener en cuenta antes de comenzar
-----------------------------------

-   ¿A qué información necesitaría un responsable de seguridad acceso rápido?
-   ¿Qué debería pasar si el código de visitante es inválido?
-   ¿Qué debería pasar si el visitante llega fuera de las horas programadas? 

Ejercicio 1: Creación de una aplicación de lienzo
===============================

**Objetivo:** En este ejercicio aprenderá a crear una aplicación de lienzo.

Tarea n.° 1: Creación de una aplicación de lienzo
---------------------------

1.  Abra la solución de Administración del campus.

    -   Inicie sesión en <https://make.powerapps.com>

    -   Si el entorno que se muestra en la esquina superior derecha no es su entorno de Bellows College, seleccione su **Entorno**. 

    -   Seleccione **Soluciones**.

    -   Haga clic para abrir la solución de **Administración del campus**.
2.  Cree nueva aplicación de lienzo

    -   Haga clic en **Nuevo** y seleccione **Aplicación \| Aplicación de lienzo \| Factor de forma de teléfono**.
        Esto abrirá el Editor de aplicaciones en una Nueva ventana.
    -   Si está creando su primera aplicación, esto le pedirá que configure el
        País / región para la aplicación. Haga clic en **Introducción.**
    -   Haga clic en Archivo y seleccione Guardar como.
    -   Compruebe si **La nube** está seleccionada. Introduzca **Seguridad del campus** para Nombre y
        haga clic en **Guardar**. Esto asegurará que los cambios no se pierdan si la aplicación se cierra de forma inesperada.
    -   Haga clic en la flecha de retroceso de la esquina superior derecha (debajo de "Power Apps") para volver a la aplicación.

3.  Conectarse al origen de datos (Visitas)
    1.  Haga clic en **Ver \| Orígenes de datos**
    2.  Haga clic en **Agregar datos**
    3.  Haga clic en **Ver todas las entidades**
    4.  Seleccione **Visitas** y espere a que la entidad Visita se muestre en Orígenes de datos.
4.  Para guardar el trabajo en curso, haga clic en **Archivo \| **Seleccione **Guardar** y, luego, pulse **Guardar**.

Tarea n.°2: Mostrar Información del visitante
--------------------------------

1.  Agregar cuadro de búsqueda

    -   Seleccione la pestaña **Vista de árbol** en la parte izquierda.
    -   Seleccione **Screen1**.
    -   Vaya a la pestaña **Insertar**.
    -   Haga clic en **Texto** y seleccione **Entrada de texto**.
    -   Seleccione el texto de la propiedad **Predeterminada** y borre el valor.
    -   Seleccione la propiedad **HintText** e introduzca **"Introducir el código de visitante"** como valor (incluidas las comillas)
    -   Haga clic en ... junto al nombre de control en una vista de árbol, seleccione **Cambiar nombre** y cambie el nombre a **textCode**
2. Agregar vista Formulario

   -   En la pestaña **Insertar**, haga clic en **Formularios** y luego seleccione **Mostrar**
   -   Coloque el formulario debajo del cuadro de texto de búsqueda usando los controladores de tamaño
   -   Seleccione la propiedad **DataSource** e introduzca **Visitas**
   -   En el panel propiedades, seleccione **Horizontal** como **Diseño**
   -   Haga clic en **Editar campos**
   -   Haga clic en **Agregar campo** y seleccione los siguientes campos: Final real, Inicio real, Edificio, Final programado, Inicio programado, Visitante
   -   Presione **Agregar**
   -   Para cambiar el orden de los campos seleccionados, arrastre las tarjetas de campo en la lista. El orden recomendado es Visitante, Generar, Inicio programado, Fin programado, Inicio real, Fin real
   -   En la pestaña Avanzado, seleccione la propiedad **Item** y escriba `LookUp(Visits, Code = textCode.Text)`

3.  Para guardar el trabajo en curso, haga clic en **Archivo \| **Seleccione **guardar** y, luego, pulse **Guardar**. Haga clic en la flecha de retroceso de la esquina superior derecha (debajo de "Power Apps") para volver a la aplicación.

4. Pruebe la aplicación

   -   Cambie a la pestaña del explorador que contiene la solución
   -   Seleccione la entidad  **Visita**
   -   Seleccione la pestaña **Datos**
   -   Abra el Selector de vistas de la esquina superior derecha haciendo clic en el nombre de la vista actual (Visitas activas)
   -   Cambie la vista a **Todos los campos**
   -   Busque un registro de visita que no tenga un valor de inicio real o de final real. Seleccione y copie el **Código** de esta visita.
   -   Cambie a la pestaña del explorador con la aplicación y presione F5 para ejecutar la aplicación
   -   Pegue el valor copiado en el cuadro de texto de búsqueda, compruebe que el registro se muestre en el formulario
   -   Borre el contenido del cuadro de texto de búsqueda.
5.  Presione **ESC** para salir de la aplicación en ejecución.


Tarea n.° 3: Agregue botones de entrada y salida
---------------------------------------

1. Guarde los resultados de búsqueda en una variable para reutilizar en el control

   * Seleccione el control **textCode**
   * Seleccione la propiedad **OnChange** en la pestaña Avanzado
   * Escriba la siguiente expresión `Set(Visit, LookUp(Visits, Code = textCode.Text))`
     Es la misma expresión que la anterior, excepto que esta vez guardamos los resultados en una variable global. Eso nos permite usar la variable *Visita* en toda la aplicación sin la necesidad de volver a escribir toda la expresión de búsqueda.

2. Agregue botones para entrada y salida
   
   1. Seleccione la pestaña **Insertar**
   2. Haga clic en **Botón**
   3. Cambie la propiedad **Texto** del botón a **"Entrada"** (puede escribir dentro de las comillas existentes)
   4. Cambie el nombre del botón a **CheckInButton** haciendo clic en el nombre del botón (Button1) en el panel derecho
   5. Haga clic en **Botón** para insertar otro botón
   6. Cambie la propiedad **Text** del botón a **"Salida"**
   7. Cambie el nombre del botón a **CheckOutButton**
   8. Coloque los botones uno al lado del otro debajo del registro de la vista Formulario 
   
3. Active y desactive botones dependiendo de los datos de visita 
   Nos gustaría habilitar el botón **Entrada** cuando el registro de visita se haya localizado (no esté en blanco), el estado del registro esté activo y la visita aún no haya comenzado, es decir, el valor de inicio real está en blanco.

   * Seleccione el botón Entrada y haga clic en la propiedad **DisplayMode** del botón en la pestaña Propiedades

   * Introduzca la siguiente expresión en la barra de funciones.

      ```
      If(!IsBlank(Visit) 
      && Visit.Status = 'Status (Visits)'.Active
      && IsBlank(Visit.'Actual Start'),
          DisplayMode.Edit,
          DisplayMode.Disabled
      )
      ```

   La expresión se puede dividir de la siguiente manera:

   * `!IsBlank(Visit)` - se encontró el registro de visita
   * `&&` - operador lógico AND
   * El estado `Visit.Status = 'Status (Visits)'.Active` del registro es *Activo*
   * `IsBlank(Visit.'Actual Start')` - el campo Inicio activo no contiene ningún dato

4. Nos gustaría habilitar el botón **Salida** cuando el registro de visita se haya localizado (no esté en blanco), el estado del registro esté activo y la visita ya haya comenzado, es decir, cuando el valor de inicio real no esté en blanco.

   * Seleccione el botón Salida y haga clic en la propiedad **DisplayMode** del botón en la pestaña Propiedades

   * Introduzca la siguiente expresión en la barra de funciones.

     ```
     If(!IsBlank(Visit) 
     && Visit.Status = 'Status (Visits)'.Active
     && !IsBlank(Visit.'Actual Start'),
         DisplayMode.Edit,
         DisplayMode.Disabled
     )
     ```

5. Para guardar el trabajo en curso, haga clic en **Archivo \| **Seleccione **Guardar** y, luego, pulse **Guardar**. Haga clic en la flecha de retroceso de la esquina superior derecha (debajo de "Power Apps") para volver a la aplicación.

6. Pulse **F5** para ejecutar la aplicación. Ambos botones deben estar deshabilitados. Introduzca el valor del código que copió anteriormente y presione **Pestaña** para alejar el foco del cuadro de texto. El botón **Entrada** debería estar habilitado.

7. Presione **ESC** para salir de la aplicación en ejecución.

## Tarea n.° 4: Proceso completo de entrada y salida

Para realizar el proceso de registro de entrada y salida, debemos actualizar los datos de visita de Common Data Service de la siguiente manera:

* Cuando el visitante registre su entrada, configure el campo *Inicio real* a la fecha y hora actuales
* Cuando el visitante salga, configure el campo *Fin real* a la fecha y hora actuales. 
* Después de la salida, configure el estado del registro como inactivo, lo que indica que la visita se ha completado

1. Seleccione el botón **Entrada**.

2. Establezca la propiedad **OnSelect** a la siguiente expresión.

   ```
   Patch(
       Visits,
       Visit,
       {'Actual Start': Now()}
   );
   Refresh([@Visits]);
   Set(Visit, LookUp(Visits, Code = textCode.Text));
   ```

   Esta expresión contiene las siguientes partes:

   * `Patch(Visits, Visit, {'Actual Start': Now()});`. El método *Parche* actualiza la entidad **Visitas**, el registro identificado por la variable **Visitar** (que es la visita actual). La expresión establece el valor del campo *Inicio real* a la fecha y hora actuales (*Ahora()* método).
   * `Refresh([@Visits]);`. Esta expresión actualiza los registros de visitas a medida que cambian los valores subyacentes
   * `Set(Visit, LookUp(Visits, Code = textCode.Text));` Esta expresión actualiza la variable *Visitar* con datos nuevos de CDS.

3. Seleccione el botón **Salida**.

4. Establezca la propiedad **OnSelect** a la siguiente expresión.

   ```
   Patch(
       [@Visits],
       Visit,
       {
           'Actual End': Now(),
           Status: 'Status (Visits)'.Inactive
       }
   );
   Refresh([@Visits]);
   Set(Visit, LookUp(Visits, Code = textCode.Text));
   ```

   La única diferencia con respecto a la expresión de entrada es la configuración del campo *Estado* al valor *Inactivo*.

5. Para guardar el trabajo en curso, haga clic en **Archivo \| **Seleccione **Guardar** y, luego, pulse **Guardar**.

6. Presione **F5** para ejecutar la aplicación. Introduzca el valor del código que copió anteriormente y presione **Pestaña** para alejar el foco del cuadro de texto. El botón **Entrada** debería estar habilitado.

7. Presione el botón **Entrada**. Ocurrirá lo siguiente:

   1. *Inicio real* tiene una fecha y hora actual
   2. El botón **Entrada** está deshabilitado
   3. El botón **Salida** está habilitado

8. Presione el botón **Salida**.

   1. *Fin real* tiene una fecha y hora actual
   2. Ambos botones están deshabilitados

9. Presione **ESC** para salir de la aplicación en ejecución

Tarea 5: Agregar indicadores visuales
--------------------------------------

La usabilidad de una aplicación móvil mejora significativamente cuando, además de la información de texto, se proporcionan los indicadores visuales. En esta tarea agregaremos un icono que indica si un visitante puede registrar su entrada o salida.

1. Seleccione la pestaña **Insertar**

2. Seleccione **Iconos \| Agregar**. En este punto, no importa qué icono seleccionemos, ya que queremos que el valor sea dinámico.

3. Cambie el tamaño y coloque el icono en el centro de la pantalla debajo de los botones

4. En la pestaña Avanzado del icono, seleccione Propiedad del **icono** (en la sección Diseño) e introduzca la siguiente expresión:

   ```
   If(
      CheckInButton.DisplayMode = DisplayMode.Disabled 
   && CheckOutButton.DisplayMode = DisplayMode.Disabled,
       Icon.EmojiFrown,
       Icon.EmojiSmile
   )
   ```

5. Para guardar el trabajo en curso, haga clic en **Archivo \| Guardar** y, luego, pulse **Guardar**.
6. Presione **F5** para ejecutar la aplicación. Introduzca el valor del código que copió anteriormente y presione **Pestaña** para alejar el foco del cuadro de texto. Compruebe que el icono muestre un emoji con el ceño fruncido.
7. Encuentre un valor de código diferente que no se haya usado antes (no debe tener un valor inicial real ni un valor final real). En este momento, puede ejecutar la aplicación creada previamente **Personal del campus** para crear nuevos registros de visitas. Compruebe que el icono muestre un emoji sonriente.
8. Presione **ESC** para salir de la aplicación en ejecución

## Tarea n.º 6: Publique la aplicación

1. Debe tener abierta aún la aplicación Seguridad del campus en el navegador. De lo contrario, seleccione la aplicación **Seguridad del campus** y haga clic en **Editar**.
2. Seleccione **Archivo \| Publicar** 
3. Seleccione **Publicar esta versión**

# Desafíos

* ¿Cómo evitar la entrada manual del código de visita?
* Agregue una validación de creación para la visita
* Agregue validación del tiempo real de la visita frente al tiempo programado de la visita (demasiado temprano, demasiado tarde, etc.)
* Agregue el estado detallado de la visita, por ejemplo, visualización de correo electrónico y validación para el visitante, razón para denegar el acceso al edificio, etc.
* ¿Cómo manejaría el requisito de múltiples edificios/reuniones/chequeos durante la única visita al campus? Por ejemplo, alguien puede visitar el campus por un día y durante ese día se reunirán con miembros del personal en varios edificios a diferentes horas del día. ¿Consideraría traer la entidad *cita* a la solución?
