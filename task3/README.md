### Task 3 
 Install latest version of mysql helm chart from mybitnami helm repository that you added earlier in your local. 
 Override the rootPassword value of mysql helm chart to something of your choice during installation.
 
 ##### 1. Install a chart and override the rootPassword value
 ```
helm install mysqlrel mybitnami/mysql --set auth.rootPassword=dip97
 ```
 
 ##### 2. verify the result
 
 ```
 1. MYSQL_ROOT_PASSWORD=$(kubectl get secret --namespace default mysqlrel -o jsonpath="{.data.mysql-root-password}" | base64 -d)
 
 2. To connect to your database:

   1. Run a pod that you can use as a client:

      kubectl run mysqlrel-client --rm --tty -i --restart='Never' --image  docker.io/bitnami/mysql:8.0.31-debian-11-r0 --namespace default --env MYSQL_ROOT_PASSWORD=$MYSQL_ROOT_PASSWORD --command -- bash

 
 
 
 
