# Node

- Verificar nodes do Cluster
```
kubectl get nodes
```


- Verificar labels dos Nodes
```
kubectl get nodes —show-labels
```

- Setar label em determinado Node
```
kubectl label node kubernetes01 label=value
```

- Verificar uso de recursos no Node
``` 
kubectl top nodes
```

- Mostrar informações do Node
```
kubectl describe node kubernetes01
```
