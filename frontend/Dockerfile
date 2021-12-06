FROM node:13-alpine as builder
WORKDIR /app
COPY ["package.json", "package-lock.json*", "./"]
RUN npm install --only=prod
COPY . .
RUN npm run build

FROM nginx:stable-alpine
EXPOSE 80
COPY --from=builder /app/build /var/www/html