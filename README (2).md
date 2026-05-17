# Crisis del Estrecho de Ormuz 2026 — Dashboard interactivo

[![Python](https://img.shields.io/badge/python-3.10%2B-blue.svg)](https://www.python.org/)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.35%2B-FF4B4B.svg)](https://streamlit.io/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-FF6F00.svg)](https://www.tensorflow.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.XXXXXXX.svg)](https://doi.org/10.5281/zenodo.XXXXXXX)

Trabajo final para la asignatura **Aplicaciones Avanzadas en Inteligencia Artificial (AAIA)** del Máster Universitario en Ciencia de Datos aplicada a las Ciencias Sociales.
Los datos fueron descargados de kaggle https://www.kaggle.com/datasets/hussnainmamoon1/hormuz-shipping-crisis-2026-daily-dataset?resource=download "Hussnain Mamoon · Updated 12 days ago"
El proyecto construye un dashboard interactivo de una sola página para analizar la crisis del estrecho de Ormuz de 2026, integrando tráfico marítimo, flujos energéticos, precios del petróleo, riesgo geopolítico, decisiones de compañías navieras, banderas autorizadas por Irán y rutas alternativas por el Cabo de Buena Esperanza. El análisis combina machine learning clásico, deep learning para predicción de riesgo y procesamiento de lenguaje natural sobre noticias geopolíticas.

## Características principales

- Interfaz continua en una sola página con modo de análisis por día único o por periodo.
- Tarjetas dinámicas con indicadores marítimos, energéticos, financieros y geopolíticos.
- Mapa interactivo de Ormuz con simulación visual de barcos varados, ataques y eventos clave.
- Comparación esquemática Asia-Europa: ruta vía Suez frente a ruta alternativa vía Cabo de Buena Esperanza.
- Series temporales con tooltips, ataques y eventos clave.
- Clustering exploratorio con K-Means, DBSCAN y Agglomerative Clustering.
- **Modelo LSTM** para predicción de riesgo compuesto a 7 días.
- **Análisis NLP de titulares de GDELT** con modelo preentrenado de Hugging Face.

## Herramientas utilizadas

Este trabajo aplica cuatro herramientas relacionadas con los temas de la asignatura, además de los repositorios de publicación:

| # | Herramienta | Tema de la asignatura | Uso en el proyecto |
|---|---|---|---|
| 1 | [GitHub Copilot](https://github.com/features/copilot) | Tema 2 – Herramientas de IA generativa | Asistente de programación para acelerar el desarrollo de la app y los módulos analíticos |
| 2 | [Scikit-learn](https://scikit-learn.org/) | Tema 3 – Bibliotecas de IA (ML clásico) | Clustering exploratorio no supervisado (K-Means, DBSCAN, Agglomerative) con PCA |
| 3 | [TensorFlow / Keras](https://www.tensorflow.org/) | Tema 3 – Bibliotecas de IA (Deep Learning) | Red LSTM para predicción de riesgo compuesto a 7 días sobre serie temporal |
| 4 | [Hugging Face Transformers](https://huggingface.co/) | Tema 4 – IA en la nube | Análisis NLP multilingüe de titulares geopolíticos obtenidos vía GDELT |

Publicación y reproducibilidad (Tema 5 – Repositorios):

- Código fuente en **GitHub**: este repositorio.
- Dataset archivado con DOI académico en **Zenodo**: ver sección [Dataset](#dataset).

## Estructura del proyecto

```text
hormuz-crisis-2026/
├── app.py                      # Aplicación principal Streamlit
├── requirements.txt
├── README.md
├── LICENSE
├── CITATION.cff
├── .gitignore
├── data/
│   └── strait_of_hormuz_shipping_disruption_2026.csv
├── src/
│   ├── __init__.py
│   ├── data_loader.py
│   ├── preprocessing.py
│   ├── visualizations.py
│   ├── visualizations_dl.py
│   ├── map_simulation.py
│   ├── ml_models.py            # Clustering scikit-learn
│   ├── deep_learning_lstm.py   # Modelo LSTM Keras
│   ├── nlp_news.py             # Pipeline Hugging Face sobre GDELT
│   └── utils.py
├── outputs/
│   ├── figures/
│   └── models/
└── docs/
    ├── methodology_notes.md
    └── final_document.md
```

## Instalación

Requisitos: Python 3.10 o superior.

```bash
git clone https://github.com/USUARIO/hormuz-crisis-2026.git
cd hormuz-crisis-2026
python -m venv .venv
# Windows:
.venv\Scripts\activate
# Linux/Mac:
source .venv/bin/activate
pip install -r requirements.txt
```

## Ejecución

```bash
streamlit run app.py
```

El navegador abrirá el dashboard. Si no se abre automáticamente, entra en `http://localhost:8501`.

## Dataset

El dataset `strait_of_hormuz_shipping_disruption_2026.csv` contiene 125 observaciones diarias entre enero y mayo de 2026, con 26 variables sobre tráfico marítimo, flujos energéticos, precios, ataques, decisiones navieras y eventos clave.

El dataset es una compilación propia a partir de fuentes públicas (Wikipedia, CNN, Al Jazeera, Kpler, IMF PortWatch). Está archivado en Zenodo con DOI permanente:

> [DOI: 10.5281/zenodo.XXXXXXX](https://doi.org/10.5281/zenodo.XXXXXXX)

## Advertencias metodológicas

- Los puntos de barcos en el mapa son una simulación visual agregada, no representan posiciones AIS reales.
- Las rutas por Suez y por el Cabo de Buena Esperanza son representaciones logísticas esquemáticas.
- El clustering es exploratorio dado el tamaño limitado del dataset.
- El LSTM proyecta un riesgo compuesto, no una predicción operativa.
- El análisis de sentimiento sobre GDELT depende de la disponibilidad de resultados externos.

## Cómo citar este trabajo

Si utilizas este código o el dataset, por favor cita:

```
[APELLIDO], [Nombre] y [APELLIDO], [Nombre] (2026).
Crisis del Estrecho de Ormuz 2026: dashboard interactivo
y análisis exploratorio.
Máster Universitario en Ciencia de Datos aplicada a las
Ciencias Sociales. DOI: 10.5281/zenodo.XXXXXXX
```

Ver el archivo [`CITATION.cff`](CITATION.cff) para el formato estructurado.

## Licencia

Este proyecto se distribuye bajo licencia [MIT](LICENSE).

## Autores

- Sebastian Garcia Torres — [sfgarcia@usal.es]
- [Sebastian Cuevas] — [cuevas@usal.es]

Trabajo realizado en el marco del Máster Universitario en Ciencia de Datos aplicada a las Ciencias Sociales, Universidad de Salamanca, curso 2025-2026.
