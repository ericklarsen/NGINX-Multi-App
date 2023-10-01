FROM node:20-alpine3.17

WORKDIR /usr/app

RUN npm install --global pm2

COPY package.json ./

# RUN npm cache clear --force

RUN npm config set fetch-retries 5
RUN npm config set fetch-retry-mintimeout 600000
RUN npm config set fetch-retry-maxtimeout 1200000
RUN npm config set fetch-timeout 1800000

RUN npm config set registry http://registry.npmjs.org/

RUN npm install

COPY ./ ./

RUN npm run build

USER node

CMD ["node", "-r","dotenv/config", "build"]