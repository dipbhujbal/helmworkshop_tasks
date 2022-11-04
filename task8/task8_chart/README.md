### Tasks

 Create a pre-install and post-delete hook in your existing sample helm chart that simply runs a Kubernetes job with a busybox image and prints the output "I am performing prerequisite tasks!" and "I am done with cleanup!" respectively.
 
 Job pre-install.yaml
 
 ```
 apiVersion: batch/v1
 kind: Job
 metadata:
  name: pre-install-job
  annotations:
    "helm.sh/hook": "pre-install"
 spec:
  template:
    spec:      
      containers:
      - name: pre-install
        image: busybox
        imagePullPolicy: IfNotPresent     
        command: ['sh', '-c', 'I am performing prerequisite tasks! ; sleep 5'] 
 
 ```

 
 Job post-delete.yaml
 
 ```
 apiVersion: batch/v1
 kind: Job
 metadata:
  name: post-delete-job
  annotations:
    "helm.sh/hook": "post-delete"
 spec:
  template:
    spec:      
      containers:
      - name: post-delete
        image: busybox
        imagePullPolicy: IfNotPresent   
        command: ['sh', '-c', 'I am done with cleanup! ; sleep 5']  
 ```
