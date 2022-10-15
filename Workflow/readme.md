
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

## Step 3. Create your custom Docker images and embed your application or service in them.

![logo_4](img/WhatsApp%20Image%202022-10-15%20at%204.25.08%20PM.jpeg)

Para cada servicio de su aplicación, debe crear una imagen relacionada. Si su aplicación se compone de un solo servicio o aplicación web, solo necesita una sola imagen.

Tenga en cuenta que las imágenes de Docker se crean automáticamente en Visual Studio. Los siguientes pasos solo son necesarios para el flujo de trabajo del editor/CLI y se explican para aclarar lo que sucede debajo.

Usted, como desarrollador, necesita desarrollar y probar localmente hasta que envíe una característica completa o cambie su sistema de control de fuente (por ejemplo, a GitHub). Esto significa que debe crear las imágenes de Docker e implementar contenedores en un host de Docker local (VM de Windows o Linux) y ejecutar, probar y depurar en esos contenedores locales.

Para crear una imagen personalizada en su entorno local mediante la CLI de Docker y su Dockerfile, puede usar el comando de compilación de docker, como se muestra en la Figura 5-5.

## Step 4. Define your services in docker-compose.yml when building a multi-container Docker application.

![logo_5](img/WhatsApp%20Image%202022-10-15%20at%204.28.19%20PM.jpeg)

El archivo docker-compose.yml le permite definir un conjunto de servicios relacionados que se implementarán como una aplicación compuesta con comandos de implementación. También configura sus relaciones de dependencia y la configuración del tiempo de ejecución.

Para usar un archivo docker-compose.yml, debe crear el archivo en su carpeta de solución principal o raíz, con un contenido similar al del siguiente ejemplo:

version: '3.4'

services:

  webmvc:
    image: eshop/web
    environment:
      - CatalogUrl=http://catalog-api
      - OrderingUrl=http://ordering-api
    ports:
      - "80:80"
    depends_on:
      - catalog-api
      - ordering-api

  catalog-api:
    image: eshop/catalog-api
    environment:
      - ConnectionString=Server=sqldata;Port=1433;Database=CatalogDB;…
    ports:
      - "81:80"
    depends_on:
      - sqldata

  ordering-api:
    image: eshop/ordering-api
    environment:
      - ConnectionString=Server=sqldata;Database=OrderingDb;…
    ports:
      - "82:80"
    extra_hosts:
      - "CESARDLBOOKVHD:10.0.75.1"
    depends_on:
      - sqldata

  sqldata:
    image: mcr.microsoft.com/mssql/server:latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"

## Step 5. Build and run your Docker application.

![logo_6](img/WhatsApp%20Image%202022-10-15%20at%204.30.49%20PM.jpeg)

Si su aplicación solo tiene un único contenedor, puede ejecutarlo implementándolo en su host Docker (VM o servidor físico). Sin embargo, si su aplicación contiene varios servicios, puede implementarla como una aplicación compuesta, ya sea usando un solo comando CLI (docker-compose up) o con Visual Studio, que usará ese comando en secreto. Veamos las diferentes opciones.

## Step 6. Test your Docker application using your local Docker host.

![logo_7](img/WhatsApp%20Image%202022-10-15%20at%204.36.08%20PM.jpeg)

Este paso variará dependiendo de lo que esté haciendo su aplicación. En una aplicación web .NET simple que se implementa como un único contenedor o servicio, puede acceder al servicio abriendo un navegador en el host de Docker y navegando a ese sitio, como se muestra en la Figura 5-13. (Si la configuración en el Dockerfile asigna el contenedor a un puerto en el host que no sea 80, incluya el puerto del host en la URL).



