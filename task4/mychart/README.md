## Task4 
**Note: Use the sample helm chart created earlier 
1. Creat a configmap with name <HELM_RELEASE_NAME>-nginx-configmap and mount it as a volume in the deployment

   configmap.yaml snippet :
    ```
    kind: ConfigMap
    metadata:
      name: {{ .Release.Name }}-nginx-configmap
    ```


   deployment.yaml snippet: 

   ```
             volumeMounts:
           - name: mnt
             mountPath: /usr/share/nginx/html/index.html
             subPath: index.html
       volumes:
          - name: mnt
            configMap:
             name: {{ .Release.Name }}-nginx-configmap

   ```

2. Create the helm template and verify the changes
   ```
   helm template <path to the sample helm chart>
   ```

3. Install the helm chart 
   ```
   helm install <release-name> <chart>
   ```
