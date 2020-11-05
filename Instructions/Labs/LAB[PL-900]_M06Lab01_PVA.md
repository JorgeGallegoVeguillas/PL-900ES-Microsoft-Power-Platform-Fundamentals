---
lab:
    title: 'Laboratorio 8: Cómo crear un bot de chat básico'
    module: 'Módulo 6: Introducción a Power Virtual Agents'
---

# Módulo 6: Introducción a Power Virtual Agents
## Laboratorio: Cómo crear un bot de chat básico

# Escenario

Bellows College es una institución educativa que tiene un campus con varios edificios. Actualmente se guarda un registro físico de las visitas al campus. La información no se recaba de manera uniforme y no hay forma de recopilar y analizar los datos sobre las visitas de todo el campus.

Como la mayoría de las organizaciones, Bellows College está respondiendo rápidamente a las preocupaciones por desinformación sobre la COVID-19, los procedimientos recomendados, los horarios, etc. En este laboratorio, creará un bot de chat de Power Virtual Agents que dirigirá a la página del Centro para el control de enfermedades con preguntas y respuestas sobre el estado actual de la pandemia. La universidad querrá esta configuración para que se pueda integrar en su portal web, así como para que esté disponible ad hoc a medida que los departamentos hagan su propia reapertura planificada.

## Etapas de alto nivel

Seguiremos el esquema a continuación para crear un agente virtual de Power Virtual Agents:

  - Suscríbase para obtener una prueba de Power Virtual Agents

  - Cree un bot usando las preguntas frecuentes

  - Pruebe el bot

  - Cambie el saludo predeterminado

  - Publicar el bot

  - **Reto adicional:** Inserte el bot en su portal

## Requisitos previos

Se han identificado las siguientes condiciones como requisitos que debe implementar para completar el proyecto:

  - Finalización del **Módulo 0 Laboratorio 0: Validación del entorno de laboratorio**

  - Finalización del **Módulo 2 Laboratorio 1: Introducción a Common Data Service**

  - Solo para el ejercicio adicional: Finalización del **Módulo 6, Laboratorio 4: Introducción a los portales de Power Apps** 

## Cuestiones que tener en cuenta antes de comenzar

Los bots pueden ser muy útiles en muchos escenarios diferentes. Según lo que sabe hasta ahora sobre Bellows College, considere en qué otro lugar de la organización podría ser útil usar un bot.

# Ejercicio 1: Suscribirse en PVA y crear un nuevo bot

En este ejercicio, se suscribirá para obtener una prueba de Power Virtual Agents.

1.  Navegue a [Power Virtual Agents](https://powerva.microsoft.com/).

2.  Haga clic en **Iniciar prueba gratuita**.

3.  Conéctese, si es necesario.

4. Debería aparecer la ventana **Crear nuevo bot**.

5. Escriba **Bot de crisis** en **Nombre** y seleccione un idioma.

6. Seleccione su entorno de práctica para crear el bot y haga clic en **Crear**. Espere a que se cree el bot.

7. Pruebe el bot. Escriba **Hola** en el cuadro de mensaje y haga clic en **Enviar**. El bot debería saludarle y decirle lo que puede hacer.

8. Cierre el **Chat**.

9. Seleccione **Temas**. El bot viene con algunos temas del usuario de muestra y algunos temas del sistema. El saludo predeterminado procede de los temas del sistema.

10. En el próximo ejercicio, generará sus propios temas desde el sitio de P+F de los CDC. No salga de esta ventana del explorador.

# Ejercicio 2: Crear temas

En este ejercicio, creará temas del sitio de P+F de los CDC.

1.  En una nueva pestaña, navegue hasta el sitio [P+F de los CDC](https://www.cdc.gov/coronavirus/2019-ncov/faq.html) y examine su contenido. Creará sus temas a partir de estas preguntas frecuentes.

2.  Copie la URL.

3.  Vuelva a Power Virtual Agents y asegúrese de que **Temas** siga seleccionado.

4.  Seleccione la pestaña **Sugerencias** debajo de **Temas**.

5.  Haga clic en **Comenzar**.

6.  Pegue la URL que copió en el cuadro de texto **Vínculo al contenido en línea** y haga clic en **Agregar**.

7.  Haga clic en **Iniciar** y espere. Puede tardar unos minutos.

8.  Debería obtener algunas sugerencias de temas creados para usted.

9.  Haga clic para abrir uno de los temas sugeridos.

10. Debería ver la frase desencadenante y cuál será la respuesta del bot. **Haga clic en Agregar a temas.**
    
11. El tema sugerido debería agregarse a sus temas. Seleccione todos los temas sugeridos y haga clic en **Agregar a temas** (puede seleccionar todo usando el icono a la izquierda de la columna Nombre). Si recibe un mensaje de error, vuelva a intentarlo.

12. Una vez que se hayan agregado los temas sugeridos, seleccione la pestaña **Existente**. Debería ver los nuevos temas con su estado en Desactivado.

13. Haga clic en el interruptor de la columna **Estado** para establecerlos todos como **Activado**. Si tiene poco tiempo, puede activar los primeros diez, pero asegúrese de haber establecido "**¿Debo usar una mascarilla?**" como **Activado**.

14. No salga de esta ventana del explorador.

# Ejercicio 3: Temas de prueba

En esta tarea, probará los temas que ha agregado.

1.  Haga clic en **Probar su bot**.

2.  Haga clic en **Restablecer**.

3.  Escriba **¿Debería usar una mascarilla?** y haga clic en **Enviar**.

4.  El bot debería proporcionarle la información correcta y preguntarle si respondió a su pregunta. Haga clic en **Sí**.

5.  El bot debería pedirle una valoración de cómo lo hizo. Dele una valoración excelente.

6.  El bot debería preguntar si puede ayudarle con algo más. Haga clic en **No**.

7.  El bot debería concluir la sesión de chat.

8.  Escriba **hola** y haga clic en **Enviar**.

9.  El bot debería saludarle y decirle lo que puede hacer. Ahora, su bot puede ayudar a los usuarios con preguntas frecuentes sobre la COVID-19, por lo que deberá cambiar el mensaje de saludo en la siguiente tarea. No salga de esta ventana del explorador.

# Ejercicio 4: Cambiar el saludo

En esta tarea, cambiará el saludo a uno específico para temas sobre la COVID-19.

1.  Asegúrese de tener seleccionado **Temas** y la pestaña **Existente**.

2.  Contraiga la sección **Temas de usuario**.

3.  Haga clic para abrir el tema **Saludo** de los temas del sistema.

4.  El tema del saludo tiene 52 frases desencadenantes, haga clic en **Ir al lienzo de creación**.

5.  Vaya al primer mensaje y reemplácelo por **Hola. Soy un agente virtual**.** Puedo contarle cómo se transmite la COVID-19, cómo protegerse, cómo preparar su hogar y a su familia para la COVID-19, los síntomas, las pruebas, etc.**

6.  Haga clic en **Guardar**.

7.  Haga clic en **Bot de prueba** si su bot no sigue abierto. Haga clic en **Restablecer** para restablecer el chat.

8.  Escriba hola y haga clic en **Enviar**.

9.  El bot debería responder ahora con el nuevo saludo.

# Ejercicio 5: Publicar el bot

En este ejercicio, publicará el bot.

1.  Seleccione **Publicar** en la barra de navegación izquierda.

2.  Haga clic en **Publicar**.

3.  Haga clic de nuevo en **Publicar** y espere a que se complete la publicación.

4.  Expanda **Administrar** en la barra de navegación izquierda y seleccione **Canales**.

5.  Obtendrá una lista de los canales disponibles en los que puede publicar su bot. Seleccione **Sitio web demo**.

6.  Cambie el mensaje de bienvenida a **Pruebe mi bot de P+F sobre COVID-19.**

7.  Escriba "Quién tiene mayor riesgo de contraer una enfermedad grave por COVID-19", "Qué significa una enfermedad más grave" y "Qué están haciendo los CDC respecto a la COVID-19" como iniciadores de conversación y haga clic en **Guardar**.

8.  Copie la **URL**.

9.  Puede compartir la URL con sus compañeros y obtener sus comentarios. Abra una nueva ventana o pestaña del explorador y navegue hasta la URL que copió. El sitio web demo debería ser como la imagen inferior.

10. Continúe y empiece a chatear con el bot.  
    
Cuando haya terminado, su bot publicado debería tener un aspecto similar a esto:

![Sitio web demo del bot: captura de pantalla](./media/8-image1.png)

# Desafíos 
* Inserte su bot de chat en el portal de visitantes de Bellows College (más información sobre cómo hacerlo en **Agregar un bot a Power Apps** [aquí](https://docs.microsoft.com/en-us/power-virtual-agents/publication-connect-bot-to-web-channels)).
