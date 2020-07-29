---
lab:
    title: 'Guía del instructor'
    module: 'Módulo XX: Compilación en Power Apps'
---

# PL-900: Fundamentos de Microsoft Power Platform
## Guía de instructor

# Entornos

Los alumnos necesitarán un entorno de Common Data Service (CDS) cada uno para completar el trabajo del curso. Los alumnos pueden aprovisionar los entornos durante la clase o estos se pueden aprovisionar antes de la entrega con las credenciales facilitadas a los alumnos antes del primer ejercicio.

Los entornos no necesitan consideraciones de configuración específicas, un CDS simple *sin ningún dato de muestra* es todo lo que se necesita.

Recomendamos completar los laboratorios como alumnos antes de ofrecer el entrenamiento. 

* La familiaridad con los ejercicios hará que la enseñanza sea más eficiente.
* Los componentes de la solución creados durante este ejercicio se pueden usar según sea necesario para sus demostraciones. No se requieren demostraciones, pero algunos las encuentran útiles. Haga algunas sobre los temas con los que se sienta más cómodo.

# Información general

Bellows College es una institución educativa que tiene un campus con varios edificios. Actualmente se guarda un registro físico de las visitas al campus. La información no se recaba de manera uniforme y no hay forma de recopilar y analizar los datos sobre las visitas de todo el campus. 

La administración del campus querría modernizar el sistema de registro de visitantes de los edificios cuyo acceso esté controlado por el personal de seguridad y en los que los anfitriones deban anotar con antelación las visitas y dejar constancia de ellas.

A lo largo de este curso, creará aplicaciones y recurrirá a la automatización para que el personal de administración y seguridad de Bellows College administre y controle el acceso a los edificios del campus. 

Algunos alumnos pueden sentir que es excesivo realizar todas las personalizaciones dentro del marco de la solución. Sin embargo, es vital desarrollar buenos hábitos para llevarlos después del curso.

> [IMPORTANTE]
> Estamos construyendo componentes típicos para las soluciones de Power Platform. Las dependencias son mínimas pero el **Laboratorio 1** es esencial, ya que el resto de los ejercicios usan el modelo de datos construido durante esta práctica de laboratorio. Los datos de muestra importados durante el laboratorio hacen que compilar y probar las aplicaciones sea más fácil, realista y fácil de relacionar.

Además del modelo de datos común creado en el Laboratorio 1, no hay dependencias entre diferentes laboratorios. Los entrenadores deben explicar claramente el objetivo de cada laboratorio y detallar los componentes y las técnicas de soluciones de alto nivel. Luego, se debe alentar a los alumnos a diseñar y construir sus propias soluciones sin seguir instrucciones paso a paso para cada ejercicio.

## Componentes

Hay componentes completos disponibles para *todos* los ejercicios. Incluyen aplicaciones de lienzo, aplicaciones basadas en modelos, flujos de Power Automate archivo pbix Power BI, datos de muestra y mapa de importación de datos y la solución completa exportada como administrada y no administrada. Los componentes no deben usarse como acceso directo para completar el ejercicio. En cambio, son útiles como herramienta de demostración y como punto de referencia general.

Debido a que todos los laboratorios del curso dependen del modelo de datos, el modelo está disponible como una solución independiente [CampusDataModel_1_0_0_1.zip](..\Allfiles\CampusDataModel_1_0_0_1.zip). Se puede importar a un entorno nuevo seguido del Ejercicio 3 en el Laboratorio 1 (importación de datos). Eso creará un punto de partida para los alumnos que no pudieron completar el laboratorio. El modelo de datos predefinidos les brinda a estos alumnos la oportunidad de ponerse al día y continuar con el resto de los ejercicios. 

## Desafíos

Se proporcionan una serie de desafíos al final de cada laboratorio. Los desafíos generalmente incluyen escenarios más realistas porque los ejercicios del curso se simplifican por cuestiones de tiempo. Los desafíos también cubren temas más avanzados que algunos alumnos pueden encontrar útiles.

Use los desafíos para iniciar una discusión sobre escenarios del mundo real y cómo se pueden aplicar las técnicas aprendidas durante los ejercicios para resolver los desafíos.

Laboratorios
======================

## Laboratorio 1: Modelo de datos

Un modelo de datos sólido es la base de las aplicaciones creadas en la plataforma. En este laboratorio, estableceremos un entorno y crearemos soluciones para hacer un seguimiento de los cambios. También crearemos un modelo de datos para admitir los requisitos e importar datos de muestra.

Temas para discutir:

* ¿Qué herramientas usaría?
* ¿Cómo aborda el modelado?
* ¿Por dónde empieza?
* Relaciones 
* Prácticas recomendadas para implementar el modelo de datos en CDS
* Traer entidades de Common Data Model (por ejemplo, contactos): qué incluir.
* Conjuntos de datos de muestra de desarrollo/prueba: cuánto es suficiente. Prácticas recomendadas en torno a la creación de conjuntos de datos de desarrollo/prueba.

### Desafíos

* ¿Consideraría usar la actividad de *cita* como parte de la solución? ¿Qué cambiaría?

  > El nombramiento o cualquier otra entidad de actividad requieren una comprensión más avanzada de conceptos como grupos de actividad, campo relacionado, etc. Es posible que algunas de las herramientas del fabricante aún no sean capaces de trabajar con estas y es posible que se requieran soluciones complejas.

* ¿Cómo hacer cumplir el final programado después del inicio programado? 

  > Un buen tema para discutir las reglas de negocios. 

* Agregue soporte técnico para múltiples reuniones durante una sola visita.

  > Relaciones de varios a varios y desafíos asociados

* Asegure el acceso al edificio no solo para los contactos externos, sino también para el personal interno.

  >  Una buena introducción al acceso a datos internos en comparación con los externos, usuarios en comparación con contactos, autenticado en comparación con anónimo. Posiblemente mencione el enfoque de Power Apps Portals de tratar a los usuarios como contactos también con el propósito

* Las visitas a ciertos edificios requieren la aprobación de la gerencia. ¿Qué cambiaría el proceso de aprobación en el modelo de datos?

  > Discusión de los flujos de procesos comerciales y aprobaciones de Power Automate como técnicas para introducir el factor humano en los procesos.

## Laboratorio 2: Aplicación de lienzo

Este laboratorio consta de dos partes dirigidas a diferentes usuarios.

En la parte 1 de este laboratorio, creará una aplicación de lienzo de Power Apps que el personal de la universidad podrá usar para administrar las visitas de sus invitados.

En la parte 2 de este laboratorio, creará una aplicación de lienzo de Power Apps que el personal de seguridad usará en las entradas del edificio para validar y registrar rápidamente a los visitantes.

Temas para discutir

- Factor de formulario para tableta en comparación con teléfono. Diseños dinámicos (disponibles próximamente en lienzo).
- ¿Cómo afecta el público objetivo al diseño de la aplicación?
- Cómo el conocimiento de Excel puede beneficiar a los creadores de aplicaciones (programación procesal tradicional en comparación con propiedades y sintaxis de expresión de Power Apps)

- Qué conector debo usar. Cómo el conector CDS ahora es interno para el lienzo Power Apps.

- Comprobador de aplicaciones: nuevas métricas todos los días. Asegúrese de volver a probar la aplicación.

- Accesibilidad: lo que hace que una buena aplicación sea accesible

### Desafíos

**Parte 1**

* Vista del calendario de todas las visitas y filtrado por intervalo de fechas

  > Componentes, discusión de controles de terceros, filtrado de datos efectivo

* Capacidad para crear y administrar contactos como parte de la aplicación

  > Múltiples pantallas, navegación entre ellas

* Cómo mostrar varias reuniones durante una sola visita

  > Cómo navegar por relaciones y propiedades

**Parte 2**

* ¿Cómo evitar la entrada manual del código de visita?

  > Utilice las capacidades de escaneo del dispositivo móvil si el visitante puede mostrar un código de barras con el código. Buena discusión sobre cómo y cuándo generar códigos de barras para los visitantes.

* Agregue una validación de creación para la visita

  > Agregue información de creación al código de barras. Potencialmente use las capacidades de GPS. 

* Agregue validación del tiempo real de la visita frente al tiempo programado de la visita (demasiado temprano, demasiado tarde, etc.)

  > Manipulación de fecha/hora en fórmulas, lógica más compleja.

* Agregue el estado detallado de la visita, por ejemplo, visualización de correo electrónico y validación para el visitante, razón para denegar el acceso al edificio, etc.

  > Acceso a las propiedades de entidades relacionadas, creando una interfaz de usuario atractiva

* ¿Cómo manejaría el requisito de múltiples edificios/reuniones/chequeos durante la única visita al campus? Por ejemplo, alguien puede visitar el campus por un día y durante ese día se reunirán con miembros del personal en varios edificios a diferentes horas del día. ¿Qué pasa con una sola reunión con múltiples participantes externos? ¿Consideraría traer la entidad *cita* a la solución? 

  > Este es un tema bueno pero potencialmente complejo y largo para discutir. Considere iniciar una discusión y dar a los alumnos alguna forma de "tarea para casa". Debata cómo Power Apps permite un enfoque iterativo para crear aplicaciones, es decir, empiece de forma sencilla y mejore sobre la marcha.

## Laboratorio 3: Power Automate

En este laboratorio, creará flujos de Power Automate para automatizar varias partes de la administración del campus. Este laboratorio requiere, además del Laboratorio 1, una aplicación integrada en la parte 1 del Laboratorio 2. Esto es necesario para que se puedan realizar pruebas de automatización (desencadenar procesos al introducir nuevos datos)

Temas para discutir

* Flujos en soluciones
* Conectores CDS (entorno estándar frente al actual)
* Otros medios de automatización en Power Platform (flujo de trabajo en tiempo real, automatización de la interfaz de usuario...)
* Interacción humana con flujos: procesos de aprobación
* Probar los procesos durante la compilación
* Compartir los flujos
* Supervisar el proceso en ejecución

### Desafíos

* Agregue información del edificio y un mapa al flujo de notificaciones.

  > Utilice potencialmente imágenes, mapas, servicios externos para enviar esta información.

* ¿Se puede generar un código de barras para el código de visita? ¿Cuándo será útil?

  > Los códigos de barras pueden incluir información adicional, como el nombre de creación, y pueden escanearse con otra aplicación, lo que permite prescindir de la entrada manual de datos. ¿Cómo generar los códigos de barras? ¿Cómo usar fuentes de código de barras? ¿Imágenes? ¿Servicios externos?

* ¿Cómo garantizar un formato de fecha fácil de usar en el cuerpo del correo electrónico?

  > Localización en Power Apps, incluido el formato local específico, las monedas y las zonas horarias.

* ¿Es posible generar una tabla con información de estadía excesiva y enviar solo un correo electrónico?

  > Usando variables, creando expresiones más compleja y manipulando el formato del correo electrónico.

## Laboratorio 4: Power BI

En este laboratorio, creará un panel de Power BI que mostrará los datos sobre las visitas al campus.

Temas para discutir

-   ¿Quién es la audiencia objetivo del informe?
-   ¿Cómo consumirá el informe la audiencia? ¿Dispositivo típico? ¿Ubicación?
-   Cómo comenzar el diseño; cómo superar el lienzo en blanco
-   Conectarse a orígenes de datos, crear y refinar el modelo de datos 
-   ¿Tiene suficientes datos para visualizar?
-   ¿Cuáles son las características posibles que puede usar para analizar datos sobre las visitas?
-   Publicar y compartir los informes
-   Accesibilidad en Power BI al crear informes interactivos

### Desafíos

* Paneles e informes para incluir los planos del campus y los edificios.

  > Incorpore mapas, imágenes y datos externos a los informes

* Informe de los patrones y las tendencias de visitas y analícelos.

  > Discusión de las capacidades analíticas y de procesamiento de datos de Power BI.

* Visualización de visitantes que se quedaron más de lo debido.

  > Cómo hacer que los informes sean más atractivos. Hable acerca de la incorporación de Power Apps en Power BI para agregar capacidades de manipulación de datos en respuesta a los informes presentados.

* Streaming de Power BI para un procesamiento casi en tiempo real para un gran campus.

  > Este es un tema complejo y las soluciones probablemente estén fuera del alcance de la mayoría de los alumnos, pero es importante analizar el envejecimiento de los datos, las instantáneas frente a las transmisiones, la frecuencia de las actualizaciones de los datos y los datos obsoletos en general.

## Laboratorio 5: Aplicación basada en modelo

En este laboratorio, creará una aplicación impulsada por el modelo de Power Apps para permitir que el personal del campus administrativo administre los registros de visitas en todo el campus.

Temas para discutir:

* Aplicaciones basadas en modelos como parte de una solución
* Power Apps basadas en modelos frente al lienzo. Público objetivo y objetivos de la aplicación.
* ¿Cómo es un buen mapa del sitio?
* ¿Qué se debe incluir en una aplicación para una entidad determinada?
* Aplicaciones y roles, seguridad en CDS, recorte de la interfaz de usuario en aplicaciones basadas en modelos
* Ajuste del modelo de datos frente al ajuste de la aplicación basada en modelo

### Desafíos

* Seleccione vistas y formularios específicos para Visitas y Edificios

  > Ajustar la aplicación para el público objetivo. Crear vistas y formularios útiles

* El personal de seguridad generalmente trabaja en un solo edificio. ¿Cómo les proporcionaría una manera fácil de mostrar visitas solo para un edificio seleccionado?

  > Personalización en aplicaciones basadas en modelos, por ejemplo, las vistas personales. Cuadrículas y filtrado. Vistas fijas previas a la construcción si el número de edificios es pequeño. Subcuadrículas (en Forma de construcción)

* ¿Cómo restringiría el acceso a entidades específicas, por ejemplo, los edificios deben ser de solo lectura para todos los miembros del personal, excepto los administradores?

  > Roles de seguridad, recorte de la interfaz de usuario. Hablar potencialmente sobre los datos de referencia (entidades propiedad del usuario frente a entidades propiedad de la organización)

* ¿Qué paneles consideraría agregar a la aplicación?

  > Paneles integrados, lienzos incorporados, Power BI integrado