FROM node:14-alpine
WORKDIR /usr/app
COPY ./package.json /usr/app
COPY ./yarn.lock /usr/app/
RUN yarn 
RUN yarn install 
COPY ./ /usr/app
EXPOSE 3000

CMD ["yarn","run","start"]