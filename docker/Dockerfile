

# 1er error identificado, no es una buena práctica usar la etiqueta "latest" para la imagen base, ya que puede causar problemas de compatibilidad en el futuro. Es mejor especificar una versión específica de Node.js, como "node:18-alpine".
FROM node:18-alpine

# Establece el directorio de trabajo
WORKDIR /app

# 2do error identificado, es mejor copiar solo los archivos necesarios para instalar las dependencias primero, como package.json y package-lock.json, en lugar de copiar todo el código fuente de inmediato. Esto permite aprovechar la caché de Docker para las capas de instalación de dependencias.  
COPY package*.json ./

# 3er error identificado es que se está instalando todas las dependencias, incluyendo las de desarrollo, lo cual no es necesario para ejecutar la aplicación en producción. Es mejor usar "npm install --only=production" para instalar solo las dependencias necesarias para ejecutar la aplicación. 
RUN npm install --only=production

# Copia el resto del código fuente
COPY . .

# 4to error identificado, el puerto expuesto en la aplicación es el 3000, pero en el Dockerfile se está exponiendo el puerto 80. Es importante asegurarse de que el puerto expuesto en el Dockerfile coincida con el puerto que la aplicación está utilizando para escuchar las solicitudes. En este caso, se debe cambiar "EXPOSE 80" a "EXPOSE 3000
EXPOSE 3000

# Comando para iniciar la aplicación
CMD ["node", "src/app.js"]