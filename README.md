# CKAD
This is based on the learning


## Configuration 

A quick note on editing PODs and Deployments
Edit a POD
Remember, you CANNOT edit specifications of an existing POD other than the below.

* spec.containers[*].image

* spec.initContainers[*].image

* spec.activeDeadlineSeconds

* spec.tolerations

For example you cannot edit the environment variables, service accounts, resource limits (all of which we will discuss later) of a running pod. But if you really want to, you have 2 options:

1. Run the kubectl edit pod <pod name> command.  This will open the pod specification in an editor (vi editor). Then edit the required properties. When you try to save it, you will be denied. This is because you are attempting to edit a field on the pod that is not editable.



A copy of the file with your changes is saved in a temporary location as shown above.

You can then delete the existing pod by running the command:

``kubectl delete pod webapp``



Then create a new pod with your changes using the temporary file

``kubectl create -f /tmp/kubectl-edit-ccvrq.yaml``



2. The second option is to extract the pod definition in YAML format to a file using the command

``kubectl get pod webapp -o yaml > my-new-pod.yaml``

Then make the changes to the exported file using an editor (vi editor). Save the changes

``vi my-new-pod.yaml``

Then delete the existing pod

``kubectl delete pod webapp``

Then create a new pod with the edited file

``kubectl create -f my-new-pod.yaml``



Edit Deployments
With Deployments you can easily edit any field/property of the POD template. Since the pod template is a child of the deployment specification,  with every change the deployment will automatically delete and create a new pod with the new changes. So if you are asked to edit a property of a POD part of a deployment you may do that simply by running the command

``kubectl edit deployment my-deployment``


## Linux Academy 

### Kubernetes API primitives (Objects)

* ``kubectl api-resources -o name``

* ``kubectl get pods -n kube-system``

* ``kubectl get nodes``

* ``kubectl get nodes $node_name``

* ``kubectl get nodes $node_name -o yaml``

* ``kubectl describe node $node_name``

### Creating Pods

* Create a pod from the yaml definition file:

``kubectl create -f my-pod.yml``

* Edit a pod by updating the yaml definiton and re-applying it:

``kubectl apply -f my-pod.yml``

* You can also edit a pod like this:

``kubectl edit pod my-pod ``

* You can delete a pod like this:

``kubectl delete pod my-pod``


### Namespaces

<https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/>


* You can get a list of the namespaces in the cluster like this:

``kubectl get namespaces``

* You can also create your own namespaces.

``kubectl create ns my-ns``

* Create the pod with the created yaml file.

``kubectl create -f my-ns.yml``

* Use the -n flag to specify a namespace when using commands like kubectl get

``kubectl get pods -n my-ns``

* You can also use -n to specify a namespace when using kubectl describe.

``kubectl describe pod my-ns-pod -n my-ns``


### Basic Container Configuration

<https://kubernetes.io/docs/tasks/inject-data-application/define-command-argument-container/>


