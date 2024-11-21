# Imagen base con Maven y Java preinstalados
FROM maven:3.9.5-eclipse-temurin-17 as builder

# Establecer directorio de trabajo
WORKDIR /app

# Copiar archivos del proyecto
COPY . .

# Construir la aplicación
RUN mvn clean package -DskipTests

# Imagen de producción con JRE
FROM eclipse-temurin:17-jre-jammy

# Establecer directorio de trabajo
WORKDIR /app

# Copiar el JAR generado
COPY --from=builder /app/target/*.jar app.jar

# Exponer el puerto 8080
EXPOSE 8080

# Comando para ejecutar la aplicación
ENTRYPOINT ["java", "-jar", "app.jar"]
