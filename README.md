# Kafka Streaming Pipeline

This project builds an event-driven streaming pipeline to analyze bank customer data in real time. It uses Kafka for data streaming and a machine learning model microservice for inference, predicting the likelihood of customers opening term deposits.

## How to Run
1. Start the services:  
   ```sh
   docker-compose up
   ```
2. If you want to manually create a Kafka topic after setup, remove `kafka-create-topics` from `docker-compose.yml` and run:  
   ```sh
   docker exec -it kafka kafka-topics.sh --bootstrap-server localhost:9092 --topic <your-topic-name> --create
   ```
3. Install dependencies:  
   ```sh
   pip install -r requirements.txt
   ```
4. Start the producer:  
   ```sh
   python3 simulation.py
   ```
5. Start the consumer and run inference:  
   ```sh
   faust -A customer_prediction worker -l info
   ```
