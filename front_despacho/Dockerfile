# Etapa de build
FROM node:20-alpine AS build

# Directorio de trabajo
WORKDIR /app

# Copiar dependencias
COPY package.json package-lock.json ./

# Instalar dependencias
RUN npm install

# Copiar proyecto
COPY . .

# Compilar aplicación
RUN npm run build

# Etapa final nginx
FROM nginx:1.19.0-alpine

# Copiar build generado
COPY --from=build /app/dist/ /usr/share/nginx/html

# Exponer puerto
EXPOSE 80