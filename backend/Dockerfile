# 1. Base image
FROM node:18-alpine

# 2. Working directory 
WORKDIR /app

ARG MONGODB_URI
ARG REDIS_URL

# Set them as environment variables inside the image
ENV MONGODB_URI=${MONGODB_URI}
ENV REDIS_URL=${REDIS_URL}

COPY package*.json ./ 


RUN npm install


COPY . .


EXPOSE 8002




CMD ["node", "server.js"]
