# Certificate

- Criação  de certificado usando CSR
    
    ```bash
    cat <<EOF | kubectl apply -f -
    apiVersion: certificates.k8s.io/v1
    kind: CertificateSigningRequest
    metadata:
      name: my-svc.my-namespace
    spec:
      request: $(cat server.csr | base64 | tr -d '\n')
      signerName: kubernetes.io/kubelet-serving
      usages:
      - digital signature
      - key encipherment
      - server auth
    EOF
    ```
    
- Liberação  de acesso a certificado
    
    ```bash
    kubectl certificate approve agent-smith
    kubectl certificate deny agent-smith
     
    ```
    
- Excluir requisição CSR
    
    ```bash
    kubectl delete csr agent-smith
    ```