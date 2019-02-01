FROM registry.access.redhat.com/rhscl/nodejs-6-rhel7
EXPOSE 8080
RUN mkdir -p /opt/app-root/ && \
    chgrp -R 0 /opt/app-root/ && \
    chmod -R g=u /opt/app-root/
WORKDIR /opt/app-root
ONBUILD COPY package.json /opt/app-root
ONBUILD RUN npm install
ONBUILD COPY /home/pradeepkumar/git/nodejs-ex /opt/app-root
CMD [ "npm", "start" ]