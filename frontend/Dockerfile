FROM node:alpine as talentplus-app-build

WORKDIR /client

COPY package.json yarn.lock README.md ./

RUN yarn

COPY ./public ./public

COPY ./src ./src

ENV REACT_APP_baseAPIURL = http://talentplus-backend-service:5000
#<backend-app-service-ip>:<port>

RUN yarn build

FROM nginx:latest

LABEL maintainer=Aamir-Pinger

COPY --from=talentplus-app-build /client/build/ /usr/share/nginx/html

EXPOSE 80
