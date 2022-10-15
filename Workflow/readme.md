
# Workflow for developing Docker container-based applications

Esta sección describe el flujo de trabajo de desarrollo de bucle interno para aplicaciones basadas en contenedores de Docker. El flujo de trabajo de ciclo interno significa que no está considerando el flujo de trabajo de DevOps más amplio, que puede incluir hasta la implementación de producción, y solo se enfoca en el trabajo de desarrollo realizado en la computadora del desarrollador. Los pasos iniciales para configurar el entorno no están incluidos, ya que esos pasos se realizan solo una vez.

Una aplicación se compone de sus propios servicios más bibliotecas adicionales (dependencias). Los siguientes son los pasos básicos que suele seguir al crear una aplicación Docker, como se ilustra en la Figura 5-1.

![logo](img/WhatsApp%20Image%202022-10-15%20at%204.16.00%20PM.jpeg)

Figura 5-1. Flujo de trabajo paso a paso para desarrollar aplicaciones en contenedores de Docker

En esta sección, se detalla todo este proceso y se explica cada paso importante centrándose en un entorno de Visual Studio.

Cuando usa un enfoque de desarrollo de editor/CLI (por ejemplo, Visual Studio Code más Docker CLI en macOS o Windows), necesita conocer cada paso, generalmente con más detalle que si usa Visual Studio. Para obtener más información sobre cómo trabajar en un entorno CLI, consulte el libro electrónico Ciclo de vida de la aplicación Docker en contenedores con plataformas y herramientas de Microsoft.

Cuando usa Visual Studio 2022, muchos de esos pasos se manejan por usted, lo que mejora drásticamente su productividad. Esto es especialmente cierto cuando usa Visual Studio 2022 y se dirige a aplicaciones de varios contenedores. Por ejemplo, con solo un clic del mouse, Visual Studio agrega el archivo Dockerfile y docker-compose.yml a sus proyectos con la configuración de su aplicación. Cuando ejecuta la aplicación en Visual Studio, crea la imagen de Docker y ejecuta la aplicación de varios contenedores directamente en Docker; incluso le permite depurar varios contenedores a la vez. Estas características impulsarán su velocidad de desarrollo.

Sin embargo, el hecho de que Visual Studio haga que esos pasos sean automáticos no significa que no necesite saber qué sucede debajo de Docker. Por lo tanto, la siguiente guía detalla cada paso.

## Step 1. Start coding and create your initial application or service baseline.

![logo_2](img/WhatsApp%20Image%202022-10-15%20at%204.20.07%20PM.jpeg)

El desarrollo de una aplicación Docker es similar a la forma en que desarrolla una aplicación sin Docker. La diferencia es que mientras desarrolla para Docker, está implementando y probando su aplicación o servicios que se ejecutan dentro de los contenedores de Docker en su entorno local (ya sea una configuración de máquina virtual de Linux por Docker o directamente Windows si usa contenedores de Windows).

## Step 2. Create a Dockerfile related to an existing .NET base image.

![logo_3](img/WhatsApp%20Image%202022-10-15%20at%204.23.24%20PM.jpeg)

Necesita un Dockerfile para cada imagen personalizada que desee crear; también necesita un Dockerfile para cada contenedor que se implementará, ya sea que implemente automáticamente desde Visual Studio o manualmente mediante la CLI de Docker (comandos docker run y docker-compose). Si su aplicación contiene un solo servicio personalizado, necesita un solo Dockerfile. Si su aplicación contiene varios servicios (como en una arquitectura de microservicios), necesita un Dockerfile para cada servicio.

El Dockerfile se coloca en la carpeta raíz de su aplicación o servicio. Contiene los comandos que le indican a Docker cómo configurar y ejecutar su aplicación o servicio en un contenedor. Puede crear manualmente un Dockerfile en código y agregarlo a su proyecto junto con sus dependencias de .NET.

Con Visual Studio y sus herramientas para Docker, esta tarea requiere solo unos pocos clics del mouse. Cuando crea un nuevo proyecto en Visual Studio 2022, hay una opción llamada Habilitar compatibilidad con Docker, como se muestra en la Figura 5-3.