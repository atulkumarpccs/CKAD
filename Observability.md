## Observability (18%)

* Understand LivenessProbes and ReadinessProbes
* Understand container logging
* Understand how to monitor applications in Kubernetes
* Understand debugging in Kubernetes



### Documentation

* <https://kubernetes.io/docs/concepts/cluster-administration/logging/>

### Reference

* A sample pod that generates log output every second:

``` 
apiVersion: v1
kind: Pod
metadata:
  name: counter
spec:
  containers:
  - name: count
    image: busybox
    args: [/bin/sh, -c, 'i=0; while true; do echo "$i: $(date)"; i=$((i+1)); sleep 1; done']

```

*  Get the container's logs:

   ```kubectl logs counter```

*  For a multi-container pod, specify which container to get logs for using the -c flag:

   ```kubectl logs <pod name> -c <container name>```

*  Save container logs to a file:

   ```kubectl logs counter > counter.log ```
