# 📊 Comparativa de Rendimiento: Docker vs VM

Este proyecto tiene como objetivo **comparar el rendimiento de un entorno Docker y una máquina virtual (VM) ejecutando la misma carga de trabajo simulada**, con el fin de evaluar diferencias en **tiempo de ejecución** y **uso de recursos del sistema**. Se centra en pruebas de rendimiento mediante operaciones CRUD masivas sobre una base de datos MySQL, utilizando datos aleatorios generados con la librería `Faker`.

---

## 🎯 Propósito del Proyecto

El propósito principal es medir y contrastar:

- ⏱️ **Tiempo de ejecución**: cuánto tarda en ejecutar una operación intensa de carga.
- 💾 **Uso de recursos**: consumo de CPU y memoria durante la ejecución.
- 📈 **Capacidad de respuesta**: observar cómo responde el entorno ante tareas masivas como la inserción de 1000 registros en una base de datos.

Estas pruebas ayudan a determinar **qué entorno (Docker o VM) es más eficiente** en escenarios reales de alta demanda.

---

## 📂 Estructura del Proyecto

```
📁 proyecto-rendimiento
├── prueba_mysql_rendimiento.py        # Script principal para generar y medir operaciones CRUD
├── medir_tiempo_docker_vm.py          # Script que mide tiempo de arranque de Docker y VM
├── Dockerfile                         # Imagen Docker con todas las dependencias necesarias
├── requirements.txt                   # Lista de librerías de Python necesarias
├── resultados/
│   └── tiempos_arranque.txt           # Archivo generado con tiempos medidos
├── evidencia/
│   ├── docker_captura/                # Capturas de pantalla de pruebas en Docker
│   └── vm_captura/                    # Capturas de pantalla de pruebas en VM
```

---

## ⚙️ Scripts y su Función

### 🔧 `prueba_mysql_rendimiento.py`
Este script realiza una **prueba de rendimiento masiva** sobre una base de datos MySQL conectada (ya sea en Docker o VM). Ejecuta:

- Inserción masiva de 1000 registros (usando datos falsos con Faker).
- Consulta de todos los registros.
- Actualización de múltiples registros.
- Eliminación masiva.

🧪 También mide el uso de recursos con `psutil` (CPU y memoria) y tiempo de cada operación.

---

### ⏱️ `medir_tiempo_docker_vm.py`
Script que:

- Ejecuta un contenedor Docker temporal y mide cuánto tarda en arrancar.
- Inicia una VM en VirtualBox y espera que esté lista (verificando el puerto 22).
- Registra los tiempos de inicio en `resultados/tiempos_arranque.txt`.

---

### 🐳 `Dockerfile`
Contiene las instrucciones para construir una imagen Docker que ya incluye:

- Python
- `mysql-connector-python`
- `Faker`
- `psutil`

Permite ejecutar el test de rendimiento directamente dentro de un contenedor aislado.

---

## 📚 Librerías Utilizadas

| Librería           | Función                                                                 |
|--------------------|-------------------------------------------------------------------------|
| `Faker`            | Generación de datos falsos (nombres, correos, direcciones)              |
| `mysql-connector`  | Conexión a bases de datos MySQL desde Python                            |
| `psutil`           | Medición del consumo de CPU y memoria en tiempo real                    |
| `subprocess`       | Ejecución de comandos externos (Docker y VBoxManage)                    |
| `socket`           | Verificación de red para detectar si la VM está lista (puerto 22)       |
| `time`             | Medición de tiempos de ejecución de cada proceso                        |
| `os`               | Creación automática de carpetas y manipulación de archivos              |

---

## 📁 Carpeta de Evidencia

```
📁 evidencia/
├── docker_captura/   # Capturas de las pruebas en entorno Docker
└── vm_captura/       # Capturas de las pruebas en entorno VirtualBox (VM)
```

Cada subcarpeta contiene capturas de pantalla que **sirven como evidencia visual** del proceso de ejecución, utilizadas en el informe final. Muestran:

- Inicio del entorno
- Ejecución de los scripts
- Resultados en consola
- Uso de recursos medido

---

## 🚀 Cómo ejecutar el proyecto

### Paso 1: Instalar dependencias
```bash
pip install -r requirements.txt
```

### Paso 2: Ejecutar prueba de rendimiento
```bash
python prueba_mysql_rendimiento.py
```

### Paso 3: Medir arranque de Docker y VM
```bash
python medir_tiempo_docker_vm.py
```

---

## 📝 Conclusión

Este proyecto proporciona una base práctica para comparar de forma objetiva la eficiencia entre entornos virtualizados con Docker y máquinas virtuales tradicionales. La evidencia recopilada (tiempos + uso de recursos) se puede usar para decidir qué entorno es más conveniente según el caso de uso.

---
