# Volume

kubectl get pvc

kubctl get pv

- Example Manisfesto PV
    
    ```bash
    kubectl example pv     
    ---
    kind: PersistentVolume
    apiVersion: v1
    metadata:
      name: pv0001
      labels:
        type: local
    spec:
      capacity:
        storage: 100Mi
      accessModes:
        - ReadWriteOnce
      hostPath:
        path: '/somepath/data01'
    ```
    
- Example Manifesto PVC
    
    ```bash
    kubectl example pvc
    ---
    kind: PersistentVolumeClaim
    apiVersion: v1
    metadata:
      name: myclaim-1
    spec:
      accessModes:
        - ReadWriteOnce
      resources:
        requests:
          storage: 100Mi
    ```
