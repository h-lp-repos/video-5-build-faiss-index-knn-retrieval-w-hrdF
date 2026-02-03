# Video 5: Indexación con FAISS y Recuperación k-NN

## Objetivo
Indexar los embeddings generados en un índice FAISS, guardar el índice en disco y ejecutar consultas k-NN (top-5).

## Pasos

1. Cargar los embeddings y el mapeo del corpus:
   ```bash
   cat corpus.json
   ```

2. Ejecutar el script de recuperación (esto construirá el índice y lo guardará como `index.faiss`):

   ```bash
   python retrieval_integration.py \
     --embeddings ../video-3-load-sentence-transformers-notebook/embeddings.npz \
     --corpus corpus.json \
     --k 5 \
     --output knn_results.json
   ```
3. Revisar el índice y los resultados:

   ```bash
   ls index.faiss knn_results.json
   cat knn_results.json
   ```

## Solución de problemas

* **Incompatibilidad de tipo de datos (dtype)**: asegurate de que los embeddings estén en `float32` y normalizados.
* **Errores de memoria**: utilizá inserciones por chunks o un índice `IndexIVFFlat` para datasets más grandes.
