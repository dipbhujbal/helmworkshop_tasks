### Tasks

 Add a helm repository in local with name mybitnami pointing to URL https://charts.bitnami.com/bitnami
 
 ```
 helm repo add mybitnami https://charts.bitnami.com/bitnami
 helm repo list
 ```
 
 
 Search for the mysql helm chart using the above added mybitnami helm repo and check the versions available

  ```
  helm search repo mysql
  ```
