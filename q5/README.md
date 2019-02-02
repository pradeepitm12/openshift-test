
## Question 5 - Create a deployment which has init container, init container should create some file and which should be available in main pod. (logic of your choice)

## Solution 5-

Step 1- Create a pod with yaml. 

        oc create -f pod.yaml 
        This consist of the initContainer
Step 2- Observe the behaviour
        
        It can be observed that first initContainer msgs are printed and finally the main container.

        oc describe -f pod.yaml


        Name:         myapp-pod
Namespace:    q5
Node:         localhost/192.168.122.98
Start Time:   Sat, 02 Feb 2019 20:32:02 +0530
Labels:       app=myapp
Annotations:  openshift.io/scc=restricted
Status:       Running
IP:           172.17.0.6
Init Containers:
  init-myservice:
    Container ID:  docker://a64f60d515cdde2561c8a3cfbfefdf23d557ab1993b163079266759ec7486f60
    Image:         busybox
    Image ID:      docker-pullable://docker.io/busybox@sha256:7964ad52e396a6e045c39b5a44438424ac52e12e4d5a25d94895f2058cb863a0
    Port:          <none>
    Host Port:     <none>
    Command:
      sh
      -c
      until nslookup myservice; do echo waiting for myservice; sleep 2; done;
    State:          Terminated
      Reason:       Completed
      Exit Code:    0
      Started:      Sat, 02 Feb 2019 20:32:15 +0530
      Finished:     Sat, 02 Feb 2019 20:32:20 +0530
    Ready:          True
    Restart Count:  0
    Environment:    <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from default-token-ksndw (ro)
  init-mydb:
    Container ID:  docker://bfa1f91719d3172d1fbb035b33dde70d6c40930d67057e26fcc0e8dbc5701f7f
    Image:         busybox
    Image ID:      docker-pullable://docker.io/busybox@sha256:7964ad52e396a6e045c39b5a44438424ac52e12e4d5a25d94895f2058cb863a0
    Port:          <none>
    Host Port:     <none>
    Command:
      sh
      -c
      until nslookup mydb; do echo waiting for mydb; sleep 2; done;
    State:          Terminated
      Reason:       Completed
      Exit Code:    0
      Started:      Sat, 02 Feb 2019 20:32:37 +0530
      Finished:     Sat, 02 Feb 2019 20:32:42 +0530
    Ready:          True
    Restart Count:  0
    Environment:    <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from default-token-ksndw (ro)
Containers:
  myapp-container:
    Container ID:  docker://524e6f0a91fcf61fae7af1ce89f5a679b28af7806b19c0362d6c609160e9ea7a
    Image:         busybox
    Image ID:      docker-pullable://docker.io/busybox@sha256:7964ad52e396a6e045c39b5a44438424ac52e12e4d5a25d94895f2058cb863a0
    Port:          <none>
    Host Port:     <none>
    Command:
      sh
      -c
      echo The app is running! && sleep 3600
    State:          Running
      Started:      Sat, 02 Feb 2019 20:32:52 +0530
    Ready:          True
    Restart Count:  0
    Environment:    <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from default-token-ksndw (ro)
Conditions:
  Type           Status
  Initialized    True 
  Ready          True 
  PodScheduled   True 
Volumes:
  default-token-ksndw:
    Type:        Secret (a volume populated by a Secret)
    SecretName:  default-token-ksndw
    Optional:    false
QoS Class:       BestEffort
Node-Selectors:  <none>
Tolerations:     <none>
Events:
  Type    Reason     Age   From                Message
  ----    ------     ----  ----                -------
  Normal  Scheduled  1m    default-scheduler   Successfully assigned myapp-pod to localhost
  Normal  Pulling    1m    kubelet, localhost  pulling image "busybox"
  Normal  Pulled     1m    kubelet, localhost  Successfully pulled image "busybox"
  Normal  Created    1m    kubelet, localhost  Created container
  Normal  Started    1m    kubelet, localhost  Started container
  Normal  Pulling    1m    kubelet, localhost  pulling image "busybox"
  Normal  Pulled     1m    kubelet, localhost  Successfully pulled image "busybox"
  Normal  Created    1m    kubelet, localhost  Created container
  Normal  Started    1m    kubelet, localhost  Started container
  Normal  Pulling    1m    kubelet, localhost  pulling image "busybox"
  Normal  Pulled     57s   kubelet, localhost  Successfully pulled image "busybox"
  Normal  Created    56s   kubelet, localhost  Created container
  Normal  Started    56s   kubelet, localhost  Started container


Step 3- Create a service 

        oc create -f service.yaml



https://medium.com/@jmarhee/using-initcontainers-to-pre-populate-volume-data-in-kubernetes-99f628cd4519 

https://kubernetes.io/docs/concepts/workloads/pods/init-containers/#examples