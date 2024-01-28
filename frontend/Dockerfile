FROM node:14.21.3-alpine3.17
WORKDIR /app
RUN apk add dumb-init
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["dumb-init", "npm", "start"]
