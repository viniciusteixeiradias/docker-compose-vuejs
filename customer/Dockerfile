# estágio de compilação
FROM node:lts-alpine as build-stage
WORKDIR /app/customer
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# estágio de produção
FROM nginx:stable-alpine as production-stage
COPY --from=build-stage /app/customer/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

# docker build -t vuejs-docker-customer .
# docker run -it -p 8080:80 --rm --name container-customer vuejs-docker-customer