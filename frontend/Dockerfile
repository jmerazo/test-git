FROM node:14.16-alpine AS builder

WORKDIR /fronted

COPY . .
RUN npm install
RUN npm run builder

FROM nginx:1.18-alpine

WORKDIR /usr/share/nginx/html

RUN rm -rf ./*
COPY --from=builder  /fronted/dist .
EXPOSE 8080

ENTRYPOINT ["nginx", "-g", "daemon off;" ]