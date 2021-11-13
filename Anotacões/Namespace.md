# Namespace

- Exibir namespaces
```
kubectl get ns
```

- Criar arquivo de manifesto do tipo namespace
```
kubectl create ns —dry-run=client -o yaml > arquivo.yaml
```

- Mostrar informações do namespace
```
kubectl describe ns namespace
```

- Editar informações de um namespace
```
kubectl edit namespace
```
