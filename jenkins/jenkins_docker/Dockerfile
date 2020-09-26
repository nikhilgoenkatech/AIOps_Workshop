FROM jenkins/jenkins:lts 

MAINTAINER Nikhil Goenka "dynatraceone@dynatrace.com"
USER root 
# Update aptitude with new repo
RUN apt-get update && \
    apt-get -y install apt-transport-https \
     ca-certificates \
     curl \
     gnupg2 \
     software-properties-common && \
     curl -fsSL https://download.docker.com/linux/$(. /etc/os-release; echo "$ID")/gpg > /tmp/dkey; apt-key add /tmp/dkey && \
     add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/$(. /etc/os-release; echo "$ID") \
   $(lsb_release -cs) \
   stable" && \
   apt-get update && \
   apt-get -y install python-pip && \
   pip install requests && \
   apt-get -y install docker-ce

# give jenkins docker rights
RUN usermod -aG docker jenkins
