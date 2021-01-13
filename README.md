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
$ docker run -p [port-on-host:port-in-container] [image-name] # run the image into localat at sepcific port ([externalPort]:[internalPort])
$ docker images              # list your images
$ docker ps                  # list your running containers
$ docker ps -a               # list your containers
$ docker rm [containerId]    # remove the container
$ docker rmi [imageId]       # remove an Image 
```

## Hooking The Source Code into a Container

So how do we get source code into a container ?

- Create a **container volume** that points to the source code.
- Add your source code into a **custom image** that is used to create a container.

### The Layered File System

When you pulled an image have a big size you actually pull much layers **for example**

```bash
$ docker pull nginx
Using the default tag: latest
latest: Pulling from library/nginx
**b8f262c62ec6**: Pull complete
**e9218e8f93b1**: Pull complete
**7acba7289aa3**: Pull complete
Digest: sha256:aeded0f2a861747f43a01cf1018cf9efe2bdd02afd57d2b11fcc7fcadc16ccd
```

As every image is built on top of Linux kernel, it has some common **dependencies** that can be **reused** by other images. Docker bundles these dependencies in one stack and these stacks are called **layers** which ****Docker caches these intermediate layers to speed up the image building process.

<p align="center" width="100%">
  <img src="https://github.com/aboelkassem/Learn-Docker/blob/main/images/docker-layerd-1.png" width="400" hight="400"/>
  <img src="https://github.com/aboelkassem/Learn-Docker/blob/main/images/docker-layerd-2.png" width="400" hight="400"/>
</p>

### Docker Volumes

- **Volume** is special type of **directory** in a **container** typically referred to as a "data volume" which you store any types of data that could be code, log files or database files and more.
- **Volumes** can be **shared** and reused among containers which make multiple container write the same volume and Container can have single or more volumes
- When **updating** an Image this **won't affect** to data volume which stayed separate
- Data volumes are **persisted** even after the container is **deleted**

<p align="center" width="100%">
  <img src="https://github.com/aboelkassem/Learn-Docker/blob/main/images/docker-volumes-1.png" width="400" hight="400"/>
  <img src="https://github.com/aboelkassem/Learn-Docker/blob/main/images/docker-volumes-2.png" width="400" hight="400"/>
</p>

To know what benefits of volumes Suppose you run a **MySQL** database with no volume, So any data stored in that database will be lost when the container is stopped or restarted. In order to avoid data loss, you can use a **volume mount**.

Now to create a volume where Node app could writes to /var/www is the container volume alias in Host area, run the following command creates **default volumes** in it's paths

```bash
$ docker run -p 8080:3000 -v /var/www node # create volume in the container
$ docker inspect [containerId]             # get the info of the container
....
"Mounts":[
	{
		"Name": "d185....86459",
		"Source":"/mnt/.../var/lib/docker/volumes/d185....86459/_data", # Host location
		"Destination":"/var/www", # Volume location in container
		"Driver":"local",
		"RW":true
	}
]
....
```

**For Customizing Volumes** to writes your **own** folder path on the host which can be your source code, log files or database files, This path can be in **your machine** and the volume **read and write** to that specific area

<p align="center" width="100%">
  <img src="https://github.com/aboelkassem/Learn-Docker/blob/main/images/docker-volumes.png" width="400" hight="400"/>
</p>

[**sourceCode_path**]: make this folder as the host mount or to put $(pwd) to make current directory is that the volume points to

$(pwd): this return the current working directory

```bash
$ docker run -p 8080:3000 -v [sourceCode_path]:/var/www node # create volume in the container but read/write into custom path when node container running
$ docker inspect [containerId]             # get the info of the container
....
"Mounts":[
	{
		"Name": "d185....86459",
		"Source":"/src", # Host location
		"Destination":"/var/www", # Volume location in container
		"Driver":"local",
		"RW":true
	}
]
....
```

```bash
$ docker rm -v [containerId]    # remove the container including it's volumes
$ docker run -it -p 80:80 -v "$(pwd):/app" -w "/app" mcr.microsoft.com/dotnet/sdk:3.1 /bin/bash
# the above command tell docker to run the container ASP.NETCore3.1 with **volume** linked from current directory(which run command from)
# to /app volume in the container making (-w /app  ) current directory to run commands from it and open the bash
```
