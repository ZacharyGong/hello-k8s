# Storage
## Pod-level Volume
Deleted when pod is destroyed

### emptyDir
Create a new empty dir for the volume
- `kubectl create -f pod-vol-emptydir.yaml`
- `kubectl exec -it storage-vol-emptydir -- /bin/bash`: manipulate on the volume

### hostPath
Use an existing dir for the volume
- `kubectl create -f pod-vol-hostpath.yaml`
- `kubectl exec -it storage-vol-hostpath -- /bin/bash`: manipulate on the volume

## ConfigMap
### Creation
Create from a YAML file
- `kubectl create -f cm.yaml`
- `kubectl get cm`

Create from a host dir or file
- `kubectl create configmap cm1 --from-file=./configs`
- `kubectl create configmap cm2 --from-file=./configs/db.conf --from-file=./configs/cache.conf`
- `kubectl get configmap`

### Usage
Pass Config to pod as env
- `kubectl create -f pod-cm-env.yaml`
- `kubectl logs storage-cm-env`

Mount Config to pod as volume
- `kubectl create -f pod-cm-vol.yaml`
- `kubectl exec -it storage-cm-env -- /bin/bash`

## Secret
- `kubectl create -f secret.yaml`
- `kubectl get secret`


## Persistent Volume
### Persistent Volume (VP)


### PersistentVolumeClaim (VPC)
PVC is used to create a PV which will be later declared and used in a pod.
- `kubectl apply -f pvc1.yaml`: create a PVC


### Storage Class
- `kubectl create -f sc.yaml`: create a default storage class
- `kubectl create -f pvc-sc.yaml`: create a PVC
- `kubectl create -f pod-pvc-sc.yaml`: create a pod using the PVC
- `kubectl exec -it storage-pvc-sc -- /bin/sh`: access to the pod and test the storage