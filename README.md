- CI/CD to Kubernetes using Jenkins and Helm

- Docker registry - https://hub.docker.com/_/registry (private)
- Helm repository - https://chartmuseum.com/ (private)

Follow the documentation for setting up your Helm repository. 

## Jenkins
Setup a [Jenkins](https://jenkins.io/) running with
- [Docker](https://www.docker.com/). Can build and push images
- [Kubectl](https://kubernetes.io/). Kubernetes CLI that will link Jenkins with the Kubernetes cluster
- [Helm](https://helm.sh/). Kubernetes package manager to simplify deployment of your Docker containers to Kubernetes

There is a [GitHub example](https://github.com/trung85/jenkins-in-kubernetes) of such a Docker image, to be used in Kubernetes.

## Build the web application
You can build the web application directly by running `build.sh`. You can create the Docker image and run it locally. See the [build.sh](build.sh) options.
```bash
# See options
$ ./build.sh --help
```

You can also pack and push the Docker image and Helm chart.
