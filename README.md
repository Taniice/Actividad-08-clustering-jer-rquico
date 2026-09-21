## A. Clustering Jerárquico – 20 Newsgroups

Se aplicó **clustering jerárquico aglomerativo** sobre una muestra de **1,000 documentos** del dataset **20 Newsgroups** de Scikit-learn.

Los textos fueron transformados mediante **TF-IDF** y posteriormente reducidos a **100 componentes mediante TruncatedSVD**. Se establecieron **20 clusters**, correspondientes a las 20 categorías originales del dataset. Las categorías reales se utilizaron únicamente para evaluar los resultados.

### Criterios de Linkage evaluados

Se probaron dos criterios diferentes:

* **Ward:** busca minimizar la variación interna al fusionar grupos. Se utilizó distancia **euclidiana**.
* **Average:** utiliza la distancia promedio entre los elementos de dos grupos. Se utilizó distancia **coseno**.

### Resultados

| Modelo      | Linkage | Distancia  |        ARI |        NMI | Silhouette |
| ----------- | ------- | ---------- | ---------: | ---------: | ---------: |
| **Average** | Average | Coseno     | **0.1192** | **0.3203** | **0.0299** |
| Ward        | Ward    | Euclidiana |     0.0641 |     0.3123 |     0.0208 |

### ANALISIS

El criterio **Average** obtuvo los valores más altos en las tres métricas evaluadas, por lo que presentó una mayor correspondencia con las categorías originales en esta ejecución.

Sin embargo, los valores de ARI y Silhouette fueron relativamente bajos, indicando que la separación de los documentos en clusters no coincide fuertemente con las categorías originales. Esto puede deberse a que diferentes categorías de noticias comparten vocabulario y características textuales similares.

El análisis de las palabras representativas de cada cluster permitió identificar grupos relacionados con diferentes temáticas del conjunto de noticias.

## B. Segmentación de clientes con Clustering Jerárquico

Se generó un conjunto de **300 clientes sintéticos** utilizando `make_blobs` de Scikit-learn, con **4 segmentos**. Las variables utilizadas fueron **frecuencia de compra** y **monto de gasto**.

Se probaron tres criterios de **Linkage** utilizando clustering jerárquico aglomerativo:

* **Ward:** minimiza la variación interna al unir grupos.
* **Complete:** utiliza la mayor distancia entre elementos de dos grupos.
* **Average:** utiliza la distancia promedio entre elementos de dos grupos.

### Resultados

| Linkage      | Silhouette |
| ------------ | ---------: |
| **Ward**     | **0.7518** |
| **Complete** | **0.7518** |
| Average      |     0.7494 |

### Hallazgos

Los criterios **Ward y Complete** obtuvieron el valor más alto de Silhouette (**0.7518**), mientras que Average obtuvo **0.7494**. Los tres resultados son similares y muestran una **buena separación y cohesión de los segmentos**.

En este conjunto de datos sintético, Ward y Complete produjeron la mejor separación según Silhouette, aunque la diferencia con Average fue pequeña.

