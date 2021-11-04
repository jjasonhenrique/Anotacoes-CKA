# Ingress

- Example Manifesto Ingress
    
    ```bash
    kubectl example ingress
    ---
    apiVersion: networking.k8s.io/v1beta1
    kind: Ingress
    metadata:
      name: name-virtual-host-ingress
    spec:
      rules:
        - host: foo.bar.com
          http:
            paths:
              - backend:
                  serviceName: service1
                  servicePort: 80
        - host: bar.foo.com
          http:
            paths:
              - backend:
                  serviceName: service2
                  servicePort: 80
    ```
    

kubectl get ingress

kubectl describe ingress ingress -n namespace
