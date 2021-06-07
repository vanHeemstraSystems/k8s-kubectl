k8s-kubectl
# k8s kubectl

This Docker image facilitates the installation of Kubernetes (k8s) client tool: kubectl on a docker host.

## Usage

1) Build and run the container as follows:

```
$ cd containers/k8s-kubectl/
$ cp sample.docker-compose.yml docker-compose.yml
$ docker-compose up -d
```

2) Check the container name as follows (container id may differ):

```
$ docker ps
CONTAINER ID  IMAGE                    COMMAND                    CREATED         STATUS         PORTS   NAMES
7caec052e161  k8s-kubectl_k8s-kubectl  "nginx -g 'daemon of ..."  27 minutes ago  Up 26 minutes  80/tcp  k8s-kubectl 
```

Hence, container name is: k8s-kubectl

3) Copy the kubectl binary executable from inside the Docker container k8s-kubectl to the Docker host (current directory):

```
$ sudo docker cp k8s-kubectl:/usr/local/bin/kubectl ./kubectl
```

4) Make kubectl executable from the location you copied it to (current directory) and move it to its execution directory (if current directory is other than execution directory)

```
$ chmod +x ./kubectl
$ sudo mv ./kubectl /usr/local/bin/kubectl
```

4) Check if the kubectl binary executable is now available on the Docker host:

```
$ sudo kubectl version --client
```

5) (Optional) look at the kubectl help page:

```
$ sudo kubectl --help
```

6) After a successful installation, you can stop the Docker container k8s-kubectl from running and remove it as it is no longer required

```
$ docker container stop [CONTAINER ID]
$ docker container rm [CONTAINER ID]
```  

That's all folks!!
