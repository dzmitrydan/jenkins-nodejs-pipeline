FROM jenkins/jenkins:alpine

USER root

RUN apk -U add docker

RUN echo "jenkins ALL=NOPASSWD: ALL" >> /etc/sudoers

RUN apk add --update shadow \
    && groupadd -g 50 staff \
    && usermod -a -G staff jenkins