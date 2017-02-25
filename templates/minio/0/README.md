# Minio.io

### Info:

 This template creates, scale in and scale out a multinodes minio cluster on top of Rancher. The configuration is generated with confd from Rancher metadata.
 Cluster size is static after deployement. It's mean that you should redeploy the stack if you should change the size of your cluster (minio.io limitation).


### Usage:

 Select Minio Cloud Storage from catalog.

 Enter the number of nodes for your minio cluster and set the key and secret to connect in minio.

 Click deploy.

 Minio can now be accessed over the Rancher network.

### Advance info
1. This template create first the container called `rancher-cattle-metadata`. It embedded confd, with some scripts to get many settings from Cattle scheduler and expose them through the volume.
2. Then, the template create `minio` container. It will launch the scripts provided from `rancher-cattle-metadata` container with `volumes_from`. it will create /opt/scheduler/conf/scheduler.cfg file with some usefull infos about container, service, stack and host. Next,  it will source `/opt/scheduler/conf/scheduler.cfg` and launch confd scripts to configure minio.

### Source, bugs and enhances

 If you found bugs or need enhance, you can open ticket on github:
 - [Minio official core project](https://github.com/minio/minio)
 - [Minio docker image](https://github.com/disaster37/alpine-minio)
 - [Rancher Cattle metadata docker image](https://github.com/disaster37/rancher-cattle-metadata)
