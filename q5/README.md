
## Question 5 - Create a deployment which has init container, init container should create some file and which should be available in main pod. (logic of your choice)

## Solution 5- 

Write a pod defination where it reads a file from a mounted volutme, but as data is not created write an initContainer so that it can create a volume write data. Please reffer pod.yaml

Step 1 - oc new-project q5

Step 2 - oc create -f pod.yaml

Step 3- Check pods 

            oc get pods
            Notice that initContainer are running first and then main pods 

Step 4- Check logs 

            oc logs -f pod/myapp-main

            output : config:data


https://medium.com/@jmarhee/using-initcontainers-to-pre-populate-volume-data-in-kubernetes-99f628cd4519 

https://kubernetes.io/docs/concepts/workloads/pods/init-containers/#examples