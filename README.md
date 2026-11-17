# Deployment minimale di Spark Streaming

Questo progetto fornisce un deployment minimale di Spark con Docker Compose, che comprende uno Spark Master, uno Spark Worker e un'istanza di Jupyter Notebook.

## Struttura
- `docker-compose.yml`: definisce i servizi.
- `Dockerfile.jupyter`: immagine di Jupyter con Java 21 e PySpark alla stessa versione del cluster.
- `notebooks/spark_streaming_demo.ipynb`: notebook di demo su Spark Structured Streaming (API unificata batch/streaming, finestre tumbling e sliding, event time e watermark, modalità di output e trigger).

## Requisiti
Solo Docker con Docker Compose. Il primo build scarica le immagini (alcuni minuti).

## Come eseguire

1.  **Avviare i servizi**:
    ```bash
    docker compose up -d --build
    ```

2.  **Accedere a Jupyter Notebook**:
    - URL: [http://localhost:8888](http://localhost:8888)
    - Token: (nessun token richiesto)

3.  **Eseguire la demo**:
    - Aprire `notebooks/spark_streaming_demo.ipynb` in Jupyter.
    - Eseguire le celle in ordine per vedere i job di streaming in azione.

## Servizi
- **Spark Master**: Web UI su [http://localhost:8080](http://localhost:8080). La porta 7077 è raggiungibile solo dagli altri container.
- **Spark Worker**: si collega al Master.
- **Jupyter Notebook**: [http://localhost:8888](http://localhost:8888)

## Versione di Spark
Il progetto usa **Spark 4.3.0**, definita in un solo punto (`SPARK_VERSION` nel `docker-compose.yml`, usata sia per le immagini `apache/spark` sia per `pyspark` nel notebook: le versioni devono coincidere). Per cambiarla:
```bash
SPARK_VERSION=4.3.0 docker compose up -d --build
```

## Note
- Jupyter gira senza token né password, quindi le porte sono pubblicate solo su `127.0.0.1`.
- Per fermare tutto: `docker compose down`.
- Il worker non include Python: il notebook usa solo funzioni built-in di Spark. Per usare UDF Python serve un worker con la stessa versione di Python del notebook.
