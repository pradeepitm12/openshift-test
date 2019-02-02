## Question 9 - Write a job which can runs 4 pods in parallel (logic of your choice) 

## Solution 9- 

Step 1- oc new-project q9 


Step 2- Write a job.yaml file which inclued the information about number of parallel pods. 

Please check job.yaml

Step 3- oc create -f job.yaml

Step 4- oc get pods (4 pods ) 

        pod/pi-2fhx2   0/1       Completed   0          7m
        pod/pi-4tm2q   0/1       Completed   0          7m
        pod/pi-bfrzc   0/1       Completed   0          7m
        pod/pi-k78cl   0/1       Completed   0          7m

Step 5- oc logs -f pod/pi-2fhx2 

        14159265358979323846264338327950288419716939937510582097494459230781640628620899862803482534211706798214808651328230664709384460955058223172535940812848


## Note - Reference from https://blog.openshift.com/openshift-jobs/