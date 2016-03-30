FROM ubuntu:14.04
ADD ProActiveWorkflowsScheduling-linux-x64-7.1.2.zip /opt/ProActiveWorkflowsScheduling-linux-x64-7.1.2.zip
RUN apt-get -y update && apt-get -y install unzip openssh-server
RUN cd /opt && unzip ProActiveWorkflowsScheduling-linux-x64-7.1.2.zip
RUN echo "proactive.useIPaddress=true" >> /opt/ProActiveWorkflowsScheduling-linux-x64-7.1.2/config/network/server.ini
EXPOSE 8080
CMD /opt/ProActiveWorkflowsScheduling-linux-x64-7.1.2/bin/proactive-server
