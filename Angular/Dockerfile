FROM node:lts-bookworm-slim
EXPOSE 4200

ARG APP_NAME=my-app
ARG GIT_USER='John Doe'
ARG GIT_EMAIL='john.doe@test.be'

WORKDIR /app

RUN apt-get update
RUN apt-get install -y git
RUN git config --global user.email "${GIT_EMAIL}"
RUN git config --global user.name "${GIT_USER}"
RUN git config --global init.defaultBranch main

RUN npm install -g npm
RUN npm install -g @angular/cli

# Ajout des modules complémentaire
# RUN npm i -g @lucide/angular

RUN ng analytics disable --global true
RUN ng n ${APP_NAME} --routing=true --skip-tests --style=scss --interactive=false 
WORKDIR /app/${APP_NAME}

CMD ["ng", "serve", "--host", "0.0.0.0"]