# Cuadernos exportados a HTML

Versiones estáticas de los cuadernos Jupyter del TFM, navegables desde cualquier navegador sin necesidad de instalar Python ni Jupyter.

## Cómo acceder

Abre `index.html` en el navegador. Desde ahí puedes navegar a cualquier cuaderno.

## Ficheros

| Fichero | Cuaderno | Contenido |
|---------|----------|-----------|
| `01_EDA.html` | Análisis Exploratorio de Datos | Exploración de la red viaria de Barcelona: disponibilidad y cobertura de los sensores de tráfico (2021–2024), patrones horarios y semanales del factor de referencia, distribución geográfica de los tramos, eventos culturales, meteorología y accidentalidad. Incluye 20 gráficos. |
| `02_dataset_integration.html` | Integración del Dataset | Proceso de carga y unificación de las fuentes de datos: ficheros ITINERARIS mensuales del Ajuntament de Barcelona, agenda de eventos, datos meteorológicos de AEMET y grafo vial. Genera el dataset integrado horario. |
| `03_feature_engineering.html` | Feature Engineering | Construcción del conjunto de variables predictoras: codificación cíclica de hora y día, lags temporales (1h, 2h, 3h, 6h, 12h, 24h, 48h, 168h), medias móviles, interacciones evento × hora, variables de calendario y distancias geográficas a puntos de interés. |
| `04_modeling.html` | Modelado Base | Entrenamiento del primer modelo LightGBM con partición train/val/test (2021–2022 / 2023 / 2024). Evaluación global con MAE, RMSE y R². Análisis de importancia de features con valores SHAP. Línea base del proyecto. |
| `05_mejoras_meteo_geo.html` | Mejoras: Meteorología y Geografía | Incorporación de datos meteorológicos horarios de AEMET por estación (temperatura, precipitación, viento), distancias a recintos de eventos y variables de sensor de tráfico. Comparativa de modelos antes y después de las mejoras. |
| `06_optimizacion_eventos.html` | Optimización: Features Dinámicas de Eventos | Justificación y construcción de features de proximidad horaria a recintos de alta afluencia: Camp Nou y Estadio Olímpic (83 partidos FCB, 2021–2024) y Palau Sant Jordi / Estadi Olímpic (260 conciertos). Comparativa de tres modelos (M1 base, M2 +partidos, M3 +conciertos). |

## Regenerar

Para actualizar un fichero tras re-ejecutar el cuaderno correspondiente:

```bash
.venv/Scripts/jupyter nbconvert --to html notebooks/<nombre>.ipynb --output-dir notebooks/html
```

Para regenerar todos de una vez:

```bash
for nb in 01_EDA 02_dataset_integration 03_feature_engineering 04_modeling 05_mejoras_meteo_geo 06_optimizacion_eventos; do
    .venv/Scripts/jupyter nbconvert --to html notebooks/${nb}.ipynb --output-dir notebooks/html
done
```
