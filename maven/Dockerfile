FROM jenkins/inbound-agent:alpine as jnlp

FROM maven:3.9-eclipse-temurin-17

RUN apt-get update && \
    apt-get install -y \
        git \
        libfontconfig1 \
        libfreetype6

COPY --from=jnlp /usr/local/bin/jenkins-agent /usr/local/bin/jenkins-agent
COPY --from=jnlp /usr/share/jenkins/agent.jar /usr/share/jenkins/agent.jar

ENV JENKINS_AGENT_WORKDIR=/home/jenkins/agent
RUN mkdir -p "${JENKINS_AGENT_WORKDIR}"

USER root

usermod -d /home/jenkins/agent -m ubuntu

USER ubuntu

ENTRYPOINT ["/usr/local/bin/jenkins-agent"]
