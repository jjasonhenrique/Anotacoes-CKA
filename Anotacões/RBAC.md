# RBAC

kubectl get pods —as dev-user ⇒ Testa o comando com determinado usuário

kubectl create role developer --namespace=default --verb=list,create --resource=pods ⇒ Cria a role

kubectl create rolebinding dev-user-binding --namespace=default --role=developer --user=dev-user ⇒ Vincula usuário/serviceaccount com role

- Example Manifesto ServiceAccount
    
    ```bash
    kubectl example serviceaccount
    ---
    apiVersion: v1
    kind: ServiceAccount
    metadata:
      creationTimestamp: 2015-08-07T22:02:39Z
      name: default
      namespace: default
      uid: 052fb0f4-3d50-11e5-b066-42010af0d7b6
    secrets:
      - name: default-token-uudge
    imagePullSecrets:
      - name: myregistrykey
    ```
    
- Example Manifesto Role or ClusterRole
    
    ```bash
    kubectl example clusterrole   
    ---
    apiVersion: rbac.authorization.k8s.io/v1
    kind: ClusterRole
    metadata:
      # "namespace" omitted since ClusterRoles are not namespaced
      name: secret-reader
    rules:
      - apiGroups: ['']
        #
        # at the HTTP level, the name of the resource for accessing Secret
        # objects is "secrets"
        resources: ['secrets']
        verbs: ['get', 'watch', 'list']
    
    kubectl example role       
    ---
    apiVersion: rbac.authorization.k8s.io/v1
    kind: Role
    metadata:
      namespace: default
      name: pod-reader
    rules:
      - apiGroups: [''] # "" indicates the core API group
        resources: ['pods']
        verbs: ['get', 'watch', 'list']
    ```
    
- Example Manifesto RoleBinding
    
    ```bash
    kubectl example rolebinding   
    ---
    apiVersion: rbac.authorization.k8s.io/v1
    # This role binding allows "jane" to read pods in the "default" namespace.
    # You need to already have a Role named "pod-reader" in that namespace.
    kind: RoleBinding
    metadata:
      name: read-pods
      namespace: default
    subjects:
      # You can specify more than one "subject"
      - kind: User
        name: jane # "name" is case sensitive
        apiGroup: rbac.authorization.k8s.io
    roleRef:
      # "roleRef" specifies the binding to a Role / ClusterRole
      kind: Role #this must be Role or ClusterRole
      name: pod-reader # this must match the name of the Role or ClusterRole you wish to bind to
      apiGroup: rbac.authorization.k8s.io
    ```
