## Question 6 - Create a pod with non-persistent volume

## Solution 6-

Write a pod defination which write a file, need to keep the pod live and finishes and get stuck into crashloopbackoff hence put a sleep of some time. 
Check the data by doing rsh into the machine.
Again start the pod , as the volume is not persistent hence you find only data for one line.

Step 1- oc new-project q6 

Step 2- oc create -f pod.yaml

Step 3- Check the data in the machine. 

        oc rsh myapp-main cat file/data

        This is temp data


Step 4- Delete the pod and again start

        oc delete pod --all
        oc create -f pod.yaml

Step 5- Again check the data

        oc rsh myapp-main cat file/data
        This is temp data       


        If it was a persistent volume then the output should be 
                This is temp data       

                This is temp data       

