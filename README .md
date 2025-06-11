<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/0/00/Universidad_Tecnol%C3%B3gica_del_Norte_de_Guanajuato_%28UTNG%29_LOGO.png" alt="Logo UTNG" width="200"/>
</p>

<h1 align="center">Universidad Tecnológica del Norte de Guanajuato</h1>

<h2 align="center">Ingeniería en Redes Inteligentes y Ciberseguridad</h2>
<h3 align="center">Grupo: GIRI9051</h3>
<h3 align="center">Unidad 1</h3>
<h3 align="center">Nombre: Julián Alexis Cano Cruces</h3>
<h3 align="center">Número de Control: 1222100415</h3>
<h3 align="center">Fecha: 11/06/25</h3>

---


# ENTORNOS DE DESARROLLO EN LA AUTOMATIZACIÓN DE REDES

## Índice

1. [Introducción](#1-introducción)  
2. [Desarrollo](#2-desarrollo)  
   - [2.1 Descripción de las herramientas utilizadas para automatización](#21-descripción-de-las-herramientas-utilizadas-para-automatización)  
     - [2.1.1 Docker Engine](#211-docker-engine)  
     - [2.1.2 Docker Compose](#212-docker-compose)  
     - [2.1.3 Docker Swagger](#213-docker-swagger)  
   - [2.2 Procedimiento de instalación](#22-procedimiento-de-instalación)  
     - [2.2.1 Instalación técnica de herramientas necesarias](#221-instalación-técnica-de-herramientas-necesarias)  
     - [2.2.2 Instalación técnica de Docker](#222-instalación-técnica-de-docker)  
     - [2.2.3 Instalación técnica de Git](#223-instalación-técnica-de-git)  
   - [2.3 Evidencia de pruebas de verificación de funcionamiento](#23-evidencia-de-pruebas-de-verificación-de-funcionamiento)  
     - [2.3.1 Imagen Hello-world](#231-imagen-hello-world)  
     - [2.3.2 Archivo .YML](#232-archivo-yml)  
3. [Conclusión](#3-conclusión)  
4. [Bibliografía](#4-bibliografía)

---

## 1. Introducción

En el presente reporte se documenta el procedimiento realizado para la instalación, configuración y verificación del funcionamiento de herramientas de automatización de redes utilizadas en la Unidad I del curso "Automatización de Infraestructura Digital". Se abordan las herramientas principales como Docker Engine, Docker Compose y Docker Swagger, así como el entorno de desarrollo empleado, incluyendo Visual Studio Code (VSCode), Git y los plugins necesarios. Este archivo README busca ser una guía técnica clara y reproducible, útil tanto para estudiantes como profesionales que desean automatizar la infraestructura de red mediante contenedores.

Durante el proceso, se ejecutaron pruebas para verificar el correcto funcionamiento del entorno de desarrollo, como la ejecución de la imagen “hello-world” con Docker, y el despliegue de un archivo .yml usando Docker Compose para comprobar la creación y ejecución de contenedores. Además, se incluye una lista de verificación y recursos de comunidades colaborativas que sirvieron de apoyo durante el proceso. El objetivo es dejar documentado un procedimiento funcional que sirva como base para la automatización de infraestructura en proyectos futuros.

---

## 2. Desarrollo

### 2.1 Descripción de las herramientas utilizadas para automatización

#### 2.1.1 Docker Engine
Motor de contenedores que permite crear, ejecutar y gestionar contenedores de forma eficiente. Facilita la implementación de aplicaciones empaquetadas con todas sus dependencias.

#### 2.1.2 Docker Compose
Herramienta para definir y correr aplicaciones Docker multicontenedor mediante archivos .yml, permitiendo una gestión centralizada y automatizada.

#### 2.1.3 Docker Swagger
Herramienta para la documentación y prueba de APIs RESTful. Permite crear interfaces interactivas para consumir y probar servicios de forma sencilla y visual.

---

### 2.2 Procedimiento de instalación

#### 2.2.1 Instalación técnica de herramientas necesarias

- Visual Studio Code: instalado desde [https://code.visualstudio.com](https://code.visualstudio.com), configurado con plugins como Docker, GitLens, y YAML.
- Git: instalado desde el repositorio oficial usando `sudo apt install git`.
- Docker: siguiendo la documentación oficial de Docker para Ubuntu.
- Docker Compose: incluido a partir de Docker v20.10 como plugin.

#### 2.2.2 Instalación técnica de Docker

Para instalar Docker en un sistema Ubuntu, se siguen los siguientes pasos:

1. Actualizar la lista de paquetes:
```bash
sudo apt-get update
```

2. Instalar certificados y herramientas necesarias:
```bash
sudo apt-get install ca-certificates curl gnupg
```

3. Agregar la clave GPG oficial de Docker:
```bash
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```

4. Agregar el repositorio de Docker al sistema:
```bash
echo   "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu   $(. /etc/os-release && echo "$VERSION_CODENAME") stable" |   sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

5. Actualizar la lista de paquetes e instalar Docker:
```bash
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

6. Verificar la instalación con la imagen hello-world:
```bash
sudo docker run hello-world
```

7. Para ejecutar Docker sin sudo, agregar el usuario al grupo docker:
```bash
sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker
```

8. Verificar nuevamente sin sudo:
```bash
docker run hello-world
```


#### 2.2.3 Instalación técnica de Git

```bash
sudo apt install git
git config --global user.name "Tu Nombre"
git config --global user.email "tuemail@example.com"
```

---

### 2.3 Evidencia de pruebas de verificación de funcionamiento

#### 2.3.1 Imagen Hello-world

**Evidencia:**

![Evidencia Hello World](ruta/a/la/imagen_hello_world.png)


Para verificar el funcionamiento correcto de Docker se ejecutó:

```bash
docker run hello-world
```

El resultado fue exitoso, mostrando un mensaje de confirmación que indica que Docker está correctamente instalado y que puede descargar y ejecutar imágenes.

#### 2.3.2 Archivo .YML

**Evidencia:**

![Evidencia stack-jacc](ruta/a/la/imagen_stack_jacc.png)


Se utilizó un archivo `stack-jacc.yml` con definición de servicios como PhpMyAdmin, MySQL, Backend Node y Frontend Angular. Para probarlo se ejecutó:

```bash
docker compose -f stack-jacc.yml up --build -d
```

Todos los servicios se levantaron correctamente, y se accedió a las interfaces web para PhpMyAdmin (`http://localhost:9090`) y al frontend (`http://localhost`) confirmando que los contenedores funcionan correctamente.

---

## 3. Conclusión

Durante el desarrollo de esta actividad, adquirí conocimientos sólidos sobre la instalación, configuración y verificación de un entorno de desarrollo moderno orientado a la automatización de redes digitales. El proceso implicó el uso de herramientas actuales y ampliamente adoptadas en la industria, como Docker y Docker Compose, las cuales permiten encapsular aplicaciones y servicios dentro de contenedores, facilitando su despliegue, escalabilidad y mantenimiento.

Gracias a estas herramientas, fue posible establecer un entorno funcional y reproducible, lo cual es fundamental en proyectos de infraestructura digital. La realización de pruebas como la ejecución de la imagen "hello-world" y el despliegue de servicios mediante archivos .YML confirmaron que las herramientas fueron instaladas y configuradas correctamente. Estos ensayos prácticos permitieron validar la operatividad del entorno y aseguraron que se encuentra listo para soportar desarrollos más complejos en fases posteriores del curso o en proyectos reales.

Además, durante esta experiencia aprendí a recurrir a recursos de comunidades colaborativas en línea, como foros técnicos, documentación oficial y repositorios públicos, los cuales resultaron fundamentales para la resolución de errores, la comprensión de conceptos avanzados y la mejora general del proceso.

---

## 4. Bibliografía

1. Docker Inc. (2024). *Get Docker*. Recuperado de https://docs.docker.com/get-docker/
2. Docker Inc. (2024). *Docker Engine Overview*. Recuperado de https://docs.docker.com/engine/
3. Docker Inc. (2024). *Docker Compose Overview*. Recuperado de https://docs.docker.com/compose/
4. Swagger API. (2024). *Swagger Tools*. Recuperado de https://swagger.io/tools/
5. Visual Studio Code. (2024). *Download VSCode*. Recuperado de https://code.visualstudio.com/
6. Git SCM. (2024). *Git Downloads*. Recuperado de https://git-scm.com/downloads
7. Ubuntu Docs. (2024). *Installing Docker on Ubuntu*. Recuperado de https://docs.docker.com/engine/install/ubuntu/
8. Bell, P. (2025). *Introducing GitHub: A Non-technical Guide*. O'Reilly Media. Accessed 4 June 2025.  
9. Gift, N., et al. (2019). *Python for DevOps: Learn Ruthlessly Effective Automation*. O'Reilly Media. Accessed 4 June 2025.  
10. Hillar, G. C. (2016). *Building RESTful Python Web Services*. Packt Publishing, Limited. Accessed 4 June 2025.  
11. Jackson, C., et al. (2020). *Cisco Certified DevNet Associate DEVASC 200-901 Official Cert Guide*. Cisco Press. Accessed 4 June 2025.  
12. Lenz, M. (2018). *Python Continuous Integration and Delivery: A Concise Guide with Examples*. Apress. Accessed 4 June 2025.  
13. Tsitoara, M. (2019). *Beginning Git and GitHub: A Comprehensive Guide to Version Control, Project Management, and Teamwork for the New Developer*. Apress. Accessed 4 June 2025.