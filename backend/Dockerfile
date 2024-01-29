FROM node:10.24.1-alpine3.11 AS build
RUN apk add dumb-init
WORKDIR /app
COPY package.json package-lock.json /app
RUN npm install

FROM node:10.24.1-alpine3.11
ENV NODE_ENV production
COPY --from=build /usr/bin/dumb-init /usr/bin/dumb-init
USER node
WORKDIR /app
COPY --chown=node:node --from=build /app/node_modules /app/node_modules
COPY --chown=node:node /models /app/models
COPY --chown=node:node /routes /app/routes
COPY --chown=node:node server.js /app
CMD ["dumb-init", "node", "server.js"]
