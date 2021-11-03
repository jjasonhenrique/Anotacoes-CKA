# Deploy

kubectl get deploy

kubectl get deploy -A

kubectl get deploy -n namespace

kubectl describe deploy teste

kubectl create deploy teste --image=nginx:1.17 --replicas=3 --dry-run=client -o yaml > deploy.yaml

kubectl apply -f deploy.yaml

kubectl get replicaset

kubectl edit deploy teste

- Example Manisfesto Deploy
    
    ```bash
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
    
- Example Manifesto DaemonSet
    
    ```bash
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
    

kubectl scale deploy nginx --replicas=5

kubectl set image deployments.apps/nginx-teste nginx=nginx:1.21.1 --record