

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: details-v1
  labels:
    app: details
    version: v1
spec:
  replicas: 1
  selector:
    matchLabels:
      app: details
      version: v1
  template:
    metadata:
      labels:
        app: details
        version: v1
    spec:
      containers:
      - name: details
        image: codingcorp-docker.pkg.coding.net/nocalhost/bookinfo/details:v1
        imagePullPolicy: IfNotPresent
        command: ['ruby', 'details.rb', '9080']
        envFrom:
        - configMapRef:
            name: bookinfo-pre-install-config
        ports:
        - containerPort: 9080
        volumeMounts:
    		- mountPath: /home/code
      		name: nocalhost-shared-volume
      volumes:
  			- name: nocalhost-shared-volume
  			  emptyDir: {}
```

