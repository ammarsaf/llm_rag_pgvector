# Overview
- Implementing pgVector as vector database on top of PostgreSQL, use it as retriever and pass it to LLM as RAG.

# Pre-requisite
- Docker: To pull pgvector, postgresql and pgadmin interface images from DockerHub and run it, setup vector database and serve as retriever.
- OpenAI account: To call the LLM api.
- Memory: 12GB and above. 

# Docker Setup

## Manual build container
1. docker pull pgvector image

`docker pull pgvector/pgvector:pg16`

`docker run --name pgvector-demo -e POSTGRES_PASSWORD=test -p 5432:5432 pgvector/pgvector:pg16`

2. docker pull pgadmin interface

`docker pull dpage/pgadmin4`

`docker run --name my-pgadmin -p 82:80 -e 'PGADMIN_DEFAULT_EMAIL=ammar@yahoo.com' -e 'PGADMIN_DEFAULT_PASSWORD=pass123' -d dpage/pgadmin4`

3. Login PGadmin4 thru http://localhost:82/
4. Create server group. 
5. Register server
     - Ensure to check "IP address" of `pgvector` container inspect as this is the Hostname to register server. ie `"IPAddress": "172.17.0.3",`
     - Connect to the pgvector database server.

**Source**
- https://www.commandprompt.com/education/how-to-run-postgresql-and-pgadmin-using-docker/
- https://bugbytes.io/posts/vector-databases-pgvector-and-langchain/

## Compose
1. `cd` into the project dir. Please ensure the `docker-compose.yml` is exist. 
2. Run 
```
docker-compose up
```

# Todo
* [x] Create `docker-compose.yml` to run both container at the same time easily.
* [x] Building multimodal RAG db on PGvector.

