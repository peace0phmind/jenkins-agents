FROM jenkins/inbound-agent:alpine as jnlp

FROM node:16.14.2-alpine

RUN apk -U add --no-cache openjdk17-jre bash git zip

COPY --from=jnlp /usr/local/bin/jenkins-agent /usr/local/bin/jenkins-agent
COPY --from=jnlp /usr/share/jenkins/agent.jar /usr/share/jenkins/agent.jar

COPY ../bin/mc /usr/local/bin/mc

ENV JENKINS_AGENT_WORKDIR=/home/jenkins/agent
RUN mkdir -p "${JENKINS_AGENT_WORKDIR}"

ENTRYPOINT ["/usr/local/bin/jenkins-agent"]
