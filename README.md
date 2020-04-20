# Udacity Nanodegree Capstone project

In this project you will apply the skills and knowledge which were developed throughout the Cloud DevOps Nanodegree program. These include:

* Working in AWS
* Using Jenkins to implement Continuous Integration and Continuous Deployment
* Building pipelines
* Working with Ansible and CloudFormation to deploy clusters
* Building Kubernetes clusters
* Building Docker containers in pipelines

The requirements are checked against [this rubric](https://review.udacity.com/#!/rubrics/2577/view).

## Steps in Completing Your Project
1. Propose and Scope the Project
2. Use Jenkins, and implement blue/green or rolling deployment.
3. Pick AWS Kubernetes as a Service, or build your own Kubernetes cluster.
4. Build your pipeline
5. Test your pipeline

----

## Pipeline building Steps with Jenkins

### Infrastructure with CloudFormation

### Kubernetes cluster
Setting up a Cluster requires to have at least one worker node (i.e.  a working machine), in which we can have one containerized application (a pod). Four exemplary steps can be:
1. `export dockerpath="{Docker-id}/{app-name}:{version=latest}"`
2. Use Kubernetes to run the Docker Hub container, where the port is the one exposed by the Docker container
```
  kubectl run mlapp --port=80 --image=$dockerpath
```
3. `kubectl get pods` (list Kubernetes pods)
4. `kubectl port-forward deployment/{app-name} {app-port}:{exp-port}`

### In the Jenkinsfile
First, we need to install jenkins on our server.
1. Set number of stages (e.g. Build/Lint/Test)
2. Each stage has a series of steps


### In the Dockerfile
In order, we can instruct it to:
1. FROM - pick a base image
2. WORKDIR (opt.) - to create a virtualized working directory
3. COPY (opt.) - copy source data to WORKDIR
4. RUN - what need to be installed, or ran, before executing the container
5. EXPOSE port
6. CMD ["path","to","exec"]

It is suggested to use [Hadolint](https://github.com/hadolint/hadolint) for linting the Dockerfile.

Then, we first build the image

```
  docker build . --tag={app-name}
```

then, to check if successful, we can list the images

```
  docker image ls
```

and to run it we need to execute (`-it` to run a process)

```
  docker run -it --rm --name {app-name} -p {app-port}:{exposed-port} {app-name}
```
