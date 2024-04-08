# Docker

**Learned from Javascript Mastery** : [Video Link](https://www.youtube.com/watch?v=GFgJkfScVNU&t=18s)

**Analogy:** You have a lunch box it doesn't matter where you eat (at office, at home, at a picnic spot) it will be same irrespective of the location. <br>
That's how a docker is irrespective of OS it still works.

Docker is a platform that enables Development, packaging and execution in a unified environment.

```
Developing => Packaging => Executing : It works on all machines
```

1. Consistency Across Environments : Docker ensures it works on different computers(OS) <br>
   E.g Installing JS on different OS is different which makes the developer work hard, but docker commands is same for everyone so no more "IT WORKS ON MY MACHINE" scenarios.

   - Reduces confusion
   - Boost collaboration
   - making our app development and deployment faster
   - Keep everyone on the same page

2. **Isolation**: Docker maintains the complete isolation between our application and dependencies.

   - **Helps in**
     - Better security
     - Better debugging
     - smooth development

3. **Portability:** Docker let us move our application between different stages easily

   - From development to testing, testing to production
   - OR from one OS to another like moving from Linux to windows/mac vice-versa.

4. Docker containers are lightweight and share the host resources. Making them much better than traditional VMs. This efficiency leads to faster application start time and less resources consumption.

5. **Version Control:** Just like git docker also tracks the application which helps us to move between previous versions if something goes wrong.

6. **Scalability**: On the basis of user traffic docker will create copies of our application that will serve the user. <br>
   **Analogy:** Its like having multiple copies of an restaurant menu. When restaurant have more customers each menu serves one table.

7. **Devops Integration:** Docker bridges the gap between development & operations. Streamlining from coding to deployment.
   - This Integration ensures
     - Developed
     - Tested
     - Deployed Efficiently

## How does docker works ?

There are two major important concepts in Docker

1. Images
2. Containers

The entire workflow revolve around them.

### Image

A docker image is

- Lightweight
- Standalone
- Executable package
  which contains every thing to run a piece of software including code, runtime(like nodejs), libraries, system tools and even the OS.

Docker image is like an recipe which tells the instruction on how to make/run the application.

**Where we run these images?**<br>
In **containers**. Containers are runnable instance of docker images. It represents the execution environment for a specific application.

Docker Image like an recipe for cake. <br>
And container is actually the real baked cake which is served by us or anyone else.

From a single docker image we can create as many as container we want.

### Ever heard about Docker Volume ?

It is a persistent data storage mechanism. It allows to share the resources between docker container and a host machine(which can be a machine/server/or also you can share among multiple containers).

- Helps in data durability and persistence even if the container is stopped or removed
- Its just like a shared compartment/storage which exists outside the container.

### Docker Network

It's an communication channel that enables different docker containers to talk to each other or with the external world.

- It creates connectivity, allowing containers to share information & services while marinating isolation.

## Docker Workflow

Docker workflow is distributed in three parts.

1. Docker Client
2. Docker Host (aka Docker Daemon)
3. Docker Registry (aka Docker Hub)

### 1. Docker Client

A user interface for interacting with Docker. It's a tool which we use in docker to give commands.
Either we use command line or GUI to give commands.

### 2. Docker Host

It is responsible for background process work like managing the dockers on the host system.

- It listens for docker client commands.
- It create and manages containers
- Build images and handle other docker related tasks.

### 3. Docker Registry

It is a centralized repository of Docker Images. It hosts both private & public registries or packages.

And we when in case we try to run an image which is actually not present locally on the machine docker pulls the image from the docker registry that's why it is very helpful.

> Docker ==> Docker Hub <br>
> Git ==> Github

## Time to install docker

Installation steps: Best place is the [docs](https://www.docker.com/products/docker-desktop/)

I am using Ubuntu (22.04)

The below steps are for command-line interface.

1. First update the packages

```
sudo apt update
```

2. Install docker

```
sudo apt install docker.io
```

3. Enable the docker service so that whenever we boot up our machine(ubuntu in my case) it automatically starts

```
sudo systemctl enable docker
```

4. Check the docker service status

```
sudo systemctl status docker
```

4.1. If the output says not enabled then run `sudo systemctl start docker`
and then recheck once again with `status` command.

5. For testing run this

```
sudo docker run hello-world
```

For Docker Desktop refer docs.

What I did :

- Created docker account from docker website.
- created gpg-keys
- initialize the pass
- Then login inside docker desktop.
  All the steps detail are present in docker. It will take some time.
  [Watch this video](https://www.youtube.com/watch?v=5_EA3rBCXmU)
  For me I totally gone through Docs and it worked fine.

## How to create our own Docker Image ?

By using `dockerfile`, in this file we write the instructions for docker to create the image

Some commands for Dockerfile

1. **FROM**: starter base of our image

```docker
FROM image[:tag] [AS name]
# Example
FROM ubuntu:22.04
```

2. **WORKDIR**: setting the path

```docker
WORKDIR /path/to/workdir

#Example
WORKDIR /app
```

3. **COPY**: copy the files/directories from the build context to the image

```docker
COPY [--chown=<user>:<group>] <src>... <dest>
#Example
COPY . /app
```

4. **RUN**: execute the commands the in shell during image build

```docker
RUN <command>
#Example
RUN npm run dev
```

5. **EXPOSE**: this informs the docker that the container will listen on specified network port at runtime.

```docker
EXPOSE <port> [<port>/<protocol>...]
#Example
EXPOSE 3000
```

6. **ENV**: sets the environment variables during build process.

```docker
ENV KEY=VALUE
#Example
ENV NODE_ENV=production
```

7. **ARG**: defines built time variables

```docker
ARG <name>[=<default value>]
#Example
ARG NODE_VERSION=20
```

8. **VOLUME**: creates a mount point for externally mounted volumes. Essentially specifying a location inside your container where you can connect external storage.

```docker
VOLUME ["/data"]
#Example
VOLUME /myvol
```

9. **CMD**: provides default command to execute when the container starts

```docker
CMD ["executable","param1","param2"]
#Example
CMD ["npm","run","dev"]
CMD npm run dev
```

10. **ENTRYPOINT**: specifies the default executable to be run when the container starts

**Difference between ENTRYPOINT and CMD**

> The ENTRYPOINT command always executes, while the CMD command can be overridden. This distinction is essential when building Docker containers and determining the default behavior of your applications.

[This article](https://codewithyury.com/docker-run-vs-cmd-vs-entrypoint/) explain the difference between RUN, CMD & ENTRYPOINT

[Docker docs](https://docs.docker.com/reference/dockerfile/#understand-how-cmd-and-entrypoint-interact) on the same thing

**KEY DIFFERENCE BETWEEN CMD & ENTRYPOINT**

- **CMD**: Flexible, can be overridden, default executable.
- **ENTRYPOINT**: cannot be overridden, fixed starting point.

If both are used **CMD** arguments will be
passed to **ENTRYPOINT**

<hr>

## Running an docker image
0. Login in the terminal with your docker username and password.
```docker
docker login
```
I don't know but this is important to do before downloading an docker image, I am not able to see the changes in the **docker desktop** without docker login in terminal.

1. Pull an docker image
```docker
docker pull ubuntu
```
If the image is not present locally it will pull it from the docker hub.


2. Run the docker image
```docker
docker run -it ubuntu
```
`-it` **interactive**

Now go inside **docker desktop** and inside **Containers** section you will see your image is running.

Now in the terminal you will also see that the host name is looked just like it's an Ubuntu terminal.<br>
For me it looked like this
```bash
root@6c1074cba1a4:/# 
```
Run all the commands you know for testing like `ls`, `uptime`, `touch`, `mkdir` etc.

