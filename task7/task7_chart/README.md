### Tasks
 Create a test hook in your sample helm chart which validates that nginx service is up
 
 snippet from  ./tests/test-connection.yaml
 
 ```
 spec:
  containers:
    - name: wget
      image: busybox
      command: ['wget']
      args: ['{{ .Release.Name }}-helm-module:{{ .Values.service.port }}']
```
