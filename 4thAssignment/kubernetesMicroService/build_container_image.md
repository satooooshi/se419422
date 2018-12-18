apiVersion: apps/v1beta2  
kind: Deployment  
metadata:  
  name: myApp  
  labels:  
    app: myApp  
spec:  
  replicas: 1  
  revisionHistoryLimit: 10  
  selector:  
    matchLabels:  
      app: myApp  
  template:  
    metadata:  
      labels:  
        app: myApp  
    spec:  
      containers:  
      - name: myApp  
        image: example/demo:latest  
        ports:  
        - containerPort: 8080  
          protocol: TCP  
        livenessProbe:  
          httpGet:  
            path: /  
            port: 8080  
          initialDelaySeconds: 30  
          timeoutSeconds: 30  
        imagePullPolicy: IfNotPresent  
      # Comment the following tolerations if Dashboard must not be deployed on master  
      tolerations:  
      - key: node-role.kubernetes.io/master  
        effect: NoSchedule  
  
---  
apiVersion: v1  
kind: Service  
metadata:  
  name: myApp  
  labels:  
    app: myApp  
spec:  
  ports:  
    - port: 8080  
      targetPort: 8080  
  selector:  
    app: myApp  
  type: NodePort  