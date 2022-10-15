
# Workflow for developing Docker container-based applications

Esta sección describe el flujo de trabajo de desarrollo de bucle interno para aplicaciones basadas en contenedores de Docker. El flujo de trabajo de ciclo interno significa que no está considerando el flujo de trabajo de DevOps más amplio, que puede incluir hasta la implementación de producción, y solo se enfoca en el trabajo de desarrollo realizado en la computadora del desarrollador. Los pasos iniciales para configurar el entorno no están incluidos, ya que esos pasos se realizan solo una vez.

Una aplicación se compone de sus propios servicios más bibliotecas adicionales (dependencias). Los siguientes son los pasos básicos que suele seguir al crear una aplicación Docker, como se ilustra en la Figura 5-1.

![logo](img/WhatsApp%20Image%202022-10-15%20at%204.16.00%20PM.jpeg)

Figura 5-1. Flujo de trabajo paso a paso para desarrollar aplicaciones en contenedores de Docker

En esta sección, se detalla todo este proceso y se explica cada paso importante centrándose en un entorno de Visual Studio.

Cuando usa un enfoque de desarrollo de editor/CLI (por ejemplo, Visual Studio Code más Docker CLI en macOS o Windows), necesita conocer cada paso, generalmente con más detalle que si usa Visual Studio. Para obtener más información sobre cómo trabajar en un entorno CLI, consulte el libro electrónico Ciclo de vida de la aplicación Docker en contenedores con plataformas y herramientas de Microsoft.

Cuando usa Visual Studio 2022, muchos de esos pasos se manejan por usted, lo que mejora drásticamente su productividad. Esto es especialmente cierto cuando usa Visual Studio 2022 y se dirige a aplicaciones de varios contenedores. Por ejemplo, con solo un clic del mouse, Visual Studio agrega el archivo Dockerfile y docker-compose.yml a sus proyectos con la configuración de su aplicación. Cuando ejecuta la aplicación en Visual Studio, crea la imagen de Docker y ejecuta la aplicación de varios contenedores directamente en Docker; incluso le permite depurar varios contenedores a la vez. Estas características impulsarán su velocidad de desarrollo.

Sin embargo, el hecho de que Visual Studio haga que esos pasos sean automáticos no significa que no necesite saber qué sucede debajo de Docker. Por lo tanto, la siguiente guía detalla cada paso.

![logo_2](img/WhatsApp%20Image%202022-10-15%20at%204.20.07%20PM.jpeg)