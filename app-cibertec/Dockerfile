# Etapa de construcción
FROM node:14 as build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build --prod

# Etapa de ejecución
FROM nginx:alpine
COPY --from=build /app/dist/app-cibertec /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
