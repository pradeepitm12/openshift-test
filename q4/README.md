## Question 4 - Create a pod and secret (username and password), inject those secrets as env in your pod (logic of your choice) 

## Solution 4-

Step 1- oc new-project q4 


Step 2- oc oc new-app --name q4test https://github.com/pradeepitm12/nodejs-hello-world 

Step 3- oc get pods (to check pods are up)

Step 4- oc get svc

Step 5- oc expose svc/q4test 

Step 6- oc get route 

Step 7- Create secret 

     oc create secret generic mysecret \
    --from-literal USER="Pradeep" \
    --from-literal PASS="123@abc"
Step 8- check the secret 

      oc get secret/mysecret -o json
        {
            "apiVersion": "v1",
            "data": {
                "PASS": "MTIzQGFiYw==",
                "USER": "UHJhZGVlcA=="
    },
    "kind": "Secret",
    "metadata": {
        "creationTimestamp": "2019-02-01T20:39:27Z",
        "name": "mysecret",
        "namespace": "q4",
        "resourceVersion": "181929",
        "selfLink": "/api/v1/namespaces/q4/secrets/mysecret",
        "uid": "77a516a5-2661-11e9-8a72-525400e00413"
    },
    "type": "Opaque"
            }   

Step 9- Set the secret into a volutom 

       oc set volume dc/q4test --add \
        >     -t secret -m /opt/app-root/secure \
        >     --name myappsec-vol --secret-name mysecret
        deploymentconfig.apps.openshift.io/q4test volume updated

Step 10- Check status of pod
Step 11- curl and check result




