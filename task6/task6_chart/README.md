## Task5

 Create a subchart in your existing helm chart from scratch.
 Add a bitnami mysql helm chart as the subchart for the existing sample chart you created earlier. Pass a custom value for rootPassword from your helm chart to mysql helm chart. Install your helm chart and verify the creation of mysql helm chart resources.
 
 
 Chart.yaml
 
 ```
 dependencies: 
  - name: mysql
    version: 9.3.5
    repository: https://charts.bitnami.com/bitnami
    condition: mysql.enabled
```


 Add a condition in your sample helm chart based on which mysql subchart installation can be enabled / disabled accordingly
 
 ```
 mysql:
 enabled: true
 auth: 
  rootPassword: *****
 ```
