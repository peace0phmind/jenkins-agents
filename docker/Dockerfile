FROM jenkins/inbound-agent:alpine as jnlp

FROM docker:cli

RUN apk -U add openjdk17-jre bash

COPY --from=jnlp /usr/local/bin/jenkins-agent /usr/local/bin/jenkins-agent
COPY --from=jnlp /usr/share/jenkins/agent.jar /usr/share/jenkins/agent.jar


ARG AGENT_WORKDIR=/home/jenkins/agent

ENV LANG='en_US.UTF-8' LANGUAGE='en_US:en' LC_ALL='en_US.UTF-8'
ENV TZ=Etc/UTC

ENV AGENT_WORKDIR="${AGENT_WORKDIR}"
RUN mkdir -p /home/jenkins/.jenkins && mkdir -p "${AGENT_WORKDIR}"

VOLUME /home/jenkins/.jenkins
VOLUME "${AGENT_WORKDIR}"
WORKDIR /home/jenkins


ENTRYPOINT ["/usr/local/bin/jenkins-agent"]
