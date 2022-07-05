# Base image
FROM ubuntu:20.04

# Installing prerequisite packages
RUN DEBIAN_FRONTEND="noninteractive" apt-get update && apt-get install -y tzdata keyboard-configuration
RUN apt-get -y install curl unzip groff less
# AWS CLI installation commands
RUN	curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
RUN	unzip awscliv2.zip && ./aws/install
# Kubectl
RUN curl -o kubectl https://s3.us-west-2.amazonaws.com/amazon-eks/1.22.6/2022-03-09/bin/linux/amd64/kubectl
RUN chmod +x ./kubectl 
RUN mkdir -p $HOME/bin && cp ./kubectl $HOME/bin/kubectl && export PATH=$HOME/bin:$PATH
# Eksctl
RUN curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
RUN mv /tmp/eksctl /usr/local/bin 