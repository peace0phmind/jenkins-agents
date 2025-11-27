FROM jenkins/inbound-agent:alpine as jnlp

FROM docker:cli

RUN apk -U add openjdk17-jre bash

COPY --from=jnlp /usr/local/bin/jenkins-agent /usr/local/bin/jenkins-agent
COPY --from=jnlp /usr/share/jenkins/agent.jar /usr/share/jenkins/agent.jar


ENV JENKINS_AGENT_WORKDIR=/home/jenkins/agent
RUN mkdir -p "${JENKINS_AGENT_WORKDIR}"


ENTRYPOINT ["/usr/local/bin/jenkins-agent"]
