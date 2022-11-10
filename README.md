# MinIO Docker Configuration

> MinIO is a High Performance Object Storage released under GNU Affero General Public License v3.0. It is API compatible with Amazon S3 cloud storage service. Use MinIO to build high performance infrastructure for machine learning, analytics and application data workloads. [MinIO](https://min.io/)

This repository contains the configuration files for running minIO in Docker containers. It is based on the [minIO](https://min.io/docs/minio/container/index.html) repository.

## Configuration

1. Set up a minIO broker

   The Docker Compose file below will run everything for you via Docker.

```yml
version: '3.8'

services:

  s3:
    image: minio/minio
    ports:
      - "9000:9000"
      - "9001:9001"
    volumes:
      - bucket:/data
    command: server --address "0.0.0.0:9000" --console-address "0.0.0.0:9001" /data

volumes:
  bucket:
```

2. Start the minIO broker

   From a directory containing the `docker-compose.yml` file created in the previous step, run this command to start all services in the correct order.

```bash
docker-compose up -d
```