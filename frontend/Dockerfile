# Stage 1: Build
FROM node:18-alpine AS build-stage
WORKDIR /app

# Environment variable define karein (Vite ke liye VITE_ prefix lazmi hai)
ARG VITE_API_URL=http://175.168.1.62:8002
ENV VITE_API_URL=$VITE_API_URL
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Stage 2: Serve with Nginx
FROM nginx:stable-alpine
COPY nginx.conf /etc/nginx/conf.d/default.conf
COPY --from=build-stage /app/dist /usr/share/nginx/html
EXPOSE 8088
CMD ["nginx", "-g", "daemon off;"]
