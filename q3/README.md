
## Question 3- Create a pod and configmap (of some file), use configmap as a volume (logic of your choice)

### Solution 3- 

#### Step 1- oc login -u developer -p redhat

#### Step 2- oc new-project q3 

Note: Written an app in nodejs so it can process an Environment variable. 


#### Step 3- oc new-app --name q3test https://github.com/pradeepitm12/nodejs-hello-world 

#### Output
    --> Found image df21ce4 (2 weeks old) in image stream "openshift/nodejs" under tag "8" for "nodejs"

    Node.js 8 
    --------- 
    Node.js 8 available as container is a base platform for building and running various Node.js 8 applications and frameworks. Node.js is a platform built on Chrome's JavaScript runtime for easily building fast, scalable network applications. Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient, perfect for data-intensive real-time applications that run across distributed devices.

    Tags: builder, nodejs, nodejs8

    * The source repository appears to match: nodejs
    * A source build using source code from https://github.com/pradeepitm12/nodejs-hello-world will be created
      * The resulting image will be pushed to image stream tag "q3test:latest"
      * Use 'start-build' to trigger a new build
    * This image will be deployed in deployment config "q3test"
    * Port 8080/tcp will be load balanced by service "q3test"
      * Other containers can access this service through the hostname "q3test"

--> Creating resources ...
    imagestream.image.openshift.io "q3test" created
    buildconfig.build.openshift.io "q3test" created
    deploymentconfig.apps.openshift.io "q3test" created
    service "q3test" created
--> Success
    Build scheduled, use 'oc logs -f bc/q3test' to track its progress.
    Application is not exposed. You can expose services to the outside world by executing one or more of the commands below:
     'oc expose svc/q3test' 
    Run 'oc status' to view your app.

#### Step 4- oc get pods (to check if pod is up)

#### Step 5- oc get svc 

    q3test    ClusterIP   172.30.87.252   <none>        8080/TCP   2m 

#### Step 6- oc expose svc/q3test 


#### Step 7- oc get route 

     q3test    q3test-q3.192.168.42.179.nip.io             q3test     8080-tcp                 None

#### Step 8 - curl -i q3test-q3.192.168.42.179.nip.io 

    Pradeep undefined

#### Step 9 - oc create configmap myconf --from-literal APP_MSG="Pradeep" 

     configmap/myconf created

#### Step 10 - oc set env dc/q3test --from configmap/myconf (set the coinfig as environment variable) 

     deploymentconfig.apps.openshift.io/q3test updated

#### Step 11 - oc get pods (after an update in dc new pod get started) 

      q3test-1-build   0/1       Completed   0          7m
q3test-2-snffm   1/1       Running     0          47s

#### Step 12- curl to chek 
      Hello Pradeep
