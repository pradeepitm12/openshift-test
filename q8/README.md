## Question 8 - Find template named cakephp-mysql-persistent and deploy it and export the yamls 

## Solution 8-

Step 1- Search and store the template file in local 

        https://github.com/pradeepitm12/cakephp-ex
Step 2- Create a new project
        oc new-project q8

Step 3- Create the app directly from the template file 

        oc new-app openshift/templates/cakephp-mysql-persistent.json -p SOURCE_REPOSITORY_URL=https://github.com/pradeepitm12/cakephp-ex

Step 4- To get all the resource 

        oc get deploymentconfig.apps.openshift.io/mysql -o yaml --export >deployment-mysql.yaml
        oc get deploymentconfig.apps.openshift.io/cakephp-mysql-persistent -o yaml --export >deployment-cakephp.yaml

        oc get imagestream.image.openshift.io/cakephp-mysql-persistent -o yaml --export >image.yaml

        oc get replicationcontroller/cakephp-mysql-persistent-1 -o yaml --export >repl-cakephp.yaml
        oc get replicationcontroller/mysql-1 -o yaml --export >repl-mysql.yaml
        
