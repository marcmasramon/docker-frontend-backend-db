FROM node:14.21.3-alpine3.17
ENV NODE_ENV production
USER node
WORKDIR /app
COPY --chown=node:node . .
RUN npm install
CMD ["npm", "start"]
