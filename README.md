Certifique se todos os nós do cluster estão com docker, docker-compose e kubernetes.

Deploy do DSpace 6:

kubectl apply -f https://raw.githubusercontent.com/celosop/dspaceufrpe/master/dspace.deploy.v6.yaml

https://github.com/celosop/dspaceufrpe/blob/master/dspace.deploy.v6.yaml

Checar o status(pode demorar uns 2 minutos para subir tudo) dos pods:

watch kubectl get all -o wide

(para sair do watch Ctrl+C)

Se quiser testar se o tomcat está acessível do localhost:

kubectl port-forward service/dspace-service 8080:8080

Acessar o site:

http://localhost:8080/xmlui
http://localhost:8080/jspui

Criar o administrador e ingest:

kubectl apply -f https://raw.githubusercontent.com/celosop/dspaceufrpe/master/dspace.job.create-admin.v6.yaml

https://github.com/celosop/dspaceufrpe/blob/master/dspace.job.create-admin.v6.yaml

kubectl apply -f https://raw.githubusercontent.com/celosop/dspaceufrpe/master/dspace.job.ingest.v6.yaml

https://github.com/celosop/dspaceufrpe/blob/master/dspace.job.ingest.v6.yaml

Checar o status(pode demorar uns 2 minutos para subir tudo) dos pods:

watch kubectl get all -o wide

(para sair do watch Ctrl+C)


Limpar o ambiente e matar os deployments:

kubectl delete -f https://raw.githubusercontent.com/celosop/dspaceufrpe/master/dspace.job.create-admin.v6.yaml
kubectl delete -f https://raw.githubusercontent.com/celosop/dspaceufrpe/master/dspace.job.ingest.v6.yaml
kubectl delete -f https://raw.githubusercontent.com/celosop/dspaceufrpe/master/dspace.deploy.v6.yaml
