# Imagen base
FROM golang as builder

# Establecer un directorio de trabajo
WORKDIR /app

# Agregar el código fuente al contenedor
COPY ./src/main.go .

RUN CGO_ENABLED=0 GOOS=linux GOPROXY=http://proxy.golang/org go build -o app ./main.go


FROM alpine:latest

# Exponer el puerto por el cual la aplicación será accesible
EXPOSE 8080

# Compilar la aplicación
COPY --from=builder /app/app .


# Comando para iniciar la aplicación
CMD ["./app"]