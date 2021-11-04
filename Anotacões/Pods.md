# Pods

kubectl get pods

kubectl get pods -A 

kubectl get pods -n namespace

kubectl run teste —image=nginx:1.17 

kubectl run teste —image=nginx:1.17 —dry-run=client -o yaml > pod.yaml 

kubectl apply -f pod.yaml

kubectl describe pods teste

kubectl delete pods teste

kubcetl delete -f pod.yaml

kubectl top pods

kubectl edit pods teste

kubectl logs -f teste-5f58d84987-cltb9

- Example Manifesto Pods
    
    ```bash
    kubectl example pods       
    ---
    apiVersion: v1
    kind: Pod
    metadata:
      name: init-demo
    spec:
      containers:
        - name: nginx
          image: nginx
          ports:
            - containerPort: 80
          volumeMounts:
            - name: workdir
              mountPath: /usr/share/nginx/html
          resources:
            limits:
              memory: '1Gi'
              cpu: '800m'
            requests:
              memory: '700Mi'
              cpu: '400m'
      # These containers are run during pod initialization
      initContainers:
        - name: install
          image: busybox
          command:
            - wget
            - '-O'
            - '/work-dir/index.html'
            - http://kubernetes.io
          volumeMounts:
            - name: workdir
              mountPath: '/work-dir'
      dnsPolicy: Default
      volumes:
        - name: workdir
          emptyDir: {}
    ```
    

kubectl run teste —image=nginx:1.21 —command sleep 4800 —dry-run=client > pod.yaml
