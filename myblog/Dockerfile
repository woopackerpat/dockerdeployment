FROM node:17-alpine

WORKDIR /app

COPY . .

RUN npm run build

EXPOSE 3000
# required for docker desktop port mapping