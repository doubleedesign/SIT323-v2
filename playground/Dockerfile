FROM node:18-alpine3.17 as build
WORKDIR /playground
COPY . /playground
RUN npm install
RUN npm run build

FROM ubuntu
RUN apt-get update
RUN apt-get install nginx -y
COPY --from=build /playground/dist /var/www/html/
EXPOSE 3000
CMD ["nginx","-g","daemon off;"]
