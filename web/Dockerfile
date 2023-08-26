FROM node:18.10.0-alpine as build

WORKDIR /usr/src/app

RUN npm i -g @nestjs/cli@10.1.10

COPY package.json package-lock.json tsconfig.json tsconfig.build.json ./
RUN npm install

COPY src ./src

RUN npm run build

FROM node:18.10.0-alpine as runtime

RUN npm i -g @nestjs/cli@10.1.10

WORKDIR /app

COPY --from=build /usr/src/app /app

CMD ["npm", "run" ,"start:prod"]