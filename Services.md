# Services

kubectl get svc

kubectl describe svc teste

kubectl expose deploy teste —port=80 —type=NodePort

- Tipos de Services:
    
    ⇒ ClusterIP -  Comunica apenas dentro do Cluster
    
    ⇒ NodePort - Permite comunicação através  do Node
    
    ⇒ LoadBalancer - cria um LoadBalancer
    

kubectl delete svc teste

- Exemplo Manifesto Services
    
    ```bash
    kubectl example service  
    ---
    apiVersion: v1
    kind: Service
    metadata:
      name: nginx-service
    spec:
      ports:
        - port: 8000 # the port that this service should serve on
          # the container on each pod to connect to, can be a name
          # (e.g. 'www') or a number (e.g. 80)
          targetPort: 80
          protocol: TCP
      # just like the selector in the deployment,
      # but this time it identifies the set of pods to load balance
      # traffic to.
      selector:
        app: nginx
    ```
