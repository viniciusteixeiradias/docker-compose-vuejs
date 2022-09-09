# estágio de compilação
FROM node:lts-alpine as build-stage
WORKDIR /app/admin
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# estágio de produção
FROM nginx:stable-alpine as production-stage
COPY --from=build-stage /app/admin/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

# docker build -t vuejs-docker-admin .
# docker run -it -p 8080:80 --rm --name container-admin vuejs-docker-admin