## Question 7- Create a pod and use NodePort service to expose it

## Solution 7- 

Step 1- create an app 

            oc new-app --name q7app https://github.com/pradeepitm12/nodejs-hello-world
Step 2- Write service file, reffer nodeport.yaml 

            oc create -f nodeport.yaml

Step 3- Expose the service 

            oc expose svc/q7-service

Step 4- curl to the node ip and port 

        curl 172.30.56.65:31080


### Reference - https://docs.openshift.com/container-platform/3.6/dev_guide/expose_service/expose_internal_ip_nodeport.html