apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: mongo
  namespace: cloudchamp
spec:
  serviceName: mongo
  replicas: 3
  selector:
    matchLabels:
      role: db
  template:
    metadata:
      labels:
        role: db
        env: demo
        replicaset: rs0.main
    spec:
      affinity:
        podAntiAffinity:
          preferredDuringSchedulingIgnoredDuringExecution:
            - weight: 100
              podAffinityTerm:
                labelSelector:
                  matchExpressions:
                    - key: replicaset
                      operator: In
                      values:
                        - rs0.main
                topologyKey: kubernetes.io/hostname
      terminationGracePeriodSeconds: 10
      containers:
        - name: mongo
          image: mongo:4.2
          command:
            - "numactl"
            - "--interleave=all"
            - "mongod"
            - "--wiredTigerCacheSizeGB"
            - "0.1"
            - "--bind_ip"
            - "0.0.0.0"
            - "--replSet"
            - "rs0"
          ports:
            - containerPort: 27017
          volumeMounts:
            - name: mongodb-persistent-storage-claim
              mountPath: /data/db
  volumeClaimTemplates:
    - metadata:
        name: mongodb-persistent-storage-claim
      spec:
        accessModes:
          - ReadWriteOnce
        storageClassName: gp2
        resources:
          requests:
            storage: 0.5Gi
