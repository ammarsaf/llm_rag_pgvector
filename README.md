# Overview
- Implementing pgVector as vector database on top of PostgreSQL, use it as retriever and pass it to LLM as RAG.

# Pre-requisite
- Docker: To pull pgvector, postgresql and pgadmin interface images from DockerHub and run it, setup vector database and serve as retriever.
- OpenAI account: To call the LLM api.
- Memory: 12GB and above. 

# Docker Setup

## Compose
1. `cd` into the project dir. Please ensure the `docker-compose.yml` is exist. 
2. Run 
```
docker-compose up
```
3. Login PGadmin4 thru http://localhost:82/
4. Create server group. 
5. Register server
     - Ensure to check "IP address" of `pgvector` container inspect as this is the Hostname to register server. ie `"IPAddress": "172.17.0.3",`
     - Connect to the pgvector database server.

# Source
- https://medium.com/@vishal.sharma./run-postgresql-and-pgadmin-using-docker-compose-34120618bcf9
- https://www.commandprompt.com/education/how-to-run-postgresql-and-pgadmin-using-docker/
- https://bugbytes.io/posts/vector-databases-pgvector-and-langchain/

# Todo
* [x] Create `docker-compose.yml` to run both container at the same time easily.
* [x] Building multimodal RAG db on PGvector.

