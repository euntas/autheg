# autheg/autheg-frontend/Dockerfile

FROM node:9

ARG UID
RUN adduser frontend --uid $UID --disabled-password --gecos ""

ENV APP /usr/src/app
RUN mkdir $APP
WORKDIR $APP

COPY package.json yarn.lock $APP/
RUN yarn
# Gems and yarn packages are installed into the mounted volumes. 
# This will stop you from needing to rebuild the whole Docker image every time you change the Gemfile or package.json.

COPY . $APP/

CMD ["yarn", "run", "dev"]
