**Задача:** Есть приложение nginx и мы хотим подключить volume pvc, те подключить volume "откуда-то".

### Файлы:
- **sc.yaml** - StorageClass который объясняет что нам нужно использовать ручные операции
- **pvc.yaml** - 
- **configmap.yaml** - конфиг map для nginx чтобы возвращал название поды и настройка папки
- **deployment-with-pvc.yaml** - 
- **pv.yaml** - PersistentVolume, создадим руками



```bash
kubectl create -f sc.yaml 
# storageclass.storage.k8s.io/local-storage created

# Для проверки что все создалось
kubectl get sc

kubectl create -f pv.yaml 

# persistentvolume/node1-pv1 createdd
kubectl get pv

kubectl create -f deployment-with-pvc.yaml 
# deployment.apps/my-deployment-with-pvc created

kubectl create -f configmap.yml 
# configmap/fileshare created

kubectl create -f pvc.yaml 
# persistentvolumeclaim/fileshare created
```