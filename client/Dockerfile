FROM node:16-alpine AS builder

USER node

RUN mkdir -p /home/node/app
WORKDIR /home/node/app


COPY --chown=node:node ./package.json ./
RUN npm install
COPY --chown=node:node ./ ./
RUN npm run build

FROM nginx
EXPOSE 3000
# if needed add
# --chown=node:node
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html

CMD ["npm", "start"]

