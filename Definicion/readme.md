# Ducker_Compose
Tutorial de instalcion de Ducker


## DUCKER COMPOSE 

![Logo](img/docker-compose-logo.png)


Docker es una plataforma de código abierto para crear, implementar y gestionar aplicaciones en múltiples contenedores. Aprenda sobre los contenedores, cómo se comparan con las máquinas virtuales y por qué Docker es tan ampliamente adoptado y utilizado.

## __¿Qué es Docker?__
Docker es una plataforma de contenerización de código abierto. Permite a los desarrolladores empaquetar aplicaciones en contenedores: componentes ejecutables estandarizados que combinan el código fuente de la aplicación con las bibliotecas del sistema operativo (SO) y las dependencias necesarias para ejecutar dicho código en cualquier entorno. Los contenedores simplifican la entrega de aplicaciones distribuidas y se han vuelto cada vez más populares a medida que las organizaciones cambian al desarrollo nativo de la nube y entornos híbridos multinube.

Los desarrolladores pueden crear contenedores sin Docker, pero la plataforma permite crear, implementar y gestionar contenedores de forma más fácil, sencilla y segura. Docker es esencialmente un kit de herramientas que permite a los desarrolladores crear, implementar, ejecutar, actualizar y detener contenedores utilizando comandos simples y automatización que ahorra trabajo a través de una única API.

Docker también hace referencia a Docker, Inc. (enlace externo a IBM), la empresa que vende la versión comercial de Docker, y al proyecto de código abierto de Docker (enlace externo a IBM), a la que colaboran Docker, Inc. y muchas otras organizaciones e individuos.


## __¿Por qué utilizar Docker?__
Docker es tan popular hoy que "Docker" y "contenedores" se utilizan indistintamente. Pero las primeras tecnologías relacionadas con los contenedores estuvieron disponibles durante años, incluso décadas (enlace externo a IBM), antes de que Docker fuera lanzado al público en 2013.

Sobre todo, en 2008, LinuXContainers (LXC) se implementó en el kernel de Linux, lo que habilitó completamente la virtualización para una sola instancia de Linux. Mientras que LXC todavía se utiliza hoy, las nuevas tecnologías que utilizan el kernel de Linux están disponibles. Ubuntu, un sistema operativo Linux moderno y de código abierto, también proporciona esta capacidad.

Docker ha mejorado las capacidades nativas de contenerización de Linux con tecnologías que permiten:

Portabilidad mejorada y continua: mientras que los contenedores LXC suelen hacer referencia a configuraciones específicas de la máquina, los contenedores Docker se ejecutan sin modificaciones en cualquier entorno de desktop, centro de datos y nube.
Peso aún más ligero y actualizaciones más granulares: Con LXC, se pueden combinar varios procesos dentro de un único contenedor. Con los contenedores Docker, solo se puede ejecutar un proceso en cada contenedor. Esto permite crear una aplicación que puede continuar ejecutándose mientras una de sus partes se desactiva para realizar una actualización o reparación.
Creación automática de contenedores: Docker puede crear automáticamente un contenedor basado en el código de origen de la aplicación.
Control de versiones de contenedor: Docker puede rastrear versiones de una imagen de contenedor, retrotraer a versiones anteriores y rastrear quién creó una versión y cómo. Puede incluso cargar sólo los deltas entre una versión existente y una nueva.
Reutilización de contenedores: los contenedores existentes se pueden utilizar como imágenes base, esencialmente como plantillas para crear nuevos contenedores.
Bibliotecas de contenedores compartidos: los desarrolladores pueden acceder a un registro de código abierto que contiene miles de contenedores aportados por los usuarios.
Hoy en día, la contenerización de Docker también funciona con el servidor Microsoft Windows. Y la mayoría de los proveedores de nube ofrecen servicios específicos para ayudar a los desarrolladores a crear, enviar y ejecutar aplicaciones en contenedores con Docker.

Por estas razones, la adopción de Docker creció rápidamente y continúa aumentando. En este artículo, Docker Inc. informa 11 millones de desarrolladores y 13 mil millones de descargas de imágenes de contenedores cada mes (enlace externo a IBM).


# Mas informacion sobre docker

1. [workflow][workflow]

[Workflow]:https://github.com/LuisKrlos27/Ducker_Compose/tree/main/Workflow