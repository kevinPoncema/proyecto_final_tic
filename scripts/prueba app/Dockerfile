# Imagen base ligera con Python
FROM python:3.10-slim

# Establecer el directorio de trabajo
WORKDIR /app

# Copiar el notebook al contenedor


# Instalar dependencias necesarias del sistema
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        gcc \
        default-libmysqlclient-dev \
        libssl-dev \
        libffi-dev \
        build-essential \
        curl \
        sysbench \
        stress \
        iperf3 && \
    pip install --no-cache-dir \
        mysql-connector-python \
        faker \
        psutil \
        notebook \
        jupyterlab \
        nbconvert \
        matplotlib && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Crear carpeta para resultados (por si es necesario)
RUN mkdir -p resultados

# Comando por defecto: levantar el servidor Jupyter
CMD ["jupyter", "lab", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root", "--NotebookApp.token=''"]
