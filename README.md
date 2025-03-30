# Kafka Streaming Pipeline

This project sets up a real-time event streaming pipeline using Kafka. It streams bank customer data to a machine learning model, which predicts the chances of a customer opening a term deposit.

## How to Run
1. Fire up the services:
   ```sh
   docker-compose up
   ```
2. Want to create a Kafka topic manually? First, remove `kafka-create-topics` from `docker-compose.yml`, then run:
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
5. Run the consumer and process incoming data:
   ```sh
   faust -A customer_prediction worker -l info
   ```
