FROM node:20-alpine3.17

WORKDIR /usr/app

RUN npm install --global pm2

COPY package*.json ./

RUN npm install

COPY ./ ./

RUN npm run build

EXPOSE 5001

USER node

CMD [ "pm2-runtime", "npm", "--", "start" ]