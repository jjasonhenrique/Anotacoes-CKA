# Criar Cluster kubernetes com kind

kind create cluster —name cluster-jason —config arquivo.yaml

# Criar arquivo de configuração 
```
cat << EOF > arquivo.yaml
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
  - role: control-plane
  - role: worker
  - role: worker
EOF
```
