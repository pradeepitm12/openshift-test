## Theory 

1. Differencec between pod and deployment

        Pod is one or more containers deployed together in one node. They are immuitable while an app is running. Pods have life cycle of Defineation -> assignemnt -> run -> removed. 

        Deployment is a collection of pods which controled by replication controller. It can have multiple triggers configured to it.

     

2. Working of s2i and buildconfig 


   S2I 

        s2i is a tool used to create ready to use images. 
        It relies on scripts like assemble , run , save-artifacts 
        An image is initiated and the code is tared into it.
        First code is untared 
        Assemble builds the code and put it at appropiate folder. 
        run is responsible run/execute the programm 

    BuildConfig 

        It defines the build defination and when the    
        build should be triggered.
        It also defines the build strategy to use .
        It cheks for the meta data in the file and take action accordingly,

3. Imagestream 

        An imagestream can contain multiple docker container images which can be identified by tags.
        It can be used to update a deployment if an update comes example a new version of bases image.
        It actually provides a well suited environment for any program to run.

4. Probing
        A well deployed, running, healthy application can become unhealth at any point of time because of any unknown issue.
        Probe helps to keep an eye on the health of the app.

        Readiness 
            It check if the app is ready to serve the request, if not  then openshift removes the container ip from table.
        Livness 
            It checks the health of an app. If health status is unhealthy then openshift restart the pod.

        Rediness probe must be use while starting of an application where as livness probe helps to get the app status when it is running.