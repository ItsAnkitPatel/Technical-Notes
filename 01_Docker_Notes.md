# Index

- [Index](#index)
- [Docker](#docker)
  - [How does docker works ?](#how-does-docker-works)
    - [Image](#image)
    - [Ever heard about Docker Volume ?](#ever-heard-about-docker-volume)
    - [Docker Network](#docker-network)
  - [Docker Workflow](#docker-workflow)
    - [1. Docker Client](#1-docker-client)
    - [2. Docker Host](#2-docker-host)
    - [3. Docker Registry](#3-docker-registry)
  - [Time to install docker](#time-to-install-docker)
  - [How to create our own Docker Image ?](#how-to-create-our-own-docker-image)
  - [Running an docker image](#running-an-docker-image)
  - [Create our own docker image](#create-our-own-docker-image)
  - [Dockerize React application](#dockerize-react-application)
    - [Removing docker containers & images](#remove-images-containers)
    - [Reflecting Changes inside Docker](#reflecting-changes)

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
   - This Integration ensures - Developed - Tested - Deployed Efficiently
   <br>
   <div align="right"><b><a href="#index">↥ Back To Top</a></b></div>

<hr>

<h2 id="how-does-docker-works"> How does docker works ? </h2>

There are two major important concepts in Docker

1. Images
2. Containers

The entire workflow revolve around them.

<h3 id="image"> Image </h3>

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

<h3 id="ever-heard-about-docker-volume"> Ever heard about Docker Volume ? </h3>

It is a persistent data storage mechanism. It allows to share the resources between docker container and a host machine(which can be a machine/server/or also you can share among multiple containers).

- Helps in data durability and persistence even if the container is stopped or removed
- Its just like a shared compartment/storage which exists outside the container.

<h3 id="docker-network"> Docker Network </h3>

It's an communication channel that enables different docker containers to talk to each other or with the external world.

- It creates connectivity, allowing containers to share information & services while marinating isolation.
<br>
<div align="right"><b><a href="#index">↥ Back To Top</a></b></div>

<hr>

<h2 id="docker-workflow"> Docker Workflow </h2>

Docker workflow is distributed in three parts.

1. Docker Client
2. Docker Host (aka Docker Daemon)
3. Docker Registry (aka Docker Hub)

<h3 id="1-docker-client"> 1. Docker Client </h3>

A user interface for interacting with Docker. It's a tool which we use in docker to give commands.
Either we use command line or GUI to give commands.

<h3 id="2-docker-host"> 2. Docker Host </h3>

It is responsible for background process work like managing the dockers on the host system.

- It listens for docker client commands.
- It create and manages containers
- Build images and handle other docker related tasks.

<h3 id="3-docker-registry"> 3. Docker Registry </h3>

It is a centralized repository of Docker Images. It hosts both private & public registries or packages.

And we when in case we try to run an image which is actually not present locally on the machine docker pulls the image from the docker registry that's why it is very helpful.

> Docker ==> Docker Hub <br>
> is just like <br>
> Git ==> Github
> <br>

<div align="right"><b><a href="#index">↥ Back To Top</a></b></div>

<hr>

<h2 id="time-to-install-docker"> Time to install docker </h2>

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
<br>
<div align="right"><b><a href="#index">↥ Back To Top</a></b></div>

<hr>

<h2 id="how-to-create-our-own-docker-image"> How to create our own Docker Image ? </h2>

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
<br>

<div align="right"><b><a href="#index">↥ Back To Top</a></b></div>

<hr>

<h2 id="running-an-docker-image"> Running an docker image </h2>

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

<br>

<div align="right"><b><a href="#index">↥ Back To Top</a></b></div>

<hr>

<h2 id="create-our-own-docker-image"> Create our own docker image </h2>

For now we will create an docker image which says programmers communities favorite line "Hello World"

1. For now create an 'hello-world' folder
2. Inside this folder we will create `hello.js`(whatever name you like to give)
   Inside this file write the code, right now we will just add single log
   ```Javascript
   console.log("Hello World! Docker Speaking");
   ```
3. Inside `hello-world` folder create a docker file called **`Dockerfile`** yup no dot no extension.
4. From this point we are going to use the knowledge given in [How to create our own docker image](#how-to-create-our-own-docker-image) section
5. First we need to select the **base image** to run the app and since we want to run an
   javascript file we need an node runtime from docker hub.

   - In this we are going to use alpine version of nodejs (lightweight version of Linux)
     ```docker
     FROM node:20-alpine;
     ```
   - Now setting the working directory where our all commands will be executed
     ```docker
     WORKDIR /app
     ```
   - Copy everything from current directory to our docker image

     ```docker
     COPY . .
     ```

     - First dot represents on our machine current directory and second dot represents our docker container current directory

   - Now we have to specify the commands we want to run in our docker container
     ```docker
     CMD node hello.js
     ```
     So the final file will look like this

   ```docker
   FROM node:20-alpine

   WORKDIR /app

   COPY . .

   CMD node hello.js
   ```

6. Now inside your terminal navigate to the folder where your docker file is located in our case
   we will go inside `hello-world`

   ```bash
   cd hello-world/
   ```

7. Now we will create an docker image.

   ```bash
   sudo docker build -t hello-world .
   ```

   `-t` option is for tag, if not given the `latest` tag will be given by default.
   In this case we are giving `hello-world` tag <br>
   `.` is for path for docker file, since we are inside the folder where dockerfile is present we will just use `.` <br>
   That's all. Our docker image is created🎉

   > Btw there is an interesting issue related to **`sudo docker images`** vs **`docker images`** when you have free time check out this [issue](https://github.com/docker/desktop-linux/issues/79)

   **IMPORTANT:** If you don't like to put `sudo` everytime you run an docker command then you run this command and restart your machine

   ```bash
   sudo usermod -aG docker $USER
   ```

   If you want a video for above command here it is: [quick video](https://www.youtube.com/watch?v=VjUbSe8ONhs) <br>
   but before that I still recommend to check this [issue](https://github.com/docker/desktop-linux/issues/79) once so that you know what actually you are doing.

   To check our docker image

   ```docker
   docker images
   ```

8. Now all is left to run the docker image we've created.

   ```docker
   docker run hello-world
   ```

9. And if we want to run an interactive session just like we did in ubuntu container

   ```docker
   docker run -it hello-world sh
   ```

   This will open the shell in our working directory `/app` <br>
   and now we can run our **`hello.js`** file just like any javascript file `node hello.js`<br> because we have node installed in our container

<br>
<div align="right"><b><a href="#index">↥ Back To Top</a></b></div>

<hr>

<h2 id="dockerize-react-application"> Dockerize React application </h2>

1. First create react application

   ```npm
   npm create vite@latest react-docker
   ```

No need to do `npm i` we are going to install node_modules inside the docker image.

2. Go inside `react-docker/` and create a `Dockerfile` and put this code inside the Dockerfile.

   ```docker
   # set the base image to create the image for react app
   FROM node:20-alpine

   # create a user with permissions to run the app
   # -S -> create a system user
   # -G -> add the user to a group
   # This is done to avoid running the app as root
   # If the app is run as root, any vulnerability in the app can be exploited to gain access to the host system
   # It's a good practice to run the app as a non-root user
   RUN addgroup app && adduser -S -G app app

   # set the user to run the app
   USER app

   # set the working directory to /app
   WORKDIR /app

   # copy package.json and package-lock.json to the working directory
   # This is done before copying the rest of the files to take advantage of Docker’s cache
   # If the package.json and package-lock.json files haven’t changed, Docker will use the cached dependencies
   COPY package*.json ./

   # sometimes the ownership of the files in the working directory is changed to root
   # and thus the app can't access the files and throws an error -> EACCES: permission denied
   # to avoid this, change the ownership of the files to the root user
   USER root

   # change the ownership of the /app directory to the app user
   # chown -R <user>:<group> <directory>
   # chown command changes the user and/or group ownership of for given file.
   RUN chown -R app:app .

   # change the user back to the app user
   USER app

   # install dependencies
   RUN npm install

   # copy the rest of the files to the working directory
   COPY . .

   # expose port 5173 to tell Docker that the container listens on the specified network ports at runtime
   EXPOSE 5173

   # command to run the app
   CMD npm run dev
   ```

   > I got this dockerfile code from **javascript mastery** YT channel

3. Inside `react-docker/` create `.dockerignore` and write these lines

   ```docker
   node_modules/
   ```

   Our docker have `package.json` & `package-lock.json` file which means it will download <br>
   the node modules everytime docker image starts, so its ok to remove node_modules

4. Time to dockerize our react-app. <br>
   In terminal navigate to `react-docker` directory and run this command
   ```docker
   docker build -t react-docker .
   ```
5. Run the docker image

   ```docker
   docker run react-docker
   ```

   But right now if we try to open the url `http://localhost:5173/` we gonna get error.

   The reason is our host machine do not know about this port even though our container knows on which port the docker image should listen
   and the main reason behind this that docker runs
   in isolation environment that means the port will not be exposed on the host machine. <br>
   Inshort even though the port listening inside the container, it cannot be accessed from the outside.

   **So what's the solution ?** <br>
   Port mapping.

   This concept of docker helps to map the port between the container and the host machine.

   The structure is like this

   ```
   docker run -p docker-container-port:host-port docker-image-name
   ```

   In our case this is how it will look

   ```
   docker run -p 5173:5173 react-docker
   ```

   But this is not enough!

   We are using vite so we have to let it know too. For that we will go inside `react-docker/src/package.json` and change the`dev` value from `"dev":"vite"` to `"dev":"vite --host"`

   Now if we run our previous command i.e

   ```docker
   docker run -p 5173:5173 react-docker
   ```

   We gonna get error like this

   ```
   docker: Error response from daemon: driver failed programming external connectivity on endpoint
   serene_nobel (358342a4a36f819d006ba130ef0e617e962d5473f472cb71fb3814cb016a4b35): Bind for
   0.0.0.0:5173 failed: port is already allocated.
   ERRO[0000] error waiting for container: context canceled
   ```

   Long story short the error says the port is already in use.

   So what we gonna do? <br>
   We will stop the container and re run the container

   To do that we first have to first find the docker container id using `ps`

   ```docker
   docker ps
   ```

   This will list out our all containers(default it show the running ones) with the port they are listening to too.

   To list out all the available docker container.

   Now take the container id of `react-docker` container from `CONTAINER ID` column which we get using `docker ps` command. After that stop that container using below command

   ```docker
   docker stop container-id
   ```

   This will stop our `react-docker` now re run the container with host port

   ```docker
   docker run -p 5173:5173
   ```

   Now you can see the website running at `http://localhost:5173/`

   Just in case you deleted your image then just build the image using `docker build -t react-docker .` and map the port using `docker run -p 5173:5173`

<h3 id="remove-images-containers"> Removing Containers And Images </h3>

- To remove a specific container use `rm`

  ```docker
  docker rm container-id
  ```

- To remove a running container use `--force` flag (you can use the shortcut `-f` too) with `rm`
  ```docker
  docker rm container-id --force
  ```
- To remove all the inactive container then use the below command

  ```docker
  docker container prune
  ```

  You will get the prompt of Y/N choose Y and enter to proceed and delete the inactive containers.

- For removing an image use `rmi`

  ```docker
  docker rmi Image-Id
  ```

  You can get the image id using `docker images`

  All of these actions can be performed on Docker Desktop GUI too.

  For id we can use the starting three letters of the ID. e.g. `372a8ca0de4b` we can use `372` if three letters doesn't work then use the whole ID.

<h3 id="reflecting-changes">Reflecting Changes inside Docker</h3>

If we make any changes inside our local `react-docker` directory those changes will not reflect on the container.<br>
We want the same experience as we get in local system don't we ?

For that we will run this command with -v flag

```docker
docker run -p 5173:5173 -v "$(pwd):/app" -v /app/node_modules react-docker
```

This one not working at all for me. Eaccess issues.

If I find any answer in future I will add it here later. I have already spend many hours figuring it out
but it's not working so I choose to move to next step.

This [issue](https://github.com/vitejs/vite/issues/11620) might help you.

For now in my Dockerfile I'm Removing the `USER app` after `RUN chown -R app:app .` worked for me.
[Answer reference](https://github.com/adrianhajdin/docker-course/issues/4#issuecomment-1921701332)

<br>
<br>
<br>

After some more research and debugging I found out that the `-v` changes the file access to root privileges.
Here's the chatgpt concise answer:

```
when you run the container with the volume mount
docker run -p 5173:5173 -v "$(pwd):/app" -v /app/node_modules react-docker,
you're mounting the current directory ($(pwd)) to the `/app` directory inside the container.
This effectively replaces the /app directory inside the container with the contents of your local directory.

The ownership and permissions of the files and directories in your local directory are likely different from
what's expected inside the container. Therefore, when the container runs, the ownership and permissions of
the files and directories are determined by your local filesystem,
which is why they appear to be owned by root instead of app.

To maintain consistent ownership and permissions,
you might need to ensure that the files and directories in your local directory have the correct ownership
and permissions before running the container with the volume mount. Alternatively,
you could adjust the ownership and permissions inside the container
using commands in the Dockerfile or entrypoint script.
```

But still I haven't found how to change the user during `-v` flag usecase.
> Some useful insight: When we use `COPY` it sets the file access privilege which we copied to our container as **root**

<br>
<div align="right"><b><a href="#index">↥ Back To Top</a></b></div>

<hr>