FROM node:14-alpine
WORKDIR /app
RUN apk add dumb-init
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["dumb-init", "npm", "start"]