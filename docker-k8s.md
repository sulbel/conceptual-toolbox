# Docker and Kubernetes
High-level concepts:
* Can think of an image as like a stopped container, and a container as a running image
* 


## Suitable Workloads
* Historically, containers were well-suited for *stateless* use-cases, but not as useful for *stateful* use-cases
  * This has changed over the last few years


## Docker
* Building an image:
  * `docker image build -t maintain/name:version .`
* Running in interactive mode:
  * `docker container run -it --name test alpine sh`
  * Running `exit` will terminate the container (since the shell is PID 1/main process)
    * Can exit the shell but leave container running with `ctrl + p + q`
    * Delete the exiting (but still running) container with `docker container rm test -f`



## Kubernetes
