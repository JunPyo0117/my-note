# 2. PaaS-TA 컨테이너 플랫폼 단독 배포
## 2-1 단독배포 아키텍쳐
![image](https://github.com/JunPyo0117/kubernetes/assets/80608601/675bb582-592e-4dff-863f-44fbd241f4e1)  

시스템 구성은 Kubernetes Cluster(Master, Worker) 환경으로 구성  
Kubespary를 통해 Kubernetes Cluster를 설치하고 Pod를 통해 Database, Private registry 등 미들웨어 환경을 제공하여 Container Image로 Kubernetes Cluster에 Container Platform 포털 환경을 배포  
총 필요한 VM 환경으로는 Master VM: 1개, Worker VM: 3개 이상이 필요하고 본 문서는 Kubernetes Cluster 환경을 구성하기 위한 Master VM 과 Worker VM 설치하며 NFS 서버를 별도로 생성하여 클러스터 구성

>컨테이너 플랫폼 v1.4 버전부터는 Cluster 배포 시 Storage가 함께 배포

>NFS 배포 시 NFS-Server 설치 선행 필요  
>[NFS 서버 설치](https://github.com/PaaS-TA/paas-ta-container-platform/blob/master/install-guide/nfs-server-install-guide.md)


## 2-2 Kubespray를 통한 kubernetes 클러스터 설치
### kubespray 란?
- kubespray 는 쿠버네티스를 쉽게 설치하는 자동화 도구  
- github을 클론받게 되면, ansible yaml파일들이 정리
- Ansible의 playbook과 inventory설정을 통해서 kubernetes 클러스터를 설정

[Kubernetes Clouster 설치가이드(PaaS-TA Github)](https://github.com/PaaS-TA/paas-ta-container-platform/blob/master/install-guide/standalone/cp-cluster-install.md)  
(위 링크 참조하여 kubespray로 쿠버네티스 클러스터 구성)

## 2-3 PaaS-TA 컨테이너 플랫폼 단독형 배포 포털 설치
![image](https://github.com/JunPyo0117/kubernetes/assets/80608601/3b62d1e6-0254-496d-a984-e36c210cf529)  
<u>음영처리된 부분 컨테이너 플랫폼 단독형 배포 포털에 포함되지 않음</u>  
- kubernetes Cluster(Master, Worker) 환경과 데이터 관리를 위한 스토리지 서버로 구성
- Kubespray를 통해 설치된 Kubernetes Cluster 환경에 컨테이너 플랫폼 포털 이미지
- Helm Chart를 관리하는 Harbor
- 컨테이너 플랫폼 포털 사용자 인증을 관리하는 Keycloak
- 인증 데이터를 관리하는 Vault
- 메타 데이터를 관리하는 MariaDB(RDBMS) 등 미들웨어 환경을 컨테이너로 제공
- 총 필요한 VM 환경으로는 Master VM: 1개, Worker VM: 3개 이상이 필요  

kubespray를 통해 kubernetest 클러스터 구성이 완료됐다면 PaaS-TA 컨테이너 플랫폼 포털 배포   
[단독형 배포 포털 설치 가이드(PaaS-TA Github)](https://github.com/PaaS-TA/paas-ta-container-platform/blob/master/install-guide/container-platform-portal/paas-ta-container-platform-portal-deployment-standalone-guide.md)  


## 2-4 컨테이너 플랫폼 포털 사용법
### 포털 메뉴
메뉴|분류|설명|접근 권한
Global|	Overview	클러스터 정보 대시보드	|Super Admin
Cluster| Admin (조회 권한)
Clusters|	클러스터 정보 관리
Cloud Accounts	Cloud Accounts 정보 관리
Instance Code Template	Instance Code Template 정보 관리
Clusters	Overview	클러스터 내 리소스 대시보드	All
Nodes	Nodes 정보 관리	Super Admin, Cluster Admin
Namespaces	Namespaces 정보 관리	All
Workloads	Deployments	Deployments 정보 관리	All
Pods	Pods 정보 관리
ReplicaSets	ReplicaSets 정보 관리
Services	Services	Services 정보 관리	All
Ingresses	Ingresses 정보 관리
Storages	Persistent Volumes	Persistent Volumes 정보 관리	Super Admin, Cluster Admin
Persistent Volume Claims	Persistent Volume Claims 정보 관리	All
Storage Classes	Storage Classes 정보 관리	Super Admin, Cluster Admin
ConfigMaps	ConfigMaps	ConfigMaps 정보 관리	All
Managements	Users	사용자 관리	Super Admin, Cluster Admin
Roles	Roles 관리	All
Resource Quotas	Resource Quotas 정보 관리
Limit Ranges	Limit Ranges 정보 관리
Info	Access	컨테이너 플랫폼 포털
CLI 사용을 위한 환경 설정 정보 관리	All
Private Repository	Private Repository 정보 관리

