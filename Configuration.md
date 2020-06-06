# Configuration (18%)

* Understand ConfigMaps

* Understand SecurityContexts

* Define an application’s resource requirements

* Create & consume Secrets

* Understand ServiceAccounts

    <https://kubernetes.io/docs/tasks/configure-pod-container/security-context/>
    
 ## Resource Requirements
 
    <https://kubernetes.io/docs/concepts/configuration/manage-compute-resources-container/#resource-requests-and-limits-of-pod-and-container>
    
  ## Secrets
  
  * <https://kubernetes.io/docs/concepts/configuration/secret/>
  
  * Create a secret using a yaml definition like this. It is a good idea to delete the yaml file containing the sensitive data after the secret object has been created in the cluster.
  
  * Once a secret is created, pass the sensitive data to containers as an environment variable.
