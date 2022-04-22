# Build front
FROM node AS builder
WORKDIR /app/
COPY . /app/
RUN npm install && npm run build

# Nginx
FROM nginx
WORKDIR /usr/share/nginx/html

RUN rm -rf ./*

COPY --from=builder /app /usr/share/nginx/html

RUN rm -rf /etc/nginx/conf.d/default.conf
RUN rm -rf /etc/nginx/conf.d/example_ssl.conf