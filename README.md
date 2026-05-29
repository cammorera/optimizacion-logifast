# 🚛 LogiFast CR — Optimización Cross Docking

Aplicación web para resolver el problema de optimización de un **centro de distribución Cross Docking** usando Programación Entera Mixta (MIP).

**Universidad de Costa Rica · Ingeniería Industrial · I Semestre 2026**

---

## 📋 Descripción

LogiFast CR opera un centro de distribución tipo cross docking en el Valle Central de Costa Rica. Esta aplicación resuelve el problema de secuenciación óptima de camiones de entrada y salida para **minimizar el tiempo total de operación (makespan)**.

### El Problema
- **5 camiones de entrada** (proveedores)
- **3 camiones de salida** (clientes)
- **8 tipos de productos**
- 1 muelle de entrada, 1 muelle de salida, almacenamiento temporal disponible

### Modelo Matemático
El modelo MIP incluye:
- **Variables continuas:** unidades transferidas x[i,j,k], tiempos de llegada/salida
- **Variables binarias:** orden de precedencia entre camiones, indicadores de transferencia
- **13 restricciones** que modelan balance de flujo, secuenciación y enlace entrada-salida
- **Función objetivo:** minimizar el makespan C

---

## 🗂️ Estructura del Repositorio

```
logifast-crossdocking/
│
├── app.py              # Aplicación principal Streamlit (interfaz)
├── solver.py           # Modelo MIP con PuLP (lógica de optimización)
├── requirements.txt    # Dependencias del proyecto
├── README.md           # Este archivo
│
├── data/
│   └── TS5.txt         # Datos de operación del caso
│
└── utils/
    ├── __init__.py     # Exportaciones del módulo
    └── parser.py       # Lectura y validación del formato TS
```

---

## 🚀 Ejecución Local

### 1. Clonar el repositorio

```bash
git clone https://github.com/TU_USUARIO/logifast-crossdocking.git
cd logifast-crossdocking
```

### 2. Crear entorno virtual (recomendado)

```bash
python -m venv venv
source venv/bin/activate        # Linux/Mac
venv\Scripts\activate           # Windows
```

### 3. Instalar dependencias

```bash
pip install -r requirements.txt
```

### 4. Ejecutar la aplicación

```bash
streamlit run app.py
```

La aplicación abrirá automáticamente en `http://localhost:8501`.

---

## ☁️ Despliegue en Streamlit Cloud

1. Suba el repositorio a GitHub (público o privado).
2. Ingrese a [share.streamlit.io](https://share.streamlit.io).
3. Haga clic en **New app**.
4. Seleccione su repositorio y la rama `main`.
5. En **Main file path** ingrese: `app.py`
6. Haga clic en **Deploy**.

Streamlit Cloud instala automáticamente las dependencias del `requirements.txt`.

---

## 📊 Funcionalidades de la App

| Sección | Descripción |
|---|---|
| 📋 Caso & Modelo | Descripción del problema y modelo matemático completo |
| 📊 Datos de Entrada | Matrices de oferta/demanda y balance por producto |
| 🔍 Solución Óptima | Secuencias, makespan, tabla de transferencias |
| 📈 Visualizaciones | Diagrama de Gantt, mapa de calor, gráficos de flujo |
| 📝 Conclusiones | Interpretación operativa y recomendaciones |

---

## ⚙️ Parámetros Configurables

Desde la barra lateral puede ajustar:

| Parámetro | Valor por defecto | Descripción |
|---|---|---|
| Tiempo por unidad | 1 min | Tiempo de carga/descarga por unidad |
| Tiempo traslado interno | 5 min | Traslado por lote entre muelles |
| Tiempo cambio de camión | 10 min | Preparación entre camiones consecutivos |
| Límite de tiempo solver | 120 seg | Tiempo máximo para el solver CBC |

---

## 🧮 Tecnologías

- **Python 3.10+**
- **Streamlit** — Interfaz web
- **PuLP + CBC** — Solver MIP de código abierto
- **Pandas** — Manipulación de datos
- **Plotly** — Visualizaciones interactivas

---

## 📄 Formato del Archivo TS

```
i  <num_camiones_entrada>   o  <num_camiones_salida>   n  <num_productos>
r  <id_camion>  <id_producto>  <cantidad>
s  <id_camion>  <id_producto>  <cantidad>
```

**Ejemplo:**
```
r 2 1 6    → Camión de entrada 2, producto 1, cantidad 6
s 1 2 12   → Camión de salida 1, producto 2, cantidad 12
```

---

## 📜 Licencia

Uso académico — Universidad de Costa Rica, I Semestre 2026.
