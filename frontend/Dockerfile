FROM node:14.21.3-alpine3.17 AS build
RUN apk add dumb-init
WORKDIR /app
COPY package.json package-lock.json /app
RUN npm install
COPY /public /app/public
COPY /src /app/src
RUN npm run build

FROM node:14.21.3-alpine3.17
RUN npm install -g serve
ENV NODE_ENV production
COPY --from=build /usr/bin/dumb-init /usr/bin/dumb-init
USER node
WORKDIR /app
COPY --chown=node:node --from=build /app/build /app/build
CMD ["dumb-init", "serve", "-s", "build"]
