# Spark Streaming Minimal Deployment

This project provides a minimal Spark deployment using Docker Compose, including a Spark Master, a Spark Worker, and a Jupyter Notebook instance.

## Structure
- `docker-compose.yml`: Defines the services.
- `notebooks/spark_streaming_demo.ipynb`: A demo notebook using Spark Structured Streaming.

## How to Run

1.  **Start the services**:
    ```bash
    docker-compose up -d
    ```

2.  **Access Jupyter Notebook**:
    - URL: [http://localhost:8889](http://localhost:8889)
    - Token: (No token required)

3.  **Run the Demo**:
    - Open `notebooks/spark_streaming_demo.ipynb` in Jupyter.
    - Run the cells to see the streaming job in action.

## Services
- **Spark Master**: [http://localhost:8080](http://localhost:8080)
- **Spark Worker**: Connects to Master.
- **Jupyter Notebook**: [http://localhost:8888](http://localhost:8888)
