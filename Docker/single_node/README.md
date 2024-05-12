# Single Node Deployment

This guide will help you set up a single node deployment of Crawlab. This setup is ideal for development and testing purposes.

## Prerequisites

- Docker installed on your machine
- Docker Compose installed on your machine

## Steps

1. **Clone the repository**

   First, you need to clone the repository that contains the Docker configuration files.

   ```bash
   git clone <repository_url>
   ```

2. **Navigate to the single node directory**

   The Docker configuration for the single node deployment is located in the `Docker/single_node` directory. Navigate to this directory.

   ```bash
   cd Docker/single_node
   ```

3. **Configure the environment variables**

   The `.env` file contains the environment variables that will be used by the Docker containers. You can modify this file to suit your needs. The `.env.defaults` file contains the default values for these variables.

   ```bash
   nano .env
   ```

4. **Start the Docker containers**

   You can start the Docker containers using Docker Compose. This will start the Crawlab and MongoDB containers.

   ```bash
   docker-compose up -d
   ```

   The `-d` flag will start the containers in detached mode, which means they will run in the background.

5. **Access the Crawlab interface**

   Once the containers are running, you can access the Crawlab interface by navigating to `http://localhost:8080` in your web browser.

## Environment Variables

Here are some of the key environment variables you can configure in the `.env` file:

- `CRAWLAB_NODE_MASTER`: Set this to `Y` to designate this node as the master node.
- `CRAWLAB_MONGO_HOST`: The hostname of the MongoDB server. In this setup, it should be set to `mongo`.
- `CRAWLAB_MONGO_PORT`: The port number of the MongoDB server. The default is `27017`.
- `CRAWLAB_MONGO_DB`: The name of the MongoDB database to use.
- `CRAWLAB_MONGO_USERNAME`: The username to use for authenticating with the MongoDB server.
- `CRAWLAB_MONGO_PASSWORD`: The password to use for authenticating with the MongoDB server.

## Persistent Data

The Docker Compose configuration is set up to persist data across container restarts. The data is stored in the following directories:

- `/var/.crawlab/master`: This directory stores Crawlab metadata.
- `/var/crawlab/master`: This directory stores Crawlab data.
- `/var/crawlab/log`: This directory stores Crawlab logs.
- `/var/crawlab/mongo/data/db`: This directory stores MongoDB data.

Please ensure these directories exist and have the appropriate permissions before starting the Docker containers.