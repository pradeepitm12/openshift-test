# openshift-test
minishift status 

minishift start 

oc login -u developer -p redhat 


## Question - 1 Deploy https://github.com/sclorg/nodejs-ex on openshift in q1 namespace/project 


### Solution - 1
#### Step 1 - git clone https://github.com/sclorg/nodejs-ex#deploy-the-app 

Note - After observing the files I can see 

#### Step 2 - oc new-project q1 

#### Step 3 - oc new-app -f openshift/templates/nodejs.json 
### Output 

--> Deploying template "q1/nodejs-example" for "openshift/templates/nodejs.json" to project q1

     Node.js
     ---------
     An example Node.js application with no database. For more information about using this template, including OpenShift considerations, see https://github.com/sclorg/nodejs-ex/blob/master/README.md.

     The following service(s) have been created in your project: nodejs-example.
     
     For more information about using this template, including OpenShift considerations, see https://github.com/sclorg/nodejs-ex/blob/master/README.md.

     * With parameters:
        * Name=nodejs-example
        * Namespace=openshift
        * Version of NodeJS Image=8
        * Memory Limit=512Mi
        * Git Repository URL=https://github.com/sclorg/nodejs-ex.git
        * Git Reference=
        * Context Directory=
        * Application Hostname=
        * GitHub Webhook Secret=nFchbxCuLxrnLdvkLyDVJ1Cmx1BcEnFjFCcONb8W # generated
        * Generic Webhook Secret=dQOoOuTBIcSAov5hMQA4PGHr03tlDETEagcWKCFp # generated
        * Custom NPM Mirror URL=

--> Creating resources ...
    service "nodejs-example" created
    route.route.openshift.io "nodejs-example" created
    imagestream.image.openshift.io "nodejs-example" created
    buildconfig.build.openshift.io "nodejs-example" created
    deploymentconfig.apps.openshift.io "nodejs-example" created
--> Success
    Access your application via route 'nodejs-example-q1.192.168.42.179.nip.io' 
    Build scheduled, use 'oc logs -f bc/nodejs-example' to track its progress.
    Run 'oc status' to view your app.


#### Step 4 -  oc status 

   ### Output 


   In project q1 on server https://192.168.42.179:8443

http://nodejs-example-q1.192.168.42.179.nip.io (svc/nodejs-example)
  dc/nodejs-example deploys istag/nodejs-example:latest <-
    bc/nodejs-example source builds https://github.com/sclorg/nodejs-ex.git on openshift/nodejs:8 
    deployment #1 deployed 15 seconds ago - 1 pod

View details with 'oc describe <resource>/<name>' or list everything with 'oc get all'.


#### Step 5 - oc get all (to see what all the resources are created) 

### Output 

oc get all 


NAME                         READY     STATUS      RESTARTS   AGE
pod/nodejs-example-1-build   0/1       Completed   0          8m
pod/nodejs-example-1-m9952   1/1       Running     0          6m

NAME                                     DESIRED   CURRENT   READY     AGE
replicationcontroller/nodejs-example-1   1         1         1         6m

NAME                     TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)    AGE
service/nodejs-example   ClusterIP   172.30.49.164   <none>        8080/TCP   8m

NAME                                                REVISION   DESIRED   CURRENT   TRIGGERED BY
deploymentconfig.apps.openshift.io/nodejs-example   1          1         1         config,image(nodejs-example:latest)

NAME                                            TYPE      FROM      LATEST
buildconfig.build.openshift.io/nodejs-example   Source    Git       1

NAME                                        TYPE      FROM          STATUS     STARTED         DURATION
build.build.openshift.io/nodejs-example-1   Source    Git@e59fe75   Complete   8 minutes ago   1m34s

NAME                                            DOCKER REPO                         TAGS      UPDATED
imagestream.image.openshift.io/nodejs-example   172.30.1.1:5000/q1/nodejs-example   latest    6 minutes ago

NAME                                      HOST/PORT                                 PATH      SERVICES         PORT      TERMINATION   WILDCARD
route.route.openshift.io/nodejs-example   nodejs-example-q1.192.168.42.179.nip.io             nodejs-example   <all>                   None 

#### Step 6 - Check all the resource one by one (Not required, as we can check every thing by oc get all) 

   oc get pods (gives all the pods )

   oc get svc (gives all the services)

   oc get replicationcontroller (gives all the replication controller)

   oc get bc (gives all the build config)

   oc get build (gives all the build)  

   To get all the detail infromation about any resource use 

    e.g. oc describe pod/pod-name-x

#### Step 7 - After checking all the resources time to expose the route  

    Get the servic by - oc get svc
    As the service was already expose check for the route and found it to be http://nodejs-example-q1.192.168.42.179.nip.io/
 

#### Step 8 - Delete the project 
     oc delete projcet q1









