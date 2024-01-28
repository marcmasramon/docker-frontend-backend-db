FROM node:14.21.3-alpine3.17
RUN apk add dumb-init
WORKDIR /app
COPY . .
RUN npm install
RUN npm run build
RUN npm install -g serve
CMD ["dumb-init", "serve", "-s", "build"]
