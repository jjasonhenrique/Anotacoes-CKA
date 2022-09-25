### Create cert with OpenSSL

```bash
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout cert.key -out cert.crt -subj "/CN=world.universe.mine/O=world.universe.mine"
```

### Create secret type tls
```bash
kubectl create secret tls my-tls-secret --cert=cert.crt \--key=cert.key
```

### Edit or create new ingress
```bash
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: tls-example-ingress
spec:
  tls:
  - hosts:
      - world.universe.mine
    secretName: my-tls-secret
  rules:
  - host: world.universe.mine
    http:
      paths:
      - path: /europe
        pathType: Prefix
        backend:
          service:
            name: europe
            port:
              number: 80
```
