FROM node:10 AS development

WORKDIR /usr/src/app

COPY package*.json ./

RUN npm ci

COPY . /usr/src/app/

EXPOSE 3000

CMD ["npm", "start"]

FROM development AS builder

RUN npm run build

FROM nginx:1.21.0-alpine AS server

COPY --from=builder /usr/src/app/build /usr/share/nginx/html
