FROM node:14-alpine as builder
WORKDIR /usr/app
COPY ./package.json /usr/app
COPY ./yarn.lock /usr/app
RUN yarn
RUN yarn install 
COPY ./ /usr/app

RUN yarn build

FROM nginx:1.17.8-alpine

COPY --from=build /usr/app/build /usr/share/nginx/html

RUN rm /etc/nginx/conf.d/default.conf

COPY nginx/nginx.conf /etc/nginx/conf.d

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]