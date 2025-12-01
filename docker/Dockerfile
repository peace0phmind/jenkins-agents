FROM jenkins/inbound-agent:alpine as jnlp

FROM docker:cli

RUN addgroup -g 1000 ubuntu && \
    adduser -u 1000 -h /home/jenkins/agent -G ubuntu -s /bin/sh -D ubuntu

RUN apk -U add openjdk17-jre bash zip unzip

COPY --from=jnlp /usr/local/bin/jenkins-agent /usr/local/bin/jenkins-agent
COPY --from=jnlp /usr/share/jenkins/agent.jar /usr/share/jenkins/agent.jar

COPY ../bin/mc /usr/local/bin/mc

ENV JENKINS_AGENT_WORKDIR=/home/jenkins/agent
RUN mkdir -p "${JENKINS_AGENT_WORKDIR}"

ENTRYPOINT ["/usr/local/bin/jenkins-agent"]
