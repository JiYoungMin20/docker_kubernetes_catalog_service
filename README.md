# 한권으로 배우는 도커 & 쿠버네티스 (Docker & Kubernetes) by 장철원

## Chapter 11. 깃허브 액션과 ArgoCD를 활용한 CI/CD

### 3개의 YAML 파일 (Chapter07 / 07_end)

* postgresql.yml : Kubernetes Deplyoment (polar-postgres)
* deployment.yml : catalog-service Deployment
* service.yml : Kubernetes Service (type : ClusterIP)

### ArgoCD 설치, 비밀번호 만들기, 접속 방법

* ArgoCD 설치

kubectl create namespace argocd

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml


* ArgoCD 비밀번호 만들기

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo


* ArgoCD 접속 방법

kubectl port-forward svc/argocd-server -n argocd 8080:443


* ArgoCD삭제

kubectl delete -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

kubectl delete namespace argocd

===
