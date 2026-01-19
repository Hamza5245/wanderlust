# 1. Base image
FROM node:18-alpine

# 2. Working directory 
WORKDIR /app


COPY package*.json ./ 


RUN npm install


COPY . .


EXPOSE 8002




CMD ["node", "server.js"]
