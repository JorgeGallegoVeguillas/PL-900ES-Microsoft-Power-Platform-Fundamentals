---
lab:
    title: 'Laboratorio 04: Power BI'
    module: 'Módulo XX: Compilación en Power Apps'
---

# PL-900: Fundamentos de Microsoft Power Platform
## Módulo X, laboratorio 4: Power BI

Escenario
========

Bellows College es una institución educativa que tiene un campus con varios edificios. Los visitantes del campus están actualmente registrados en revistas en papel. La información no se recaba de manera uniforme y no hay forma de recopilar y analizar los datos sobre las visitas de todo el campus. 

La administración del campus querría modernizar el sistema de registro de visitantes de los edificios cuyo acceso esté controlado por el personal de seguridad y en los que los anfitriones deban anotar con antelación las visitas y dejar constancia de ellas.

A lo largo de este curso, creará aplicaciones y recurrirá a la automatización para que el personal de administración y seguridad de Bellows College administre y controle el acceso a los edificios del campus. 

En este laboratorio, creará un panel de control de Power BI que visualiza datos sobre las visitas al campus.

Pasos de alto nivel del laboratorio
======================

Seguiremos los pasos a continuación para diseñar y crear el panel de control de Power BI:

-   Conéctese al Common Data Service 
-   Transforme los datos para incluir descripciones fáciles de usar para los registros relacionados (búsquedas)
-    Cree y publique un informe con varias visualizaciones de la información de las visitas al campus.
-    Consulta de lenguaje natural del usuario para crear visualizaciones adicionales
-    Cree una vista móvil


## Requisitos previos

* Finalización del laboratorio 1: modelado de datos

Cuestiones que tener en cuenta antes de comenzar
-----------------------------------

-   ¿Quién es la audiencia objetivo del informe?
-   ¿Cómo consumirá el informe la audiencia? ¿Dispositivo típico? ¿Ubicación?
-   ¿Tiene suficientes datos para visualizar?
-   ¿Cuáles son las características posibles que puede usar para analizar datos sobre las visitas?

Ejercicio 1: Cree informes de Power BI 
===============================

**Objetivo:** En este ejercicio, creará un informe de Power BI basado en datos de la base de datos de Common Data Service.

Tarea 1: Preparación de datos
---------------------------

1.  Encuentre la URL de su organización

    * Vaya al Centro de administración de Power Platform en https://aka.ms/ppac.
    * En el panel de navegación izquierdo, seleccione Entornos y luego seleccione el entorno de destino.
    * Haga clic con el botón derecho del mouse en la **URL de entorno** del panel **Detalles**, luego seleccione **Copiar vínculo**.
2. Si no tiene instalado Power BI Desktop, vaya a https://aka.ms/pbidesktopstore para descargar e instalar la aplicación Power BI.

3. Abra Power BI Desktop, inicie sesión si se le solicita.

4. Seleccione **Obtener datos**.

5. Seleccione **Power Platform**, luego seleccione **Common Data Service**y presione **Conectar**.

6. Pegue la URL del entorno que copió anteriormente, presione **Aceptar**.

7. Expanda el nodo **Entidades**, seleccione las entidades **bc_Building** y **bc_Visit**, haga clic en **Cargar**.

8. Haga clic en el icono **Modelo** de la barra de herramientas vertical izquierda.

9. Arrastre la columna **bc_buildingid** desde la tabla **bc_Building** y suéltela en la columna **bc_building** de la tabla **bc_Visit**. Eso creará una relación entre dos entidades que Power BI podrá usar para mostrar datos relacionados.

10. Seleccione el icono **Informe** en la barra de herramientas izquierda.

11. Expanda el nodo **bc_Visits** del panel **Campos**.

12. Haga clic en ... y seleccione **Nueva columna**.

13. Complete la fórmula del siguiente modo

    ```
    Column = RELATED(bc_Building[bc_name])
    ```

    y pulse ENTRAR. Eso agregará un nuevo campo con el nombre del edificio en los datos de las visitas.

14. Haga clic en ... al lado del campo y seleccione **Renombrar**. Escriba **Edificio** como nombre del campo.

15. Haga clic en ... al lado del campo **bc_visitid** y seleccione **Renombrar**. Escriba **Visitas** como nombre del campo.

16. Haga clic... al lado del campo **bc_scheduledstart** y seleccione **Renombrar**. Escriba **Inicio** como nombre del campo.

17. Para guardar el trabajo en curso, presione **Archivo | Guardar ** e introduzca un nombre de archivo de su elección.

## Tarea n.°2: Cree gráficos y visualizaciones de tiempo

1. Presione el icono de gráfico circular en el panel **Visualizaciones** para insertar el gráfico.
2. Arrastre el campo **Edificio** y colóquelo en el cuadro de destino **Leyenda**.
3. Arrastre el campo **Visitas** y colóquelo en el cuadro de destino **Valores**.
4. Cambie el tamaño del gráfico circular utilizando los tiradores de las esquinas para que todos los componentes del gráfico sean visibles.
5. Haga clic en **Nueva visualización** en la cinta de Power BI, luego seleccione el gráfico de columnas apiladas en el panel de **Visualizaciones**. 
6. Arrastre el campo **Visitas** y colóquelo en el cuadro de destino **Valores**.
7. Arrastre el campo **Comienzo** y colóquelo en el cuadro de destino **Eje**.
8. Haga clic en **X** junto a **Día** y **Trimestre** para dejar solo los totales de **Año** y **Mes**.
9. Cambie el tamaño del gráfico, según sea necesario, con los controladores de las esquinas.
10. Pruebe la interactividad del informe:
    * Seleccione varios sectores de creación en el gráfico circular y observe los cambios en el informe de tiempos.
    * Seleccione varias barras en el gráfico de columnas de tiempo y observe los cambios en el informe circular.
    * Explore en profundidad el nivel del mes con los iconos o el comando de la cinta de opciones **Datos/Explorar en profundidad | Expandir al siguiente nivel**.
11. Guarde el trabajo en curso presionando **Archivo | Guardar**.

Ejercicio 2: Crear panel de control de Power BI
================================

## Tarea 1: Publicar informe de Power BI

1. Presione el botón **Publicar** en la cinta.

2. Seleccione **Mi espacio de trabajo** como destino, luego presione **Seleccionar**.

3. Espere hasta que se complete la publicación y haga clic en **Abrir\<nombre de su informe\>.pbix en Power BI**.

## Tarea n.°2: Crear panel de control de Power BI

1. Expanda **Mi espacio de trabajo**.
2. Seleccione el informe debajo de los títulos **Informes**.
3. Seleccione **Anclar una página en vivo** en el menú. Según el diseño, es posible que deba presionar ... para mostrar elementos adicionales del menú.
4. Seleccione **Nuevo tablero** en la confirmación de **Anclar al tablero**.
5. Introduzca **Administración del campus** como un **Nombre del tablero**, presione **Anclar elemento en vivo**.
6. Seleccione el nodo **Mi espacio de trabajo**, seleccione el panel **Administración del campus**.
7. Pruebe la interactividad de los gráficos circulares y de barras que se muestran.

## Tarea n.° 3: Agregue visualizaciones usando lenguaje natural

1. Seleccione **Hacer una pregunta sobre sus datos** en la parte superior del tablero
2. Introduzca **edificios por número de visitas** en el área de preguntas y respuestas. Se mostrará el gráfico de barras.
3. Seleccione **Anclar visualización**.
4. Seleccione **Tablero de instrumentos existente**, seleccione el panel de **Administración del campus**, presione **Anclar**.
5. Pruebe el comportamiento haciendo clic en el gráfico para obtener detalles de las Preguntas y respuestas.

## Tarea n.° 4: Crear vista de teléfono móvil

1. Seleccione el informe de la zona de **Informes**.
2. Dependiendo de la versión de la interfaz de usuario, seleccione ... | Vista para dispositivos móviles o **Vista web | Vista de teléfono**.
3. Reorganice los iconos como desee.
4. Seleccione... | Generar código QR.
5. Si tiene un dispositivo móvil, escanee el código utilizando una aplicación de escáner QR disponible en plataformas iOS y Android.
6. Navegue y explore los informes en un dispositivo móvil.

# Desafíos

* Paneles de control e informes para incluir planos del edificio y el campus
* Informe y analice patrones y tendencias de visitas
* Visualización sobrepasada
* Streaming de Power BI para un procesamiento casi en tiempo real para un campus grande 