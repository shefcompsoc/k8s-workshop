# CompSoc Kubernetes Workshop

Hello and welcome to the Kubernetes Workshop practical session! Here you'll learn how to create a cluster and deploy Pods to it. This README will be the main guide for students on what to do, but please feel free to ask the demonstrator if you have any questions.

## Resources

- [Workshop slides](https://docs.google.com/presentation/d/1gUAFvMCad-gJ7Em19_P0BnAhQpC_Osm9TZagCTWB4Aw/edit?usp=sharing)
- [Feedback form](https://forms.gle/1cabpZTWray8gk3X7)
- [Official Kubernetes documentation](https://kubernetes.io/docs/home)
- [Docker Desktop](https://www.docker.com/products/docker-desktop)

## Setup Instructions

### Step 1: Install Docker Desktop (if you haven't already)

[Docker Desktop](https://www.docker.com/products/docker-desktop/) is a GUI for running Docker on your local machine. It also just happens to have a Kubernetes cluster built into it, which we'll be using today. Docker Desktop supports all operating systems so you shouldn't have any trouble installing it!

### Step 2: Configure Docker Desktop

By default, Docker Desktop doesn't install a Kubernetes cluster for you, you have to tell it to do that. 

#### Step 2.1: Go to Docker Desktop Settings

![Screenshot of Docker Desktop with an arrow pointing towards the settings icon](images/docs_settings.png)

#### Step 2.2: Go to the Kubernetes Tab & Enable Kubernetes

![Screenshot of Docker Desktop with an arrow pointing towards the Kubernetes settings tab and the Enable Kubernetes button](images/docs_kubernetes.png)

#### Step 2.3: Set Kubernetes Runtime & Apply Changes

![Screenshot of Docker Desktop with an arrow pointing towards the kubeadm cluster provisioner & the apply changes button](images/docs_apply.png)

#### Step 2.4: Test Kubernetes

Now that Kubernetes is installed, you can check that it's running by opening a terminal and running this command:
```shell
kubectl get nodes
```

If everything is installed correctly, you should get an output like this:
```
NAME             STATUS   ROLES           AGE   VERSION
docker-desktop   Ready    control-plane   2m    v1.32.2
```

## Tasks

### Task 1: Creating a Deployment

For this task, we'll create a new [Deployment](https://kubernetes.io/docs/reference/kubernetes-api/workload-resources/deployment-v1/) using the [traefik/whoami](https://github.com/traefik/whoami) container as an example. This should introduce you to the basics of applying manifests to a cluster.

#### Step 1: Read the manifest file

It's always a good idea to read the file you're about to apply before you do! For this task, we'll be applying [manifests/pods/deployment.yaml](manifests/pods/deployment.yaml).

As you're reading the manifest, see if you can answer these questions:
- How many replicas of this Pod are you deploying?
- Which container image are you about to deploy?
- What is the name of the Deployment, and thus the name of the Pods, that you're going to deploy?

#### Step 2: Apply the manifest

All manifests can be applied with the [kubectl](https://kubernetes.io/docs/reference/kubectl/) command. Normally, you would pass a YAML file from your local machine, but you can also use a URL to a raw text file instead, like so:
```shell
kubectl apply -f https://raw.githubusercontent.com/shefcompsoc/k8s-workshop/refs/heads/main/manifests/pods/deployment.yaml
```

#### Step 3: Check your Deployment

You should now be able to see that your Kubernetes cluster has a new Deployment running. You can check this by running:
```shell
kubectl get deployments
```

You should get an output similar to this:
```
NAME           READY   UP-TO-DATE   AVAILABLE   AGE
k8s-workshop   3/3     3            3           22m
```

## Acknowledgements

Resources used in the making of this workshop:
- [Kubernetes docs](https://kubernetes.io/docs/home)
- [Docker Desktop](https://www.docker.com/products/docker-desktop)