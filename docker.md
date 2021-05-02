# Docker
High-level concepts:
* Can think of an image as like a stopped container, and a container as a running image
* While a VM virtualizes hardware, containers virtualize an OS
  * Containers share the kernel of their host OS
* Containers work primarily by `namespaces` and `cgroups`
  * `namespaces` facilitate the isolation of process tree, filesystem, etc
  * `cgroups`, short for control groups, govern the resource utilization of containers



## Suitable Workloads
* Historically, containers were well-suited for *stateless* use-cases, but not as useful for *stateful* use-cases
  * This has changed over the last few years


## Docker
* Building an image:
  * `docker image build -t maintain/name:version .`
* Running in background mode:
  * `docker run -d -p 80:80 docker/getting-started`
* Running in interactive mode:
  * `docker container run -it --name test alpine sh`
  * Running `exit` will terminate the container (since the shell is PID 1/main process)
    * Can exit the shell but leave container running with `ctrl + p + q`
    * Delete the exiting (but still running) container with `docker container rm test -f`
* Hosting on a container registry:
  * `docker image push maintainer/name:version`
  * Will push to dockerhub by default
* Stopping and removing a container
  * `docker ps` to obtain the container id
  * `docker stop <id>`
  * `docker rm <id>`


### Images
An image is a bunch of independent layers that are loosely connected by a manifest file
* These layers are unaware of the bigger image 

## Dockerfile
A list of instructions for how to build an image of your app
* Convention that all instructions are CAPITALIZED
* Always starts with `FROM` base image (OS)
  * Alpine is popular, e.g. `FROM alpine`
* Next, usually want to `RUN` pulling in our backend
  * e.g. for node: `RUN apk add --update nodejs nodejs-npm`
* Next, want to copy our source code to the container OS image
  * `COPY . /src`
  * `WORKDIR /src`
* Install code dependencies
  * `RUN npm install`
* Expose the port application binds on
  * `EXPOSE 8080`
* `ENTRYPOINT` for specifying where to run the app
  * `ENTRYPOINT ["node", "./app.js"]`
  * ./app.js is relative to the `WORKDIR` location
* Finally, can build the image with `docker image build -t tag .`


### Multistage Builds
* A single Dockerfile that has multiple `FROM` instructions
  * Each `FROM` marks a stage of the build


### Logging
There are 2 main types of logs we are interested in: *daemon* logs and *container* logs
* Daemon logs are the logs from the docker daemon
  * Most modern linux systems use systemd, which get sent to journald
  * Can read these logs with command `journalctl -u docker.service`
  * Non-systemd, try `/var/log/messages`
  * Windows, try `~/AppData/Local/Docker`
* Container logs aka application logs
  * Docker hopes that apps log to `stdout` and `stderr`
  * Also supports logging drivers, such as Splunk
    * Set logging driver in `daemon.json`



### Microservices
Docker compose can be used to describe multi-container apps
* `docker-compose up` to bring the apps up
* `docker-compose down` to bring the apps down

### Best Practices
* Use official images
* Keep images small
* Be explicit in referencing images
  * Use specific releases, not always latest

