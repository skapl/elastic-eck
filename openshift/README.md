# Filebeat on Openshift

Read application logs in a specific namespace with filebeat.


## Usage

Deploy **busybox** for testing filebeat:
```
# create test namespace
oc create namespace test

# deploy busybox
oc apply -f busybox.yaml -n test
```

Deploy **filebeat**
```
# create monitoring namespace
oc create namespace monitoring

# deploy filebeat
oc apply -f filebeat/ -n monitoring
```


Check https://www.elastic.co/guide/en/beats/filebeat/current/running-on-kubernetes.html for more info.
