---
lab:
    title: 'Laboratorio: Power Automate'
    module: 'Módulo 4: Comenzar con Power Automate'
---

# Módulo 4: Comenzar con Power Automate
## Laboratorio: Power Automate

Escenario
========

Bellows College es una institución educativa que tiene un campus con varios edificios. Los visitantes del campus están actualmente registrados en revistas en papel. La información no se recaba de manera uniforme y no hay forma de recopilar y analizar los datos sobre las visitas de todo el campus. 

La administración del campus querría modernizar el sistema de registro de visitantes de los edificios cuyo acceso esté controlado por el personal de seguridad y en los que los anfitriones deban anotar con antelación las visitas y dejar constancia de ellas.

A lo largo de este curso, creará aplicaciones y realizará la automatización para permitir que el personal de administración y seguridad de Bellows College administre y controle el acceso a los edificios en el campus. 

En este laboratorio, creará flujos de Power Automate para automatizar varias partes de la administración del campus. 

Pasos de alto nivel del laboratorio
======================

Los siguientes se han identificado como requisitos que debe implementar para completar el proyecto.

* El código único asignado a cada visitante debe estar disponible antes de su visita.
* El personal de seguridad necesita recibir notificaciones de los visitantes que se quedan más allá de sus intervalos de tiempo programados.

## Requisitos previos

* Finalización del laboratorio 1: modelado de datos
* Aplicación Campus Staff creada en la Parte 1 del Laboratorio 2: Aplicación de lienzo (para pruebas)

Cuestiones que tener en cuenta antes de comenzar
-----------------------------------

-   ¿Cuál es el mecanismo de distribución más apropiado para los códigos de visitante?
-   Cómo se pueden medir las estadías prolongadas y pueden aplicar políticas estrictas.

Ejercicio 1: Crear flujo de notificación de visita
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

7. Seleccione la acción **Obtener registro**. 

   * Seleccione **Contactos** como **Nombre de la entidad**
   * Buscar contenido dinámico, seleccionar **Visitante (valor)** como un valor para **Identificación del elemento**.

8. Haga clic en **Nuevo paso**. Este es el paso que crea y envía un correo electrónico al visitante.

9. Busque el *correo*, seleccione el conector **Correo** y la acción **Enviar una notificación por correo electrónico**. 

   * Seleccione **Correo electrónico** como valor **Para**.

   * Ingrese **Su visita programada a Bellows College** como **Tema**.

   * Ingrese el siguiente texto en el **cuerpo del correo electrónico**:  
        *Nota: El texto en negrita indica contenido dinámico que debe insertarse en estos lugares. Se recomienda escribir todo el texto primero y luego agregar contenido dinámico en el lugar correcto.*
     >
     > Estimado {**Nombre**},
     >
     > Actualmente tiene programado visitar Bellows Campus desde {**Inicio programado**} hasta {**Fin programado**}.
     >
     > Su código de seguridad es {**Código**}, no lo comparta. Se le pedirá que reproduzca este código durante su visita.
     >
     >
     > Saludos cordiales.
     >
     > La administración del campus
     >
     > Bellows College
     
   
10.  Seleccione el nombre del flujo y cambie su nombre a **Notificación de visita**

11.  Presione **Guardar**.

Tarea n.°2: Valide y pruebe el flujo
--------------------------------

1.  Abra la aplicación **Personal del campus** que creó 
2.  Presione + para añadir un nuevo registro de visita
3.  Ingrese la información requerida, presione **Guardar**
4.  Abra el flujo, ubique y abra el más reciente **Ejecutar**
5.  Abra el paso **Correo** y verifique que el contenido del correo electrónico se haya generado correctamente.

# Ejercicio 2: Cree un flujo de barrido de seguridad

**Objetivo:** En este ejercicio, creará un flujo de Power Automate que implementa el requisito. El barrido de seguridad se realiza cada 15 minutos y se notifica a la seguridad si alguno de los visitantes se ha pasado de la hora programada.

## Tarea n.° 1: Cree un flujo para recuperar registros

1. Abra la solución de Administración del campus.

   -   Inicie sesión en <https://make.powerapps.com>

   -   Seleccione su **entorno.**

   -   Seleccione **Soluciones**.

   -   Haga clic para abrir la solución de **Administración del campus**.

2. Haga clic en **Nuevo** y seleccione **Flujo**. Esto abrirá el editor de flujo en una nueva ventana.

3. Busque si hay *periodicidad*, seleccione el conector **Programación**, desencadene **Periodicidad**.

4. Establezca **Intervalo** en **15 minutos**

5. Haga clic en **Nuevo paso**. Busque **Actual** y seleccione el conector **Common Data Service (entorno actual)**. Seleccione la acción **Registros de lista**.

   * Introduzca **Visitas** como **Nombre de la entidad**

   * Introduzca la siguiente expresión como **Consulta de filtro**

     ```
     statecode eq 0 and bc_actualstart ne null and bc_actualend eq null and Microsoft.Dynamics.CRM.OlderThanXMinutes(PropertyName='bc_scheduledend',PropertyValue=15)
     ```

   Para desglosarlo

   * `statecode eq 0` filtra las visitas activas (donde el estado es igual a activo)
   * `bc_actualstart ne null` restringe la búsqueda a las visitas donde el Inicio real tiene un valor, es decir, hubo un registro
   *  `bc_actualend eq null` restringe la búsqueda a las visitas donde no se realizó pago (el final real no tiene valor) 
   * `Microsoft.Dynamics.CRM.OlderThanXMinutes (PropertyName = 'bc_scheduledend', PropertyValue = 15)` restringe las visitas donde debían completarse hace más de 15 minutos.  

6.  Haga clic en **Nuevo paso**. Busque **Aplicar**, Seleccione la acción **Aplicar a cada una** 

7.  Seleccione **valor** del contenido dinámico como **Seleccionar una salida de los pasos anteriores.**.

8.  Agregar recuperación de datos para los registros relacionados

    * Haga clic en **Agregar una acción** dentro del bucle.
    * Busque **Actual** y seleccione el conector **Common Data Service (entorno actual)**. 
    * Seleccione la acción **Obtener registro**.
    * Haga clic en ..., seleccione **Renombrar**. Introduzca **GetBuilding** como nombre del paso
    * Seleccione **Edificios** como **Nombre de la entidad**
    * Seleccione **Edificio (valor)** como **Identificación del producto**

9.  Repita la secuencia de recuperación de datos anterior para **Visitante** y **Usuario**, seleccionando el nombre de la entidad relacionada y usando **Visitante (valor)** y **Propietario (valor) **como **Identificación del producto**, respectivamente

10.  Agregue la acción **Enviar una notificación por correo electrónico** desde conexión de **Correo electrónico**, permaneciendo en **Aplicar a cada bucle**

11.  Introduzca su dirección de correo electrónico como **Para**

12.  Ingrese "El contacto {**Nombre completo**} prolongó demasiado su visita". **Nombre completo** es un contenido dinámico del registro de visitas actual.

13.  Escriba "Sucedió en el edificio **Nombre **", donde **Nombre** es contenido dinámico del paso **GetBuilding**

14.  Localice **Correo electrónico principal** desde el paso **GetUser** e insértelo en el campo CC (el anfitrión de la reunión recibirá una copia del correo electrónico)

15.  Seleccione el nombre de flujo **Sin título** en la esquina superior izquierda y cámbiele el nombre a **Barrido de seguridad**

16.  Presione **Guardar**.

## Tarea n.° 2: Valide y pruebe el flujo

1. Localice o cree registros de visitas que 
   1. Tengan estado activo
   2.  El final programado esté en el pasado (por más de 15 minutos)
   3. El Inicio real tenga un valor.
2. Abra el flujo creado en la tarea 1 y presione **Probar**
3. Seleccione **Yo realizaré la acción de desencadenamiento**
4. Seleccione **Ejecutar flujo**
5. Cuando el flujo compite, expanda **Aplicar a cada uno**, luego expanda los pasos **Enviar una notificación por correo electrónico**
6. Compruebe los valores **Tema**, **Cuerpo del correo electrónico**. Expanda **Mostrar más** y verifique el valor **CC**.
8. Desplácese hasta la solución, haga clic en ... junto al flujo y seleccione **Apagar**. Esto es para evitar que el flujo se ejecute según una programación en el sistema de prueba.

# Desafíos

* Agregue información del edificio y un mapa al flujo de notificaciones.
* ¿Se puede generar un código de barras para el código de visita? ¿Cuándo será útil?
* ¿Cómo garantizar un formato de fecha fácil de usar en el cuerpo del correo electrónico?
* ¿Es posible generar una tabla con información de estadía excesiva y enviar solo un correo electrónico?
