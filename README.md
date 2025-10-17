# spark-local-env
## How to use
`docker compose up -d`
## Add Worker Node
Add below code at `docker-compose.yaml`
```YAML
  spark-worker-N:
    image: apache/spark:3.5.7
    platform: linux/amd64
    command: >
      bash -c "
        /opt/spark/sbin/start-worker.sh spark://spark-master:7077 &&
        tail -f /dev/null
      "
    environment:
      - SPARK_MODE=worker
      - SPARK_WORKER_CORES=2
      - SPARK_WORKER_MEMORY=2G
      - SPARK_WORKER_WEBUI_PORT=<PORT_NUMBER>
      - SPARK_PUBLIC_DNS=localhost
      - AWS_PROFILE=${AWS_PROFILE_NAME}
      - AWS_REGION=${AWS_REGION}
    ports:
      - "<PORT_NUMBER>:<PORT_NUMBER>"
    depends_on:
      - spark-master
    volumes:
      - ~/.aws:/root/.aws:ro
      - ./jars:/opt/spark/extra-jars
    networks:
      - spark-network
```