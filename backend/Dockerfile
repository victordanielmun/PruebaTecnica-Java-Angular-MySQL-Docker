# Dockerfile para Spring Boot
FROM eclipse-temurin:17-jdk-jammy as builder

# Establecer directorio de trabajo
WORKDIR /app

# Copiar archivos del proyecto
COPY . .

# Construir la aplicación
RUN ./mvnw clean package -DskipTests

# Imagen de producción
FROM eclipse-temurin:17-jre-jammy

# Establecer directorio de trabajo
WORKDIR /app

# Copiar el JAR generado
COPY --from=builder /app/target/*.jar app.jar

# Exponer el puerto 8080
EXPOSE 8080

# Comando para ejecutar la aplicación
ENTRYPOINT ["java", "-jar", "app.jar"]