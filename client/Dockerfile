FROM node:alpine as builder

WORKDIR /app

COPY package.json .
RUN npm install
RUN npm i --save-dev chalk@2.4.2 ansi-styles@3.2.1
COPY . . 
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html