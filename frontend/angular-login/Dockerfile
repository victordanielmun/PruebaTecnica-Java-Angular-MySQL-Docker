# Dockerfile para Angular
FROM node:18 AS builder

# Establecer directorio de trabajo
WORKDIR /app

# Copiar archivos del proyecto
COPY package*.json ./
RUN npm install

# Construir la aplicación Angular
COPY . .
RUN npm run build --prod

# Imagen de producción
FROM nginx:alpine

# Copiar los archivos de construcción al servidor NGINX
COPY --from=builder /app/dist/<nombre-de-tu-proyecto-angular> /usr/share/nginx/html

# Exponer el puerto 80
EXPOSE 80

# Iniciar NGINX
CMD ["nginx", "-g", "daemon off;"]