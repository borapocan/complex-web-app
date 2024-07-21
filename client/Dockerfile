FROM node:16-alpine as builder

WORKDIR '/app'
#WORKDIR '/home/node/app'

COPY ./package.json ./
#COPY --chown=node:node ./package.json ./

RUN npm install

#COPY --chown=node:node ./ ./
COPY ./ ./

RUN npm run build

FROM nginx

EXPOSE 3000

COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

COPY --from=builder /app/build /usr/share/nginx/html
#COPY --from=builder /home/node/app/build /usr/share/nginx/html
