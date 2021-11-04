# Others

Static Pods ficam em /etc/kubernetes/manifests (use ps aux | grep kubelet)

kubectl config view ⇒ Verifica arquivo config no .kube do usuário

kubectl explain objecto --recursive

kubectl api-resources

kubectl explain pod --recursive | grep -A3 hostPath ⇒ procura por algum parâmetro  especifico

ENTRYPOINT = COMMAND

CMD = ARGS

kubectl taint node node01 key=value:NoExecute
