# Demonstrator's Handbook

Hi, this is a quick guide for workshop demonstrators to use during the practical. It'll mostly go over some of the common issues people face and how to resolve them.

## Someone's having issues and I can't fix it

Don't panic! If someone's having a problem and you've no idea why, then ask for some help from the other demonstrators. 

If no one can solve the issue, you may just have to ask the attendee to watch someone else do the practical. It sucks, but it's all we can do at that point.

## Common Problems

### Problem 1: Docker Desktop not starting

#### Solution 1: Attendee is running in a VM

The first thing to check is whether the attendee is trying to run Docker Desktop inside a VM. Docker is itself a Linux VM, so cannot run inside VMs (at least not without a lot of faff). If that's the case, you'll have to tell the attendee to use their host system.

#### Solution 2: Reinstall Docker Desktop

If the attendee is not running Docker Desktop in a VM, then get them to try reinstalling it.

### Problem 2: NodePort already allocated

Sometimes if an attendee is already running other software on their device, or they've attempted to apply [manifests/services/nodeport.yaml](manifests/services/nodeport.yaml) twice, they may get an error like this:
```
The Service "k8s-workshop" is invalid: spec.ports[0].nodePort: Invalid value: 30001: provided port is already allocated
```

#### Solution 1: Service already exists

The first thing to try should be running `kubectl get services`, looking at the `PORT(S)` column and seeing which Service is using that port, then running `kubectl delete service <service name>`.

#### Solution 2: No Service present

If there is no Service claiming that port, it's likely that another piece of software is running on the attendee's device and claiming that port. If the attendee is unsure what would be using that port, then the best solution now would be to tell them to:
- Clone the repo: `git clone https://github.com/shefcompsoc/k8s-workshop`
- Edit [manifests/services/nodeport.yaml](manifests/services/nodeport.yaml) to have a new `nodePort`
- Apply the new manifest by running `kubectl apply -f manifests/services/nodeport.yaml`