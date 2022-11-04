## Tasks

**Note Use template files from https://github.com/infracloudio/citadel-internal/tree/master/workshops/helm/kubernetes_manifests and create a chart.

1.  Each and every manifest should be templated such that the name of each kubernetes resource should get generated as <release_name>-helm-module>

    Named template:
    
    ```
    {{- define "resource.name" -}}
     name: {{ .Release.Name }}-helm-module
    {{- end }}

    ```
    
    Use this template to name each resource
    e.g 
    
    ```
    metadata:
      {{- include "resource.name" .| nindent 2}}
    ```
2.  The kubernetes service resource should obtain the value for type of service and port from values.yaml

    nginx-service.yaml:
    
    ```
      ports:
    - port: {{ .Values.service.port }}
    ```
   
 3.  The serviceaccount will be created using kubernetes manifest provided and kubernetes deployment resource will be created in this service account ELSE the serviceaccount creation will be skipped and kubernetes deployment resource will be created in the default serviceaccount

     nginx-sa.yaml
   
       ```
       {{- if eq .Values.serviceAccount.create true }}
          apiVersion: v1
          kind: ServiceAccount
          metadata:
            {{- include "resource.name" .| nindent 2 }}
            labels:
              app.kubernetes.io/name: nginx-app
              app.kubernetes.io/instance: nginx
       {{- end }}
      ```
      
      nginx-deployment.yaml
      
      ```
        {{- if .Values.serviceAccount.create  }}
           serviceAccountName: {{ .Release.Name }}-helm-module
        {{- end }}
      ```
