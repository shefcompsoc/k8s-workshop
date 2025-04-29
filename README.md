[//]: # (TODO: download the presentation as .pptx and add to files)

# CompSoc Kubernetes Workshop

Hello and welcome to the Kubernetes Workshop practical session! Here you'll learn how to create a cluster and deploy Pods to it. This README will be the main guide for students on what to do, but please feel free to ask the demonstrator if you have any questions.

## Resources

- [Workshop slides](https://docs.google.com/presentation/d/1gUAFvMCad-gJ7Em19_P0BnAhQpC_Osm9TZagCTWB4Aw/edit?usp=sharing)
- [Feedback form](https://forms.gle/1cabpZTWray8gk3X7)
- [Official Kubernetes documentation](https://kubernetes.io/docs/home)
- [Docker Desktop](https://www.docker.com/products/docker-desktop)

## Practical Instructions

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

## Acknowledgements

Resources used in the making of this workshop:
- [Kubernetes docs](https://kubernetes.io/docs/home)
- [Docker Desktop](https://www.docker.com/products/docker-desktop)