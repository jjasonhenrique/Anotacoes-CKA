# Secrets, ConfigMaps and ENV

- ENV
    
    ```bash
    containers:
    - name:
      image:
      env:
        - name:
          value
    ```
    
- Secrets
    
    ```bash
    containers:
    - name:
      image:
      envFrom:
        - secretRef:
            name: teste
    ```
    
- ConfigMaps
    
    ```bash
    containers:
    - name:
      image:
      envFrom:
        - configMapRef:
            name: teste
    ```
    

kubectl create configmap teste ⇒ sem informações 

kubectl create configmap teste1 —from-literal=APP=COLOR 

kubectl create configmap teste1 —from-file=/path 

kubectl create secret generic teste1 —from-literal=APP=COLOR  

kubectl create secret generic teste1 —from-file=/path  

- Example Manifesto Secret
    
    ```bash
    kubectl example secret
    ---
    apiVersion: v1
    kind: Secret
    metadata:
      name: test-secret
    data:
      username: example
      password: VBewrUI.42
    ```
    
- Example manifesto ConfigMap
    
    ```bash
    kubectl example configmap
    ---
    apiVersion: v1
    kind: ConfigMap
    metadata:
      name: test-configmap
    data:
      data-1: value-1
      data-2: value-2
    ```
    
- Usando Secret como Volume em um POD
    
    ```bash
    volumes:
    - name: app-secret-volume
      secret:
        secretName: app-secret
    ```
