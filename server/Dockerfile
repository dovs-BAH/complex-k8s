FROM node:16-alpine

USER node

RUN mkdir -p /home/node/app
WORKDIR /home/node/app


COPY --chown=node:node ./package.json ./
RUN npm install
COPY --chown=node:node ./ ./

#Change to npm run if it doesn't work
CMD ["npm", "run", "start"]