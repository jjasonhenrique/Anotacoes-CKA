# Troubleshooting

kubectl run test-pod --image=busybox:1.28 --rm -it --restart=Never -- nslookup ip-do-pod > nginx-resolver-pod.txt

kubectl run test-service --image=busybox:1.28 --rm -it --restart=Never -- nslookup nome-do -service > nginx-resolver-pod.txt

kubectl describe objectok8s nomedoobjectok8s

kubectl logs -f nomedopod

kubectl exec nomedopod — nslookup nomedoservice  > saida.out

Verificar  TargetPort do service

Verificar usuário e senha do pod da app e do banco usando kubectl edit

Verificar selector

Verificar nome do servico

Usar kubectl port-forward pod/name 8080:pod port e acessar pela sua máquina via browser ou curl

Service Selector = Pod Label

targertPort = containerPort

kubectl cluster-info

openssl x509 -noout -in pki/file ou kubeadm certs check-expiration