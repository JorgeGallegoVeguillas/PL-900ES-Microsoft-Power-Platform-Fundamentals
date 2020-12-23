---
lab:
    title: 'Laboratorio 3: Cómo crear una aplicación de lienzo, parte 2'
    module: 'Módulo 3: Comenzar con Power Apps'
---

# Módulo 3: Comenzar con Power Apps
## Laboratorio 2: Cómo crear una aplicación de lienzo, parte 2

# Escenario

Bellows College es una institución educativa que tiene un campus con varios edificios. Actualmente se guarda un registro físico de las visitas al campus. La información no se recaba de manera uniforme y no hay forma de recopilar y analizar los datos sobre las visitas de todo el campus. 

La administración del campus querría modernizar el sistema de registro de visitantes de los edificios cuyo acceso esté controlado por el personal de seguridad y en los que los anfitriones deban anotar con antelación las visitas y dejar constancia de ellas.

A lo largo de este curso, creará aplicaciones y realizará la automatización para permitir que el personal de administración y seguridad de Bellows College administre y controle el acceso a los edificios en el campus. 

En la parte 2 de este laboratorio, creará, diseñará y compilará una aplicación de lienzo Power Apps que el personal de seguridad utilizará en las entradas del edificio para confirmar y registrar rápidamente a los visitantes.

# Pasos de alto nivel del laboratorio

Seguirá el siguiente esquema para diseñar la aplicación de lienzo:

-   Crear la aplicación usando el factor de forma del teléfono
-   Conectarse a Common Data Service como un origen de datos
-   Capturar la entrada (código de visitante) y ubicar el registro de visitante
-   Configurar un control de visor de formularios para mostrar la información del visitante
-   Utilice una vista de Common Data Service para rellenar la galería
-   Manejar el proceso de entrada y salida para un visitante

## Requisitos previos

* Finalización del **Módulo 0 Laboratorio 0: Validación del entorno de laboratorio**
* Finalización del **Módulo 2 Laboratorio 1: Introducción a Common Data Service**

## Cuestiones que tener en cuenta antes de comenzar

-   ¿A qué información necesitaría un responsable de seguridad acceso rápido?
-   ¿Qué debería pasar si el código de visitante es inválido?
-   ¿Qué debería pasar si el visitante llega fuera de las horas programadas? 

# Ejercicio 1: Creación de una aplicación de lienzo

**Objetivo:** En este ejercicio aprenderá a crear una aplicación de lienzo.

## Tarea 1: Creación de una aplicación de lienzo

1.  Abra la solución de Administración del campus.

    -   Inicie sesión en <https://make.powerapps.com>

    -   Si el Entorno que se muestra en la parte superior derecha no es su Entorno de práctica, seleccione su **Entorno**. 

    -   Seleccione **Soluciones**.

    -   Haga clic para abrir la solución de **Administración del campus**.
    
2.  Cree nueva aplicación de lienzo

    -   Haga clic en **Nuevo** y seleccione **Aplicación \| Aplicación de lienzo \| Factor de forma de teléfono**.
        Esto abrirá el Editor de aplicaciones en una Nueva ventana.
        
    -   Haga clic en **Omitir** si se presenta el cuadro de diálogo Bienvenido a Power Apps Studio.
    
3.  Guardar la aplicación de lienzo

    -   Haga clic en **Archivo** y seleccione **Guardar como**.
    
    -   Compruebe si **La nube** está seleccionada. 
    
    -   Escriba **(Su apellido) Seguridad del campus** como Nombre y haga clic en **Guardar**.
        
    -   Haga clic en la flecha **Atrás** de la parte superior izquierda (debajo de Power Apps) para volver a la aplicación.

3.  Conectarse al origen de datos (Visitas)

    -   Haga clic en **Vista \| Orígenes de datos**
    
    -   Haga clic en **Ver todas las entidades**
    
    -   Seleccione **Visitas** y espere a que la entidad Visita se muestre debajo de la sección Datos **en tu aplicación**.
    
4.  Para conservar el trabajo en curso, haga clic en **Archivo** y luego en **Guardar**. Utilice la flecha hacia atrás para volver a la aplicación.

## Tarea 2: Mostrar Información del visitante

1.  Agregar cuadro de búsqueda

    -   Seleccione la pestaña **Vista de árbol** en la barra de navegación izquierda.
    
    -   Seleccione **Screen1**.
    
    -   Vaya a la pestaña **Insertar**.
    
    -   Haga clic en **Texto** y seleccione **Entrada de texto**.
    
2.  Editar el objeto de entrada de texto

    -   Con el objeto de entrada de texto seleccionado, seleccione el texto de la propiedad **Predeterminado** y borre el valor.
    
    -   Seleccione la propiedad **HintText** y especifique `escribir el código de visitante` como valor (incluidas las comillas dobles)
    
    -   Haga clic en **...** junto al nombre del control en la vista de árbol (TextInput1), seleccione **Cambiar nombre** y cambie el nombre a `textCode`.
    
3.  Agregar una vista de formulario

    -   En la pestaña **Insertar**, haga clic en **Formularios** y luego seleccione **Mostrar**
   
    -   Usando controladores de tamaño, coloque el formulario debajo del cuadro de texto de búsqueda
   
    -   Seleccione la propiedad **DataSource** y, luego, **Visitas**.
   
    -   En el panel propiedades, seleccione **Horizontal** como **Diseño**

4.  Editar la vista de formulario

    -   Haga clic en **Editar campos**
   
    -   Haga clic en **Agregar campo** y seleccione los siguientes campos: **Fin real**, **Inicio real**, **Creación**, **Fin programado**, **Inicio programado**, **Visitante**
   
    -   Presione **Agregar**
   
    -   Quite los campos **Nombre** y **Creado en**.
   
    -   Para cambiar el orden de los campos seleccionados, arrastre las tarjetas de campo en la lista. El orden recomendado es: Visitante, Edificio, Inicio programado, Fin programado, Inicio real y Fin real.
   
    -   Haga clic en la **X** para cerrar el panel Campos
   
5.  Con la vista de formulario seleccionada, seleccione la pestaña Avanzado del panel Propiedades. Seleccione la propiedad **Item** y escriba `LookUp(Visits, Code = textCode.Text)` 

6.  Para conservar el trabajo en curso, haga clic en **Archivo** y luego en **Guardar**. Utilice la flecha hacia atrás para volver a la aplicación.

7.  Preparación para probar la aplicación

    -   Cambie a la pestaña del explorador que contiene la solución
   
    -   Seleccione la entidad  **Visita**
   
    -   Seleccione la pestaña **Datos**
   
    -   Abra el selector de vista en la parte superior derecha haciendo clic en el nombre de la vista actual, **Visitas activas**
   
    -   Cambiar la vista a **Todos los campos**
   
    -   Busque un registro de visita que no tenga un valor de Inicio real o Final real. Seleccione y copie el **Código** para esta visita.

8.  Pruebe la aplicación

    -   Cambie a la pestaña del explorador con la aplicación, pulse **F5** o haga clic en el icono **Reproducir** en la esquina superior derecha para obtener una vista previa de la aplicación.
   
    -   Pegue el valor copiado en el cuadro de texto de búsqueda, compruebe que el registro se muestre en el formulario
   
9.  Borre el contenido del cuadro de texto de búsqueda.
   
10.  Presione **ESC** para salir de la aplicación en ejecución.

## Tarea 3: Agregue botones de entrada y salida

En esta tarea, crearemos botones para que el usuario se registre y salga de su Visita. 

1. Guarde los resultados de búsqueda en una variable para reutilizar en el control

    * Seleccione el control **textCode**
   
    * En el panel Propiedades, seleccione la pestaña **Avanzado** y la propiedad **OnChange**
   
    * Escriba la siguiente expresión `Set(Visit, LookUp(Visits, Code = textCode.Text))`
    
    > Esto guardará la visita en una variable global cuando un usuario busque en el cuadro de búsqueda de textCode. Eso nos permite usar la variable *Visita* en toda la aplicación sin la necesidad de volver a escribir toda la expresión de búsqueda.

2. Agregar un botón Entrada

   * Seleccione la pestaña **Insertar**
   
   * Haga clic en **Botón**
   
   * En el panel Propiedades, cambie la propiedad **Texto** del botón a "`Entrada`" (puede escribir dentro de las comillas existentes).
   
   * Haga clic en **...** junto al nombre del botón en una vista de árbol (Button 1), seleccione **Cambiar nombre** y cámbielo a `CheckInButton`

3. Agregar un botón Salida.   

   * Haga clic en **Botón** en la pestaña Insertar para agregar otro botón.
   
   * En el panel Propiedades, cambie la propiedad **Texto** del botón a "`Salida`" (puede escribir dentro de las comillas existentes).
   
   * Cambie el nombre del botón a `CheckOutButton`
   
   * Coloque los botones debajo del cuadro de búsqueda, con **Entrada** encima de **Salida**. 
   
## Tarea 4: Habilitar y deshabilitar botones dependiendo de los datos de visita

Nos gustaría habilitar el botón **Entrada** cuando el registro de visita se haya localizado (no esté en blanco), el estado del registro esté activo y la visita aún no haya comenzado, es decir, el valor de inicio real está en blanco.

1. Seleccione el **botón Entrada** y haga clic en la propiedad **DisplayMode** del botón en la pestaña Propiedades.

2. Escriba la siguiente expresión en la barra de funciones:

      ```
      If(!IsBlank(Visit) 
      && Visit.Status = 'Status (Visits)'.Active
      && IsBlank(Visit.'Actual Start'),
          DisplayMode.Edit,
          DisplayMode.Disabled
      )
      ```

   La expresión se puede dividir de la siguiente manera:

   * **IsBlank(Visit)** - Se encontró el registro de visita.
   * **&&** - logical AND operator
   * **Visit.Status = 'Status (Visits)'.Active** El estado del registro es *Activo*.
   * **IsBlank(Visit.'Actual Start')** - El campo Inicio activo no contiene ningún dato.
   * **DisplayMode.Edit, DisplayMode.Disabled** - Si se cumplen las condiciones anteriores, el botón se podrá editar. De lo contrario, el botón permanecerá deshabilitado.

Nos gustaría habilitar el botón **Salida** cuando el registro de visita se haya localizado (no esté en blanco), el estado del registro esté activo y la visita ya haya comenzado, es decir, cuando el valor de inicio real no esté en blanco.

3. Seleccione el botón Check Out y haga clic en la propiedad **Modo de visualización** del botón en la pestaña Propiedades

4. Escriba la siguiente expresión en la barra de funciones:

     ```
     If(!IsBlank(Visit) 
     && Visit.Status = 'Status (Visits)'.Active
     && !IsBlank(Visit.'Actual Start'),
         DisplayMode.Edit,
         DisplayMode.Disabled
     )
     ```

5. Para conservar el trabajo en curso, haga clic en **Archivo** y luego en **Guardar**. Utilice la flecha hacia atrás para volver a la aplicación.

6. Presione **F5** para ejecutar la aplicación. 

7. Ambos botones deben estar deshabilitados. Introduzca el valor del código que copió anteriormente y presione **Pestaña** para alejar el foco del cuadro de texto. El botón **Entrada** debería estar habilitado. 

8. Desactive el contenido del cuadro de búsqueda.

9. Presione **ESC** para salir de la aplicación en ejecución.

## Tarea 5: Proceso completo de entrada y salida

Para realizar el proceso de entrada y salida, debemos actualizar los datos de la visita de Common Data Service de la siguiente manera:

* Cuando el visitante se registre, configure el campo *Inicio real* a la fecha y hora actuales
* Cuando el visitante salga, configure el campo *Fin real* a la fecha y hora actuales. 
* Después de la salida, configure el estado del registro como inactivo, lo que indica que la visita se ha completado.

1. Seleccione el botón **Entrada**.

2. Establezca la propiedad **OnSelect** de la pestaña Avanzado a la siguiente expresión.

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

   * **Patch(Visits, Visit, {'Actual Start': Now()});**. El método *Parche* actualiza la entidad **Visitas**, el registro identificado por la variable **Visitar** (que es la visita actual). La expresión establece el valor del campo *Inicio real* a la fecha y hora actuales (*Ahora()* método).
   * **Refresh([@Visits]);**. Esta expresión actualiza los registros de visitas a medida que cambian los valores subyacentes
   * **Set(Visit, LookUp(Visits, Code = textCode.Text));** Esta expresión actualiza la variable *Visita* con datos nuevos de Common Data Service.
   
   > Cuando un usuario haga clic en este botón, el inicio real de la visita se establecerá en la fecha y hora actuales y los datos se actualizarán.

3. Seleccione el botón **Salida**.

4. Establezca la propiedad **OnSelect** de la pestaña Avanzado a la siguiente expresión:

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

   Cuando un usuario haga clic en este botón, el final real se establecerá en la fecha y hora actuales, el estado del registro de visita se establecerá en inactivo y los datos se actualizarán.

5. Para conservar el trabajo en curso, haga clic en **Archivo** y luego en **Guardar**. Use la flecha **Atrás** para volver a la aplicación.

6. Presione **F5** o haga clic en el botón Reproducir para ejecutar la aplicación. Introduzca el valor del código que copió anteriormente y presione **Pestaña** para alejar el foco del cuadro de texto. El botón **Entrada** debería estar habilitado.

7. Presione el botón **Entrada**. Ocurrirá lo siguiente:

   * El **Inicio real** se establece en la fecha y hora actuales.
   
   * El botón **Entrada** está deshabilitado
   
   * El botón **Salida** está habilitado

8. Presione el botón **Salida**.

   * El **Final real** se establece en la fecha y hora actuales.
   
   * Ambos botones están deshabilitados

9. Desactive el contenido del cuadro de búsqueda.

10. Presione **ESC** para salir de la aplicación en ejecución.

## Tarea 6: Agregar indicadores visuales

La usabilidad de una aplicación móvil mejora significativamente cuando se proporcionan indicadores visuales. En esta tarea agregaremos un icono que indica si un visitante puede registrarse o no.

1. Seleccione la pestaña **Insertar**

2. Seleccione **Iconos \| Añadir**: En este punto, no importa qué icono seleccionemos, ya que queremos que el valor sea dinámico.

3. Cambie el tamaño del icono y colóquelo a la izquierda de los botones.

4. En la pestaña Avanzado del icono, seleccione la propiedad **Icono** (en la sección Diseño) y escriba la siguiente expresión

   ```
   If(
      CheckInButton.DisplayMode = DisplayMode.Disabled 
   && CheckOutButton.DisplayMode = DisplayMode.Disabled,
       Icon.EmojiFrown,
       Icon.EmojiSmile
   )
   ```

5. Para conservar el trabajo en curso, haga clic en **Archivo** y luego en **Guardar**. Use la flecha **Atrás** para volver a la aplicación.

6. Presione **F5** para ejecutar la aplicación. Introduzca el valor del código que copió anteriormente y presione **Pestaña** para alejar el foco del cuadro de texto. Compruebe que el icono muestre un emoji con el ceño fruncido.

7. Busque un valor de código diferente que no se haya utilizado antes (no debe tener un valor de inicio real o fin real). 

    > Puede ir a la pestaña anterior para copiar otro Código de una de las Visitas que creó. También puede ejecutar la aplicación creada previamente **Personal del campus** para crear nuevos registros de visitas. Compruebe que el icono muestre un emoji sonriente para este código.

Su aplicación en ejecución debería verse aproximadamente como la siguiente:

![Aplicación de seguridad de ejecución de lienzo](media/3-canvas-app-running.png)

8. Presione **ESC** para salir de la aplicación en ejecución.

## Tarea 7: Publique la aplicación

1. Aún debe tener la aplicación Seguridad del campus abierta en su explorador. Seleccione la aplicación **Seguridad del campus** y haga clic en **Editar**

2. Seleccione **Archivo \| Publicar** 

3. Seleccione **Publicar esta versión**.

# Desafíos

* Evitar la entrada manual del código de visita
* Agregue una validación de creación para la visita
* Agregue validación del tiempo real de la visita frente al tiempo programado de la visita (demasiado temprano, demasiado tarde, etc.)
* Agregue el estado detallado de la visita, por ejemplo, visualización de correo electrónico y validación para el visitante, razón para denegar el acceso al edificio, etc.
* Múltiples construcciones/reuniones/controles durante una sola visita al campus. Por ejemplo, alguien puede visitar el campus por un día y durante ese día se reunirán con miembros del personal en varios edificios a diferentes horas del día. ¿Consideraría traer la entidad *cita* a la solución?
