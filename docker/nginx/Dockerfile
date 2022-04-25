# Build front
FROM node AS builder
WORKDIR /app/

COPY package*.json /app/

RUN npm install

COPY . /app/
RUN npm run build

# Nginx
FROM nginx
WORKDIR /usr/share/nginx/html

RUN rm -rf ./*

COPY --from=builder /app/dist/ .

RUN rm -rf /etc/nginx/conf.d/default.conf
RUN rm -rf /etc/nginx/conf.d/example_ssl.conf