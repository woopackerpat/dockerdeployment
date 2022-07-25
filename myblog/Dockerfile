FROM node:17-alpine as build

WORKDIR /app

COPY package.json .
COPY package-lock.json .

RUN npm ci --production

COPY . .

RUN npm run build

FROM nginx:1.23.1-alpine

COPY --from=build /app/build /user/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]