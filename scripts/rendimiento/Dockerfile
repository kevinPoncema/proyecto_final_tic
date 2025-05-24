# Imagen base ligera con Python
FROM python:3.10-slim

# Instalar dependencias del sistema
RUN apt update && apt install -y sysbench stress iperf3

# Establecer directorio de trabajo
WORKDIR /app

# Crear carpeta para resultados
RUN mkdir -p resultados

# Instalar dependencias de Python
RUN pip install psutil notebook jupyterlab nbconvert matplotlib

# Comando por defecto: levantar el servidor Jupyter
CMD ["jupyter", "lab", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root", "--NotebookApp.token=''"]
