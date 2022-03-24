FROM node:14-alpine
WORKDIR /usr/app
COPY ./package.json /usr/app
RUN yarn install 
COPY ./ /usr/app

RUN yarn build

FROM nginx:stable-alpine
COPY --from=builder /usr/app/dist /usr/share/nginx/html
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
EXPOSE 4000

CMD ["yarn","start"]