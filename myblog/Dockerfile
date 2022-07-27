FROM node:17-alpine as build

WORKDIR /app

COPY package.json .
COPY package-lock.json .

RUN npm ci --omit=dev

COPY . .

RUN npm run build

FROM nginx:1.23.1-alpine as prod

RUN apt-get update -y \
    && apt-get install python3-certbot-nginx -y \
    && certbot --nginx -d patcharapol.in.th -d www.patcharapol.in.th

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]