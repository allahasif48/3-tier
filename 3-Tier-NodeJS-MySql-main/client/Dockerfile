# client/Dockerfile
# Stage 1: Build React app
FROM node:21-alpine3.17 AS build
WORKDIR /app
COPY . .
RUN npm install
RUN npm run build

# Stage 2: Serve with Nginx
FROM nginx:1.25.3-alpine
COPY --from=build /app/public /usr/share/nginx/html

# Copy the NGINX config
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
