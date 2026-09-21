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

### Hallazgos

El criterio **Average** obtuvo los valores más altos en las tres métricas evaluadas, por lo que presentó una mayor correspondencia con las categorías originales en esta ejecución.

Sin embargo, los valores de ARI y Silhouette fueron relativamente bajos, indicando que la separación de los documentos en clusters no coincide fuertemente con las categorías originales. Esto puede deberse a que diferentes categorías de noticias comparten vocabulario y características textuales similares.

El análisis de las palabras representativas de cada cluster permitió identificar grupos relacionados con diferentes temáticas del conjunto de noticias.
