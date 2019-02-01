
## Question 2- In q2 namespace, create imagestream for nodejs and deploy https://github.com/sclorg/nodejs-ex 

### Solution 2- 

#### Step 1- oc login -u developer -p redhat

#### Step 2- oc new-project q2 

#### Step 3- oc get is -n openshift 
##### Ouptut
Got a docker image 172.30.1.1:5000/openshift/nodejs 

#### Step 4- oc import-image 172.30.1.1:5000/openshift/nodejs --insecure --confirm 

imagestream.image.openshift.io/nodejs imported

Name:			nodejs
Namespace:		q9
Created:		Less than a second ago
Labels:			<none>
Annotations:		openshift.io/image.dockerRepositoryCheck=2019-02-01T18:45:38Z
Docker Pull Spec:	172.30.1.1:5000/q9/nodejs
Image Lookup:		local=false
Unique Images:		1
Tags:			1

latest
  tagged from 172.30.1.1:5000/openshift/nodejs
    will use insecure HTTPS or HTTP connections

  * 172.30.1.1:5000/openshift/nodejs@sha256:218b4ab32859c402792a6f7962d68e94d59826d304742774ea40affba91f2586
      Less than a second ago

Image Name:	nodejs:latest
Docker Image:	172.30.1.1:5000/openshift/nodejs@sha256:218b4ab32859c402792a6f7962d68e94d59826d304742774ea40affba91f2586
Name:		sha256:218b4ab32859c402792a6f7962d68e94d59826d304742774ea40affba91f2586
Created:	Less than a second ago
Annotations:	image.openshift.io/dockerLayersOrder=ascending
Image Size:	180.6MB in 9 layers
Layers:		75.17MB	sha256:a02a4930cb5d36f3290eb84f4bfa30668ef2e9fe3a1fb73ec015fc58b9958b17
		9.672MB	sha256:70cd6e3d07d1e04c76ab381733edeb047304201da2e787a54169487fc50df42e
		4.746kB	sha256:223ac6fd4e5e8b913bd473593d40f0a0ab4c61122f9334e119737ddb545b1ef0
		200.4kB	sha256:dccd6afbeb2dbebdc2121a050fa7e164c8994b79229bcfe711c1adc4e4079ecd
		86.47MB	sha256:b7cd75d97ede5cba81f626711af09540fb87b6713e09cbf74807d65a3df7d3d0
		8.849MB	sha256:75b443da66961b98eef71b29cf21451176dd2b9ca60c6a7691b5f637dac99820
		2.254kB	sha256:c437a4e7c6cf04dde494e3a2be8e531c1eb6a608c0b9529f64bb2385967e2e41
		3.269kB	sha256:ef508dd1df6bf3056b5bd0c29a8f886e62150527c9ab6dad4d5e76772cd7ed39
		199.5kB	sha256:fb33488a57ad711a01e2188c9be6fdc07a7e13041032adfc94698a254e893333
Image Created:	2 weeks ago
Author:		<none>
Arch:		amd64
Entrypoint:	container-entrypoint
Command:	/bin/sh -c $STI_SCRIPTS_PATH/usage
Working Dir:	/opt/app-root/src
User:		1001
Exposes Ports:	8080/tcp
Docker Labels:	com.redhat.component=rh-nodejs8-container
		com.redhat.deployments-dir=/opt/app-root/src
		com.redhat.dev-mode=DEV_MODE:false
		com.redhat.dev-mode.port=DEBUG_PORT:5858
		description=Node.js 8 available as container is a base platform for building and running various Node.js 8 applications and frameworks. Node.js is a platform built on Chrome's JavaScript runtime for easily building fast, scalable network applications. Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient, perfect for data-intensive real-time applications that run across distributed devices.
		help=For more information visit https://github.com/sclorg/s2i-nodejs-container
		io.k8s.description=Node.js 8 available as container is a base platform for building and running various Node.js 8 applications and frameworks. Node.js is a platform built on Chrome's JavaScript runtime for easily building fast, scalable network applications. Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient, perfect for data-intensive real-time applications that run across distributed devices.
		io.k8s.display-name=Node.js 8
		io.openshift.builder-version="1f79356"
		io.openshift.expose-services=8080:http
		io.openshift.s2i.scripts-url=image:///usr/libexec/s2i
		io.openshift.tags=builder,nodejs,nodejs8
		io.s2i.scripts-url=image:///usr/libexec/s2i
		maintainer=SoftwareCollections.org <sclorg@redhat.com>
		name=centos/nodejs-8-centos7
		org.label-schema.build-date=20181205
		org.label-schema.license=GPLv2
		org.label-schema.name=CentOS Base Image
		org.label-schema.schema-version=1.0
		org.label-schema.vendor=CentOS
		summary=Platform for building and running Node.js 8 applications
		usage=s2i build <SOURCE-REPOSITORY> centos/nodejs-8-centos7:latest <APP-NAME>
		version=8
Environment:	PATH=/opt/app-root/src/node_modules/.bin/:/opt/app-root/src/.npm-global/bin/:/opt/app-root/src/bin:/opt/app-root/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
		SUMMARY=Platform for building and running Node.js 8 applications
		DESCRIPTION=Node.js 8 available as container is a base platform for building and running various Node.js 8 applications and frameworks. Node.js is a platform built on Chrome's JavaScript runtime for easily building fast, scalable network applications. Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient, perfect for data-intensive real-time applications that run across distributed devices.
		STI_SCRIPTS_URL=image:///usr/libexec/s2i
		STI_SCRIPTS_PATH=/usr/libexec/s2i
		APP_ROOT=/opt/app-root
		HOME=/opt/app-root/src
		BASH_ENV=/opt/app-root/etc/scl_enable
		ENV=/opt/app-root/etc/scl_enable
		PROMPT_COMMAND=. /opt/app-root/etc/scl_enable
		NODEJS_SCL=rh-nodejs8
		NODEJS_VERSION=8
		NPM_RUN=start
		NAME=nodejs
		NPM_CONFIG_PREFIX=/opt/app-root/src/.npm-global

#### Step 5 oc get is 

       nodejs    172.30.1.1:5000/q2/nodejs   latest    6 minutes ago

#### Step 6 oc new-app --name q2image nodejs~https://github.com/pradeepitm12/nodejs-ex 

#### Step 7 oc get all 

#### Step 8 oc get svc 

     q2image   ClusterIP   172.30.236.32   <none>        8080/TCP   1m
#### Step 9 oc expose svc/q2image 

#### Output 
     q2image   q2image-q2.192.168.42.179.nip.io             q2image    8080-tcp                 None



## Note:
I started trying by writing a Docker file in the source Code but at the every time I get ***crash reloop error***
      





