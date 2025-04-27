# Hadoop Docker Compose Setup

This repository contains a `docker-compose.yml` file to easily set up a multi-node Hadoop cluster using Docker.

## Services

The Docker Compose configuration defines the following Hadoop services:

*   **namenode**: The Hadoop Distributed File System (HDFS) NameNode.
    *   Web UI: [http://localhost:9870](http://localhost:9870)
    *   HDFS Port: `9000`
*   **datanode**: An HDFS DataNode.
    *   Web UI: [http://localhost:9864](http://localhost:9864)
*   **resourcemanager**: The Yet Another Resource Negotiator (YARN) ResourceManager.
    *   Web UI: [http://localhost:8088](http://localhost:8088)
*   **nodemanager**: A YARN NodeManager.
*   **historyserver**: The MapReduce Job History Server.
    *   Web UI: [http://localhost:8188](http://localhost:8188)

## Prerequisites

*   Docker: [Install Docker](https://docs.docker.com/get-docker/)
*   Docker Compose: [Install Docker Compose](https://docs.docker.com/compose/install/) (often included with Docker Desktop)

## Usage

1.  **Clone the repository (if applicable):**
    ```bash
    git clone <your-repo-url>
    cd <your-repo-directory>
    ```

2.  **Start the Hadoop Cluster:**
    Open a terminal in the directory containing the [docker-compose.yml](http://_vscodecontentref_/0) file and run:
    ```bash
    docker-compose up -d
    ```
    The `-d` flag runs the containers in detached mode (in the background). The services might take a few minutes to become fully operational, especially due to the `SERVICE_PRECONDITION` checks.

3.  **Access Services:**
    Once the containers are running and healthy, you can access the web UIs for the different services using the links provided in the Services section.

4.  **Stop the Hadoop Cluster:**
    To stop and remove the containers, network, and volumes created by Docker Compose, run:
    ```bash
    docker-compose down -v
    ```
    The `-v` flag ensures that the volumes (`hadoop_namenode`, `hadoop_datanode`, `hadoop_historyserver`) are also removed. Omit `-v` if you want to preserve the data stored in the volumes.

## Configuration

The Hadoop configuration is primarily managed through environment variables within the [docker-compose.yml](http://_vscodecontentref_/1) file. You can modify these variables to adjust settings like HDFS replication factor, memory allocation, etc.
