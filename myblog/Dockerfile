FROM node as build

WORKDIR /app

COPY package.json .
COPY package-lock.json .

RUN npm ci --omit=dev

COPY . .

RUN npm run build

FROM nginx:1.23.1-alpine as prod

RUN apk update
RUN apk install python3-certbot-nginx 
RUN certbot --nginx -d patcharapol.in.th -d www.patcharapol.in.th

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]