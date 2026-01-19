# Stage 1: Build
FROM node:18-alpine AS build-stage
WORKDIR /app

# Sahi spelling: VITE_API_PATH
ARG VITE_API_PATH
ENV VITE_API_PATH=$VITE_API_PATH

COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Stage 2: Serve with Nginx
FROM nginx:stable-alpine
COPY nginx.conf /etc/nginx/conf.d/default.conf
COPY --from=build-stage /app/dist /usr/share/nginx/html

# Nginx default port 80 use karta hai, 
# lekin humne bahar 8088 map kiya hai, isliye 80 hi rehne dein
EXPOSE 80 
CMD ["nginx", "-g", "daemon off;"]
