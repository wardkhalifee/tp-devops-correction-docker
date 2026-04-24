FROM node:18 AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

FROM httpd:2.4
COPY --from=build /app/dist/ /usr/local/apache2/htdocs/
COPY ../http-server/my-httpd.conf /usr/local/apache2/conf/httpd.conf