FROM node:22-alpine as builder

workdir /app

copy package.json package-lock.json ./

run npm ci

copy . .

run npm run build

from nginx:alpine as runner

workdir /usr/share/nginx/html

copy --from=builder /app/dist ./

cmd ["nginx", "-g", "daemon off;"]