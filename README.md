# Mapeo de inundaciones con Sentinel-1 mediante U-Net (Sen1Floods11)

Examen parcial de *Redes Neuronales y Aprendizaje Profundo* (UNI FIIS, 2026-II) · Pregunta 2.
Segmentación de agua de inundación píxel a píxel a partir de las bandas SAR VV y VH, con estudio de
ablación, evaluación en distribución, generalización a Bolivia, análisis de fallos del SAR y un bono de fusión con Sentinel-2.

**Integrantes:** _(completar: 5 integrantes con apellidos, nombres y código)_

## Contenido
| Carpeta | Descripción |
|---|---|
| `notebooks/Pregunta2_UNet_Sen1Floods11_v2.ipynb` | Notebook reproducible (Google Colab): descarga, entrenamiento, ablación, evaluación, análisis y bono |
| `notebooks/Pregunta2_ejecutado_con_salidas.ipynb` | Versión ejecutada, con las salidas de la corrida reportada |
| `report/` | Informe  PDF|
| `results/` | Resumen de resultados; aquí se colocan los CSV y figuras generados |

## Cómo reproducir
1. Abrir el notebook en Google Colab (`Archivo > Abrir cuaderno > GitHub`) y activar GPU
   (`Entorno de ejecución > Cambiar tipo de entorno de ejecución`).
2. Con `FAST_MODE = True` se hace una prueba rápida (minutos). Para la corrida completa usar `FAST_MODE = False` y ejecutar todas las celdas.
3. Los datos se descargan automáticamente por HTTPS desde el bucket público `sen1floods11` (v1.1); no se requiere autenticación.
   Espacio aproximado: 6 GB (chips dorados, S2 y 1500 chips débiles).
4. Los resultados se guardan en `/content/outputs` y la última celda los empaqueta en un `.zip`.

Tiempo de referencia (GPU de Colab): la ablación completa (8 configuraciones, 1500 pasos cada una) tomó unos 32 minutos.
Para ejecutar localmente: `pip install -r requirements.txt` y abrir el notebook con Jupyter (se necesita GPU para tiempos razonables).

## Diseño experimental (resumen)
- **Modelo:** U-Net implementada desde cero (sin bibliotecas de segmentación y sin pesos preentrenados), con opciones de profundidad, compuertas de atención y conexiones de salto.
- **Partición:** la oficial del dataset; los CSV de train/valid/test no incluyen Bolivia, que se reserva como test geográfico. Los chips débiles de Bolivia se excluyen.
- **Selección:** el modelo final y el umbral de decisión se eligen solo con validación.
- **Semilla:** una sola (0); ver limitaciones en el informe.

## Resultados principales
Ver `results/resultados_resumen.md` y `report/Informe_Pregunta2.pdf`.
En test (eventos vistos) el IoU del agua es 0.670; en Bolivia, 0.593.

## Referencia del dataset
Bonafilia, D., Tellman, B., Anderson, T., & Issenberg, E. (2020). *Sen1Floods11: a georeferenced dataset to train and test deep learning flood algorithms for Sentinel-1.* CVPR Workshops, 210–211. https://github.com/cloudtostreet/Sen1Floods11
