# Usa la imagen base de Ubuntu
FROM ubuntu:latest

# Instala las dependencias necesarias
RUN apt-get update && \
    apt-get install -y python3 python3-pip python3-venv

# Establece el directorio de trabajo en /app
WORKDIR /app

# Copia el archivo requirements.txt y el script de Python en el contenedor
COPY requirements.txt requirements.txt
COPY hello.py app.py

# Crea un entorno virtual y activa el entorno virtual
RUN python3 -m venv venv
RUN . ./venv/bin/activate

# Instala las dependencias de Python en el entorno virtual
RUN ./venv/bin/pip install -r requirements.txt

# Expone el puerto 8000 para la aplicación Flask
EXPOSE 8000

# Define el comando para ejecutar la aplicación Flask
CMD ["./venv/bin/python", "app.py"]
