CD usando argo cd e minikube

Ja com o minikube instalado em sua maquina 

Passo 1 
 Inicie o minikube 
  minikube start 

Passo 2 
 Instale o argo CD em seu cluster

  kubectl create namespace argocd
  kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

É possivel simular o ambiente eks onde ao mudar o tipo de clusterIp para loadbalancer ele atribua um ip externo ( no caso do minikube ele simula)

Edite o svc do argocd-server
mude para Load Balancer 

ao dar o comando "kubetcl get svc -n argocd , ira listar o serviço com o ip, so jogar no navegador

Login do arcd é admin, a senha é possivel pega-la com o comando " kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d
" 

No argocd 
 Applications 
  New app
   cluster https://kubernetes.default.svc
   path . ( Ja que o caminho esta no diretorio raiz )