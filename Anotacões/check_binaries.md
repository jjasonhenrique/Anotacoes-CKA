### Check Binaries k8s

Acess github 

```bash
sha512sum /usr/bin/kubelet > /answer
sha512sum downloadfile >> /answer
Remove diference between hashes
cat /answer | uniq
```
