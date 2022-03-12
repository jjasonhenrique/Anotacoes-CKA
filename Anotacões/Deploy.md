- Verificar deploy no namespace default
```
kubectl get deploy
```


- Verificat deploy em todos os namespaces
```
kubectl get deploy -A
```


- Verificar deploy em algum namespace especifico
```
kubectl get deploy -n namespace
```


- Verificar informações  de um deploy
```
kubectl describe deploy teste
```


- Criar arquivo de manifesto do tipo deploy
```
kubectl create deploy teste --image=nginx:1.17 --replicas=3 --dry-run=client -o yaml > deploy.yaml
```


- Aplicar arquivo de configuração 
```
kubectl apply -f deploy.yaml
```


- Verificar replicaset no namespace default
```
kubectl get replicaset
```


- Editar deploy teste no namespace default
```
kubectl edit deploy teste
```


- Exemplo de Manisfesto Deploy   
    ```
    kubectl example deploy
    ---
    apiVersion: apps/v1
    kind: Deployment
    metadata:
      name: nginx-deployment
      labels:
        app: nginx
    spec:
      replicas: 3
      selector:
        matchLabels:
          app: nginx
      template:
        metadata:
          labels:
            app: nginx
        spec:
          containers:
            - name: nginx
              image: nginx:1.14.2
              ports:
                - containerPort: 80
    ```
    
- Exemplo de Manifesto DaemonSet
    ```
    kubectl example daemonset
    ---
    apiVersion: apps/v1
    kind: DaemonSet
    metadata:
      name: fluentd-elasticsearch
      namespace: kube-system
      labels:
        k8s-app: fluentd-logging
    spec:
      selector:
        matchLabels:
          name: fluentd-elasticsearch
      template:
        metadata:
          labels:
            name: fluentd-elasticsearch
        spec:
          tolerations:
            # this toleration is to have the daemonset runnable on master nodes
            # remove it if your masters can't run pods
            - key: node-role.kubernetes.io/master
              effect: NoSchedule
          containers:
            - name: fluentd-elasticsearch
              image: quay.io/fluentd_elasticsearch/fluentd:v2.5.2
              resources:
                limits:
                  memory: 200Mi
                requests:
                  cpu: 100m
                  memory: 200Mi
              volumeMounts:
                - name: varlog
                  mountPath: /var/log
                - name: varlibdockercontainers
                  mountPath: /var/lib/docker/containers
                  readOnly: true
          terminationGracePeriodSeconds: 30
          volumes:
            - name: varlog
              hostPath:
                path: /var/log
            - name: varlibdockercontainers
              hostPath:
                path: /var/lib/docker/containers
    ```
    
    
- Aumentar número de replicas de um deploy
```
kubectl scale deploy nginx --replicas=5
```


- Setar imagem de um deploy
```
kubectl set image deployments.apps/nginx-teste namecontainer=nginx:1.21.1 --record
```
