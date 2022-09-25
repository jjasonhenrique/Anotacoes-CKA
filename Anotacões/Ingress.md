# Ingress

- Exemplo Manifesto Ingress
    
    ```bash
    kubectl example ingress
    ---
    apiVersion: networking.k8s.io/v1
    kind: Ingress
    metadata:
      name: world
      annotations:
        nginx.ingress.kubernetes.io/rewrite-target: /
    spec:
      ingressClassName: nginx-example
      rules:
      - http:
          paths:
          - path: /Europe
            pathType: Prefix
            backend:
              service:
                name: europe
                port:
                  number: 80
    ```
    
- Verificar ingress no namespace default
```
kubectl get ingress
```

- Verificar informações de ingress em determinado namespace
```
kubectl describe ingress ingress -n namespace
```
