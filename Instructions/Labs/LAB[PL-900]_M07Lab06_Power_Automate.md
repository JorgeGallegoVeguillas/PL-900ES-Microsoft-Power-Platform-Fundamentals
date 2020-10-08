---
lab:
    title: 'Laboratorio: Power Automate'
    module: 'Módulo 4: Comenzar con Power Automate'
---

# Módulo 4: Comenzar con Power Automate
## Laboratorio: Power Automate

Escenario
========

Bellows College es una institución educativa que tiene un campus con varios edificios. Los visitantes del campus están actualmente registrados en revistas en papel. La información no se recaba de manera coherente y no se pueden recopilar y analizar los datos sobre las visitas de todo el campus. 

La administración del campus querría modernizar el sistema de registro de visitantes de los edificios cuyo acceso esté controlado por el personal de seguridad y en los que los anfitriones deban anotar con antelación las visitas y dejar constancia de ellas.

A lo largo de este curso, creará aplicaciones y realizará la automatización para permitir que el personal de administración y seguridad de Bellows College administre y controle el acceso a los edificios en el campus. 

En este laboratorio, creará flujos de Power Automate para automatizar varias partes de la administración del campus. 

Pasos de alto nivel del laboratorio
======================

A continuación, se indican los requisitos que se deben implementar para completar el proyecto:

* El código único asignado a cada visitante debe estar disponible antes de su visita.
* El personal de seguridad necesita recibir notificaciones de los visitantes que se quedan más allá de sus intervalos de tiempo programados.

## Requisitos previos

* Finalización del laboratorio 1: modelado de datos
* Aplicación Campus Staff creada en la Parte 1 del Laboratorio 2: Aplicación de lienzo (para pruebas)

Cuestiones que tener en cuenta antes de comenzar
-----------------------------------

-   ¿Cuál es el mecanismo de distribución más apropiado para los códigos de visitante?
-   Cómo se pueden medir las estadías prolongadas y pueden aplicar políticas estrictas.

Ejercicio n.° 1: Crear flujo de notificación de visita
===============================

**Objetivo:** En este ejercicio, creará un flujo de Power Automate que implementa el requisito. La notificación del visitante se realiza mediante correo electrónico. La notificación incluye el código único asignado a la visita.

Tarea n.° 1: Crear flujo
---------------------------

1.  Abra la solución de Administración del campus.

    -   Inicie sesión en <https://make.powerapps.com>

    -   Seleccione su **entorno.**

    -   Seleccione **Soluciones**.

    -   Haga clic para abrir la solución de **Administración del campus**.

2.  Haga clic en **Nuevo** y seleccione **Flujo**. Esto abrirá el editor de flujo en una nueva ventana.

3. Busque **Actual** y seleccione el conector **Common Data Service (entorno actual)**.

4. Seleccione el desencadenador **Cuando se crea**, **actualiza** o **elimina un registro**.

   * Seleccione **Crear** para **desencadenar la condición**.
   * Seleccione **Visitas** para **el nombre de la entidad**.
   * Seleccione **Organización** para el **alcance**.

5.  Haga clic en **Nuevo paso**. Este paso es necesario para recuperar la información de los visitantes, incluido el correo electrónico.

6. Busque **Actual** y seleccione el conector **Common Data Service (entorno actual)**.

7. Seleccione la acción **Obtener un registro**. 

   * Seleccione **Contactos** como **Nombre de entidad**.
   * En el campo **Id. de elemento**, seleccione **Visitante (Valor)** en la lista de contenido dinámico.

8. Haga clic en **Nuevo paso**. Al realizar este paso, se creará y enviará un correo electrónico al visitante.

9. Busque el *correo*, seleccione el conector **Correo** y la acción **Enviar una notificación por correo electrónico**. 
   * Si se le solicita que acepte los términos y condiciones para usar esta acción, haga clic en **Aceptar**.
   
   * Seleccione el campo **Para** y, luego, **Correo electrónico** en la lista de contenido dinámico.

   * Escriba **Su visita programada a Bellows College** en el campo **Asunto**.

   * Escriba el siguiente texto en el **cuerpo del correo electronico**:  
        *Nota: El contenido dinámico debe colocarse donde los campos se mencionan entre paréntesis. Se recomienda escribir todo el texto primero y luego agregar el contenido dinámico en el lugar correcto.*

   ```
    Hola, {Nombre}:

    Actualmente tiene programado visitar Bellows Campus desde {Inicio programado} hasta {Final programado}.

    Su código de seguridad es {Código}; no lo comparta. Se le pedirá que muestre este código durante su visita.


    Saludos cordiales,

    La administración del campus
    Bellows College
   ```
   
10.  Seleccione el nombre del flujo **Sin título** y cambie su nombre a **Notificación de visita**.

11.  Pulse **Guardar**.

Tarea \#2: Valide y pruebe el flujo
--------------------------------

1.  Abra la aplicación **Personal del campus** que creó 
2.  Presione + para añadir un nuevo registro de visita
3.  Ingrese la información requerida, presione **Guardar**
4.  Abra el flujo, ubique y abra el más reciente **Ejecutar**
5.  Abra el paso **Correo** y verifique que el contenido del correo electrónico se haya generado correctamente.

# Ejercicio n.° 2: Cree un flujo de barrido de seguridad

**Objetivo:** En este ejercicio, creará un flujo de Power Automate que implementa el requisito. El barrido de seguridad se realiza cada 15 minutos y se notifica a la seguridad si alguno de los visitantes se ha pasado de la hora programada.

## Tarea 1: Cree un flujo para recuperar registros

1. Abra la solución de Administración del campus.

   -   Inicie sesión en <https://make.powerapps.com>

   -   Seleccione su **entorno.**

   -   Seleccione **Soluciones**.

   -   Haga clic para abrir la solución de **Administración del campus**.

2. Haga clic en **Nuevo** y seleccione **Flujo**. Esto abrirá el editor de flujo en una nueva ventana.

3. Busque si hay *repeticiones*, seleccione el conector **Programación** y, luego, seleccione el desencadenador **Periodicidad**.

4. Establezca **Intervalo** en **15 minutos**

5. Haga clic en **Nuevo paso**. Busque **Actual** y seleccione el conector **Common Data Service (entorno actual)**. Seleccione la acción **Registros de lista**.

   * Introduzca **Visitas** como **Nombre de la entidad**
   
   * Haga clic en **Mostrar opciones avanzadas**.

   * Introduzca la siguiente expresión como **Consulta de filtro**

     ```
     statecode eq 0 and bc_actualstart ne null and bc_actualend eq null and Microsoft.Dynamics.CRM.OlderThanXMinutes(PropertyName='bc_scheduledend',PropertyValue=15)
     ```

   Para desglosarlo

   * `statecode eq 0` filtra las visitas activas (donde el estado es igual a activo)
   * `bc_actualstart ne null` restringe la búsqueda a las visitas donde el Inicio real tiene un valor, es decir, hubo un registro
   * `bc_actualend eq null` restringe la búsqueda a las visitas donde no se realizó pago (el final real no tiene valor) 
   * `Microsoft.Dynamics.CRM.OlderThanXMinutes (PropertyName = 'bc_scheduledend', PropertyValue = 15)` restringe las visitas donde debían completarse hace más de 15 minutos.  

6.  Haga clic en **Nuevo paso**. Busque **Aplicar**, Seleccione la acción **Aplicar a cada una** 

7.  Seleccione **valor** del contenido dinámico en el campo **Seleccionar una salida de los pasos anteriores**.

8.  Recupere los datos de edificio para el registro relacionado:

    * Haga clic en **Agregar una acción** dentro del bucle.
    * Busque **Actual** y seleccione el conector **Common Data Service (entorno actual)**. 
    * Seleccione la acción **Obtener un registro**.
    * Haga clic en ... junto a **Obtener un registro** y seleccione **Cambiar nombre**. Introduzca **GetBuilding** como nombre del paso
    * Seleccione **Edificios** como **Nombre de la entidad**
    * Seleccione **Edificio (Valor)** como **Id. de elemento** en el contenido dinámico.

9.  Recupere los datos de visitante para el registro relacionado.

    * Haga clic en **Agregar una acción** dentro del bucle.
    * Busque **Actual** y seleccione el conector **Common Data Service (entorno actual)**. 
    * Seleccione la acción **Obtener un registro**.
    * Haga clic en ... junto a **Obtener un registro** y seleccione **Cambiar nombre**. Escriba **GetVisitor** como nombre del paso.
    * Seleccione **Visitas** como **Nombre de entidad**.
    * Seleccione **Visitante (valor)** como **Id. de elemento** en el contenido dinámico.
    
10.  Recupere los datos de propietario para el registro relacionado.
    * Haga clic en **Agregar una acción** dentro del bucle.
    * Busque **Actual** y seleccione el conector **Common Data Service (entorno actual)**. 
    * Seleccione la acción **Obtener un registro**.
    * Haga clic en ... junto a **Obtener un registro** y seleccione **Cambiar nombre**. Escriba **GetUser** como nombre del paso.
    * Seleccione **Visitas** como **Nombre de entidad**.
    * Seleccione **Propietario (Valor)** como **Id. de elemento** en el contenido dinámico.

11.  Agregue la acción **Enviar una notificación por correo electrónico** desde la conexión **Correo** mientras permanece en el bucle **Aplicar a cada uno**.

12.  Introduzca su dirección de correo electrónico como **Para**

13.  Escriba “El contacto {**Vistante (Valor)**} sobrepasó su tiempo de visita” en el campo **Asunto**. **Visitante (Valor)** es un contenido dinámico del paso **GetVisitor**.

14.  Escriba “Ocurrió en el edificio {**Nombre**}” en el campo **Cuerpo**. **Nombre** es un contenido dinámico del paso **GetBuilding**.

15.  Haga clic en **Mostrar opciones avanzadas**.

16.  Localice **Correo electrónico principal** desde el paso **GetUser** e insértelo en el campo CC (el anfitrión de la reunión recibirá una copia del correo electrónico)

17.  Seleccione el nombre de flujo **Sin título** en la esquina superior izquierda y cambie el nombre a **Barrido de seguridad**.

16.  Pulse **Guardar**.

## Tarea n.°2: Valide y pruebe el flujo

1. Busque o cree registros de visitas que:
   1. Tengan estado activo
   2. Han sobrepasado su Final programado (15 minutos como mínimo)
   3. El Inicio real tenga un valor.
2. Navegue hasta la solución y busque el flujo **Barrido de seguridad**. Haga clic en ... y en **Editar**.
3. Cuando se abra el flujo, haga clic en **Prueba**.
4. Seleccione **Yo realizaré la acción de desencadenamiento**.
5. Haga clic **Prueba** y en **Ejecutar flujo**.
6. Cuando el flujo se haya completado, haga clic en **Listo**. 
7. Expanda **Aplicar a cada uno** y, luego, los pasos **Enviar una notificación por correo electrónico**. Compruebe los valores **Tema**, **Cuerpo del correo electrónico**. Expanda **Mostrar más** y verifique el valor **CC**.
8. Navegue hasta la solución, haga clic en ... junto al flujo y seleccione **Apagar**. Esto es para evitar que el flujo se ejecute según una programación en el sistema de prueba.

# Desafíos

* Agregue información del edificio y un mapa al flujo de notificaciones.
* ¿Se puede generar un código de barras para el código de visita? ¿Cuándo será útil?
* ¿Cómo garantizar un formato de fecha fácil de usar en el cuerpo del correo electrónico?
* ¿Es posible generar una tabla con información de estadía excesiva y enviar solo un correo electrónico?
