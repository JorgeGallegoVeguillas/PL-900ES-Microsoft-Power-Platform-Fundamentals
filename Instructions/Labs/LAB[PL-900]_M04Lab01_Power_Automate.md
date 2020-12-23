---
lab:
    title: 'Laboratorio 6: Cómo crear una solución automatizada'
    module: 'Módulo 4: Comenzar con Power Automate'
---

# Módulo 4: Comenzar con Power Automate
## Laboratorio: Cómo crear una solución automatizada

## Escenario

Bellows College es una institución educativa que tiene un campus con varios edificios. Los visitantes del campus están actualmente registrados en revistas en papel. La información no se recaba de manera uniforme y no hay forma de recopilar y analizar los datos sobre las visitas de todo el campus. 

La administración del campus querría modernizar el sistema de registro de visitantes de los edificios cuyo acceso esté controlado por el personal de seguridad y en los que los anfitriones deban anotar con antelación las visitas y dejar constancia de ellas.

A lo largo de este curso, creará aplicaciones y realizará la automatización para permitir que el personal de administración y seguridad de Bellows College administre y controle el acceso a los edificios en el campus. 

En este laboratorio, creará flujos de Power Automate para automatizar varias partes de la administración del campus. 

# Pasos de alto nivel del laboratorio

Se han identificado las siguientes condiciones como requisitos que debe implementar para completar el proyecto:

* El código único asignado a cada visitante debe estar disponible antes de su visita.
* El personal de seguridad necesita recibir notificaciones de los visitantes que se quedan durante más tiempo que sus intervalos de tiempo programados.

## Requisitos previos

* Finalización del **Módulo 0 Laboratorio 0: Validación del entorno de laboratorio**
* Finalización del **Módulo 2 Laboratorio 1: Introducción a Common Data Service**
* Aplicación Campus Staff creada en el **Módulo 3 Laboratorio 2: Cómo crear una aplicación de lienzo, parte 2** (para pruebas)
* Contacto de Diego Cabrera creado con una dirección de correo electrónico personal en el **Módulo 3 Laboratorio 4: Cómo crear una aplicación basada en modelo** (para pruebas)

## Cuestiones que tener en cuenta antes de comenzar

-   ¿Cuál es el mecanismo de distribución más apropiado para los códigos de visitante?
-   ¿Cómo se pueden medir las estancias prolongadas y aplicar directivas estrictas?

# Ejercicio 1: Crear flujo de notificación de visita

**Objetivo:** En este ejercicio, creará un flujo de Power Automate que implementa el requisito. El visitante debe recibir un correo electrónico que incluya el código único asignado a la visita.

## Tarea 1: Crear flujo

1.  Abra la solución de Administración del campus.

    -   Inicie sesión en <https://make.powerapps.com>

    -   Seleccione su **entorno.**

    -   Seleccione **Soluciones**.

    -   Haga clic para abrir la solución de **Administración del campus**.

2.  Haga clic en **Nuevo** y seleccione **Flujo**. Se abrirá el editor de flujo de Power Automate en una nueva ventana.

3. Busque *Actual* y seleccione el conector **Common Data Service (entorno actual)**.

4. Seleccione el desencadenador **Cuando se crea, actualiza o elimina un registro**.

   * Seleccione **Crear** para **desencadenar la condición**.
   
   * Seleccione **Visitas** para **el nombre de la entidad**.
   
   * Seleccione **Organización** para el **alcance**.
   
   * En la etapa de desencadenamiento, haga clic en los puntos suspensivos (**...**) y en **Cambiar nombre**. Cambie el nombre de este desencadenador a **"Cuando se crea una visita"**. Esta es una buena manera de que usted y otros editores de flujo puedan comprender el propósito de la etapa sin tener que profundizar en los detalles.

5.  Haga clic en **Nuevo paso**. Esta etapa es necesaria para recuperar la información de los visitantes, incluyendo la dirección de correo electrónico.

6. Busque *Actual* y seleccione el conector **Common Data Service (entorno actual)**.

7. Seleccione la acción **Obtener un registro**. 

   * Seleccione **Contactos** como **Nombre de la entidad**.
   
   * En el campo **Id. de elemento**, seleccione **Visitante (valor)** de la lista de contenido dinámico.
   
   * En esta acción, haga clic en los puntos suspensivos (**...**) y en **Cambiar nombre**. Cambie el nombre de esta acción a **"Obtener visitante"**. Esta es una buena manera de que usted y otros editores de flujo puedan comprender el propósito de la etapa sin tener que profundizar en los detalles.

8. Haga clic en **Nuevo paso**. Esta es la etapa que creará y enviará un correo electrónico al visitante.

9. Busque el *correo*, seleccione el conector **Correo** y la acción **Enviar una notificación por correo electrónico**. 

   * Si se le solicita que acepte los términos y condiciones para usar esta acción, haga clic en **Aceptar**.
   
   * Seleccione el campo **Para** y **Correo electrónico** en la lista de contenido dinámico. Observe que se encuentra debajo del encabezado **Obtener visitante**. Esto significa que está seleccionando el correo electrónico relacionado con el visitante que buscó en la etapa anterior. 

   * Escriba **Su visita programada a Bellows College** en el campo **Asunto**.

   * Escriba el siguiente texto en el **cuerpo del correo electrónico**:  
        
        > El contenido dinámico debe colocarse donde se nombran los campos entre paréntesis. Se recomienda copiar y pegar todo el texto primero y, luego, agregar contenido dinámico en los lugares correctos.
   
        ```
        Estimado/a, {First Name}:

        Actualmente tiene programada una visita a Bellows Campus desde las {Scheduled Start} hasta las {Scheduled End}.

        Su código de seguridad es {Code}. No lo comparta. Necesitará este código durante su visita.

        Saludos cordiales,

        La administración del campus
        Bellows College
        ```
   
10.  Seleccione el nombre del flujo **Sin título** en la parte superior y cámbiele el nombre a `Notificación de visita`.

11. Pulse **Guardar**.

    Deje esta pestaña de flujo abierta para la siguiente tarea. El flujo debería tener la siguiente apariencia:

![Flujo de notificación de visitante de Power Automate](media/4-power-automate-notify.png)

## Tarea 2: Valide y pruebe el flujo

1.  Abra una nueva pestaña en su explorador y vaya a <https://make.powerapps.com>.

2.  Haga clic en **Aplicaciones** y seleccione la aplicación **Personal del campus** que creó.

3.  Deje esta pestaña abierta y vuelva a la pestaña anterior con el flujo. 

4.  En la barra de comandos, haga clic en **Probar**. Seleccione **Yo realizaré la acción de desencadenamiento** y, luego, **Guardar y probar**.

5.  Deje abierta la pestaña de flujo y vuelva a la pestaña anterior con la aplicación **Personal del campus**.

6.  Presione **+** para añadir un nuevo registro de visita.

7.  Escriba **John Doe** como **Nombre** y elija cualquier **Edificio**.

8.  Elija a **John Doe** como el **Visitante**.

9.  Elija el **Inicio programado** y **Fechas de finalización programadas** para cualquier fecha en el futuro.

10.  Pulse el icono de **marca de verificación** para guardar la nueva visita.

11.  Vuelva a la pestaña anterior con el flujo que se está probando. Observe cómo se ejecuta el flujo. Si hay algún error, vuelva y compare el flujo con el ejemplo anterior. Si el correo electrónico se envía correctamente, lo recibirá en la bandeja de entrada. 

12.  Haga clic en la flecha hacia atrás de la barra de comandos.

13.  En la sección **Detalles**, observe que el **Estado** está **Habilitado**. Esto significa que el flujo se ejecutará siempre que se cree una nueva Visita, hasta que lo desactive. Cada vez que se ejecute el flujo, verá que se agrega a la lista **Historial de ejecución de 28 días**.

14.  Desactive el flujo haciendo clic en **Apagar** en la barra de comandos. Es posible que deba pulsar los puntos suspensivos (**...**) para ver esta opción.

15.  Cierre esta ventana.

# Ejercicio n.° 2: Cree un flujo de barrido de seguridad

**Objetivo:** En este ejercicio, creará un flujo de Power Automate que implementa el requisito. El barrido de seguridad se realiza cada 15 minutos y se notifica a seguridad si alguno de los visitantes ha sobrepasado la hora programada.

## Tarea 1: Cree un flujo para recuperar registros

1. Abra la solución de Administración del campus.

   -   Inicie sesión en <https://make.powerapps.com>

   -   Seleccione su **Entorno**.

   -   Seleccione **Soluciones**.

   -   Haga clic para abrir la solución de **Administración del campus**.

2. Haga clic en **Nuevo** y seleccione **Flujo**. Se abrirá el editor de flujo de Power Automate en una nueva ventana.

3. Busque *Periodicidad*, seleccione el conector **Programación** y luego, seleccione el desencadenante **Periodicidad**.

4. Establezca **Intervalo** en **15 minutos**

5. Haga clic en **Nuevo paso**. Busque *Actual* y seleccione el conector **Common Data Service (entorno actual)**. Seleccione la acción **Registros de lista**.

   * Introduzca **Visitas** como **Nombre de la entidad**
   
   * Haga clic en **Mostrar opciones avanzadas**.

   * Introduzca la siguiente expresión como **Consulta de filtro**

   ```
     statecode eq 0 and bc_actualstart ne null and bc_actualend eq null and Microsoft.Dynamics.CRM.OlderThanXMinutes(PropertyName='bc_scheduledend',PropertyValue=15)
   ```
   
   * Para desglosarlo:
       * **statecode eq 0** filtra las visitas activas (aquellas cuyo Estado es igual a Activo).
       * **bc_actualstart ne null** restringe la búsqueda a las visitas en las que Inicio real tenga un valor (es decir, se produjo un registro).
       * **bc_actualend eq null** restringe la búsqueda a las visitas en las que no hubo salida (Final real no tiene valor); 
       * **Microsoft.Dynamics.CRM.OlderThanXMinutes(PropertyName='bc_scheduledend',PropertyValue=15)** restringe las visitas que debieron completarse hace más de 15 minutos.

   * En esta acción, haga clic en los puntos suspensivos (**...**) y en **Cambiar nombre**. Cambie el nombre de esta acción a **“Enumerar las visitas activas que finalizaron hace más de 15 minutos”**. Esta es una buena manera de que usted y otros editores de flujo puedan comprender el propósito de la etapa sin tener que profundizar en los detalles.

6.  Haga clic en **Nuevo paso**. Busque *Aplicar*, Seleccione la acción **Aplicar a cada una** 

7.  Seleccione **valor** del contenido dinámico en el campo **Seleccionar una salida de las etapas anteriores**. Observe que está debajo del encabezado gris **Enumerar las visitas activas que finalizaron hace más de 15 minutos**. Esto significa que está seleccionando la lista de visitas que buscó en la etapa anterior. 

8.  Recuperar datos de Edificios para registro relacionado.

    * Haga clic en **Agregar una acción** dentro de Aplicar para cada bucle.
    
    * Busque *Actual* y seleccione el conector **Common Data Service (entorno actual)**. 
    
    * Seleccione la acción **Obtener un registro**.
    
    * Seleccione **Edificios** como **Nombre de la entidad**
    
    * Seleccione **Edificio (valor)** como **Id. de elemento** del contenido dinámico.
    
    * Haga clic en **...** junto a **Obtener un registro** y seleccione **Cambiar nombre**. Escriba **Obtener edificio** como nombre de la etapa.
    
9.  Recuperar datos de visitantes para registros relacionados.

    * Haga clic en **Agregar una acción** dentro de Aplicar para cada bucle.
    
    * Busque *Actual* y seleccione el conector **Common Data Service (entorno actual)**.
    
    * Seleccione la acción **Obtener un registro**.
    
    * Seleccione **Contactos** como **Nombre de la entidad**.
    
    * Seleccione **Visitante (valor)** como **Id. de elemento** del contenido dinámico.
    
    * Haga clic en **...** junto a **Obtener un registro** y seleccione **Cambiar nombre**. Escriba **Obtener visitante** como nombre de la etapa.
    
11.  Enviar una notificación por correo electrónico

     * Haga clic en **Agregar una acción** dentro de Aplicar para cada bucle. Añada la acción **Enviar una notificación por correo electrónico** de conexión de **Correo**.

12.  Introduzca su dirección de correo electrónico como **Para**

13.  Escriba lo siguiente en el campo **Asunto**. **Nombre completo** es un contenido dinámico del paso **Obtener visitante**.

   ```
   {Full Name} sobrepasó el tiempo de su visita.
   ```
   
14.  Escriba lo siguiente en el campo **Cuerpo**. **Nombre** es un contenido dinámico de la etapa **Obtener edificio**.

   ```
   Se sobrepasó el tiempo de visita en el edificio {Name}.
         
   Saludos.
         
   Seguridad del campus
   ```

17.  Seleccione el nombre de flujo **Sin título** en la esquina superior izquierda y cámbiele el nombre a **Barrido de seguridad**.

18.  Pulse **Guardar**.

    El flujo debería ser algo parecido a lo siguiente:

![Parte 1 del flujo programado del barrido de seguridad](media/4-power-automate-security-sweep.png)

## Tarea 2: Valide y pruebe el flujo

Su flujo comenzará a enviarle correos electrónicos (al correo electrónico que especificó al crear anteriormente el contacto de Diego Cabrera) si hay visitas que cumplan con los requisitos establecidos en el flujo.

1. Compruebe que los registros de visitas:

   1. Tengan estado activo
   
   2. Tengan un final programado pasado (más de 15 minutos).
   
   3. El Inicio real tenga un valor.
   
   > **Nota**: Para ver estos datos, vaya hasta make.powerapps.com en una nueva pestaña. Haga clic en Soluciones en el panel izquierdo para localizar la solución. Seleccione la entidad Visita y luego seleccione la pestaña Datos. Haga clic en Visitas activas en la esquina superior derecha para mostrar el selector de vista y, después, seleccione Todos los campos.
   
2. Navegue hasta su solución y localice el flujo **Barrido de seguridad**. Haga clic en [...] y en **Edición**.

3. Cuando se abra el flujo, haga clic en **Probar**.

4. Seleccione **Realizaré la acción desencadenante**.

5. Haga clic en **Probar** y **Ejecutar flujo**.

6. Cuando el flujo se complete, haga clic en **Listo**. 

7. Expanda **Aplicar a cada uno** y luego expanda la etapa **Enviar una notificación por correo electrónico**. Compruebe los valores **Tema**, **Cuerpo del correo electrónico**.

8. Desplácese hasta la solución, haga clic en [...] junto al flujo y seleccione **Apagar**. Esto es para evitar que el flujo se ejecute según una programación en el sistema de prueba.

# Desafíos

* Agregue el Inicio real y el Final programado al cuerpo del correo electrónico.
* ¿Cómo podría garantizar un formato de fecha fácil de usar en el cuerpo del correo electrónico?
* ¿Es posible generar una tabla con información del exceso del tiempo de permanencia y enviar solo un correo electrónico?
* ¿Se puede generar un código de barras para el código de visita? ¿Cuándo será útil?
