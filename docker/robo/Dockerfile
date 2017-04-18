FROM infra:latest
MAINTAINER Ahmet Atalay

ENV HOME /home/hubot
WORKDIR /home/hubot
RUN npm install -g yo generator-hubot

USER hubot

ENV HUBOT_NAME robo
ENV HUBOT_OWNER robo
ENV HUBOT_DESCRIPTION hubot in mattermost

RUN echo no | yo hubot --adapter=mattermost --name=$HUBOT_NAME --owner=$HUBOT_OWNER --description=$HUBOT_DESCRIPTION && \
sed -i /heroku/d ./external-scripts.json

ENV MATTERMOST_ENDPOINT /robo/incoming
ENV MATTERMOST_TOKEN <MATTERMOST_OUTGOING_TOKEN>
ENV MATTERMOST_INCOME_URL <MATTERMOST_INCOMING_URL>

ENV HUBOT_AUTH_ADMIN 1

#Redis Url must be your external url. It can be a public ip or localhost or private ip!
ENV REDIS_URL redis://<Your-External-Url>:6379

EXPOSE 8080
ENTRYPOINT ["bin/hubot"]
CMD ["-a", "mattermost"]
