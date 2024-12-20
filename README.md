# Kafka Event Listener Project

This project demonstrates the use of Apache Kafka for real-time data transition between a server and a data source. It simulates a real-life data pipeline using Docker containers for both Apache Kafka and MinIO S3 bucket.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Setup](#setup)
- [Usage](#usage)
- [Configuration](#configuration)
- [Contributing](#contributing)
- [License](#license)

## Introduction

This Kafka Event Listener project aims to replicate real-life data transitions between a server and a data source using Apache Kafka running on Docker. Additionally, it mimics an AWS S3-like data pipeline using MinIO S3 bucket, also running on Docker.

## Features

- Real-time data transition simulation
- Apache Kafka setup on Docker
- MinIO S3 bucket setup on Docker
- Seamless data pipeline integration

## Setup

I suggest the file structure to be like this:

    my-kafka-project/
    │
    ├──> minio-server
    │    ├── .env
    │    └── docker-compose-minio.yaml
    ├──> kafka-files
        ├── KafkaConsumer.ipynb
        ├── KafkaProducer.ipynb
        ├── netflix_dataset.csv
        └── docker-compose.yaml
To set up this project, follow these steps:

1. **Clone the repository:**
    ```bash
    git clone https://github.com/waltzofflowers/kafka_trying.git
    cd kafka-event-listener
    ```

2. **Start Docker Kafka containers:**

    ```bash
    docker-compose up -d
    ```

3. **Start Docker Minio Container containers:**

You may need different file location for Minio Server.That way you can use it on other projects as well.Go to the file path you want to install Minio. 
    
Also try to move docker-compose-minio.yaml and .env files all together to new file location. That way you can set your user password credentials.
    
Execute this command below.


    docker-compose-minio up -d

You can manage docker containers using.

    docker ps

Also you need to be aware of all of the containers that is not running on docker at that moment. This way you will not have duplicate containers as well. Use code below to chekc that out.
   
    docker ps -a

## Usage

Close the ipynb files before starting the minio webserver. Because either producer or consumer wont finish off causing webserver wont open up.

1. **Producing messages to Kafka:**

Open KafkaProducer.ipynb try to execute it cell to cell. Try to use google it required ones i put little few there.Try to execute the producer and consumers last execution together.

2. **Running the Kafka Consumer:**

Do the same thing for KafkaConsumer as well.

3. **Accessing MinIO S3 bucket:**

You can access the MinIO S3 bucket using the following URL: `http://localhost:9000`
    
Default credentials: # You can create that credentials in webserver. But if you dont wanna mess with that. Use username and password you set at .env file as a access_key and secret_key it will accept it as a valid credential.

    - **Access Key:** `minio`
    - **Secret Key:** `minio123`

4. **Offset Explorer**

You can check out kafka status and data with it. Deleting everything in it doesnt also deletes topic. So clearing the data with offset explorer is wise choice. Since we are using it on a pc without any limitation data isnt lost throughout the process.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any improvements or bug fixes.


So gonna finish up with few words over here. It is wise to delete kafka_output.csv in a filepath and on S3 server as well just to work with code properly. Also stating up above as well try to delete partitions and whats getting written in there to avoid conflict in kafka as well.