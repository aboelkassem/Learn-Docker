## What is Docker ?

Docker is a way to simplify the process of **building application, shipping them as containers, and running** them in different environments like development, staging and production.

**Docker** runs natively on **Linux** or **Windows Server 2016 or higher** and runs on Windows box, Linux box or Mac box development machines (with a virtual machine)

Docker relies on "**images**" and "**containers**"

**Image** A **read-only template** composed of layered filesystems used to share common files and create Docker container instances. is something that's used to **build a container**, image have necessary **files** to run something on an OS and you have a framework or your database, for example Windows with [ASP.NET](http://asp.NET) Core and application Code, Image like a **blueprint of the container** but it creates a running instance of a container 

**Container** An **isolated and secured shipping container** created from an image that can be run, started, stopped, moved and deleted. Runs your application, they are actually where the live application runs or the database or caching server or whatever it may be to runs in windows, Linux server machine.

### Docker Benefits for web developers

- **Accelerate developer onboarding** means Docker helps to set up a development environment very quickly when work with team on the same containers with different machines


<p align="center" width="100%">
  <img src="https://github.com/aboelkassem/Learn-Docker/blob/main/images/docker-benefit-1.png" width="400" hight="400"/>
</p>

- **Eliminate App Conflicts** like having versions of frameworks which docker offer **isolated** containers and each container that contains its version

<p align="center" width="100%">
  <img src="https://github.com/aboelkassem/Learn-Docker/blob/main/images/docker-benefit-2.png" width="400" hight="400"/>
</p>

- **Environment Consistency** like moving your code and development environment by just moving images between different environments like from ****development to staging or production

<p align="center" width="100%">
  <img src="https://github.com/aboelkassem/Learn-Docker/blob/main/images/docker-benefit-3.png" width="400" hight="400"/>
</p>

- **Ship Software Faster** which make it high productivity, quality, consistency and predictability

<p align="center" width="100%">
  <img src="https://github.com/aboelkassem/Learn-Docker/blob/main/images/docker-benefit-4.png" width="400" hight="400"/>
</p>

- **Docker Hub**: Ever imagined sharing your machine like you share the code using **GitHub**? Docker’s Docker Hub provides access to **thousands of images** that are configured with the environment so that when your code works in your machine, you can build images and share it all over the internet.
- **Continuous integration support:** Docker supports CI tools like **[Travis](https://travis-ci.com/plans)** and **[Jenkins](https://www.jenkins.io)**. Docker images can be built and tagged with specific versions and deployed anywhere

    > **Travis** is a hosted continuous integration service used to build and test
    software projects hosted at GitHub and Bitbucket. **Jenkins** is a free and opensource automation server. It helps automate the parts of software
    development related to building, testing, deploying, facilitating continuous
    integration, and continuous delivery

### Docker Tools

- Docker Toolbox **(Deprecated)** for Windows 7 or 8/ Mac
- [Docker CE](https://hub.docker.com/editions/community/docker-ce-desktop-windows) (Community Edition) for windows 10 or Mac
    - Provides Image and Container
    - Enable **Hyper-V** for Windows **or Hyperkit** for Mac to run VMs

### Docker Architecture

<p align="center" width="100%">
  <img src="https://github.com/aboelkassem/Learn-Docker/blob/main/images/docker-arch-1.png" width="400" hight="400"/>
</p>

**Docker ecosystems**

- **Docker Registry**: Docker maintains all the images in the registry and they can be pulled from the registry too
- **Docker Hub**: This is the repository for all your custom-built images. Images can be pushed and accessed from the Hub
- **Docker Client:** The CLI tool used to interact with the Docker server
- **Docker Daemon:** The Docker server process/engine responsible for pulling, pushing, and building the images. It is also used for running the container

<p align="center" width="100%">
  <img src="https://github.com/aboelkassem/Learn-Docker/blob/main/images/docker-arch-2.png" width="500" hight="500"/>
</p>

### Setting Up Your Docker Environment

**Installing Docker on Mac**

- Navigate to [This link](https://hub.docker.com/editions/community/docker-ce-desktop-mac/) and download and install it.

**Installing Docker on Windows**

- Navigate to [This link](https://hub.docker.com/editions/community/docker-ce-desktop-windows) and download and install it

**Docker Kitematic Tool (usually not used much)**

<p align="center" width="100%">
  <img src="https://github.com/aboelkassem/Learn-Docker/blob/main/images/docker-kitematic.png" width="500" hight="500"/>
</p>

### Basic Key Commands

```bash
$ docker pull [imag-name]    # pull images from DockerHub to your dev env like asp.net,node.js
$ docker run [imag-name]     # run the image into localhost
$ docker run -p [port-on-host:port-in-container] [image-name] # run the image into localat at sepcific port ([specificPort]:**80**) 80 is fixed port for container 
$ docker images              # list your images
$ docker ps                  # list your running containers
$ docker ps -a               # list your containers
$ docker rm [containerId]    # remove the container
$ docker rmi [imageId]       # remove an Image 
```
