# Real-time Crypto Streaming Platform

This project is a real-time data pipeline using:
- Binance WebSocket (crypto ticker stream)
- Apache Kafka for streaming pipeline
- PostgreSQL for persistent storage
- Streamlit Dashboard for live monitoring

## Architecture
WebSocket → Kafka → PostgreSQL → Dashboard

## Features
- Real-time BTCUSDT price ingestion
- Structured storage into database (id, symbol, price, timestamp)
- Live dashboard updates every 3 seconds
- Fully containerized using Docker

## Tech Stack
| Component | Technology |
|----------|------------|
| Data Source | Binance WebSocket API |
| Streaming | Kafka |
| Storage | PostgreSQL |
| Dashboard | Streamlit |
| Deployment | Docker Compose |
| Language | Python |

## Dashboard Preview
<img width="1919" height="1077" alt="Screenshot 2025-12-05 134439" src="https://github.com/user-attachments/assets/2f08a952-db53-4eeb-9ac5-ab1de9bf38f2" />

<img width="1919" height="1079" alt="Screenshot 2025-12-05 134415" src="https://github.com/user-attachments/assets/b9d3ee0b-2bd9-4532-afdb-699e89ccf6dc" />

<img width="1919" height="1077" alt="Screenshot 2025-12-05 140947" src="https://github.com/user-attachments/assets/a915deb5-1709-4121-8d8b-c315375f4969" />


## How to Run
```sh
# Start Docker services
docker compose up -d

# Activate virtual environment
venv\Scripts\activate

# Run Kafka producer
python src\producer_crypto.py

# Run Kafka → DB consumer
python src\consumer_db.py

# Run dashboard
streamlit run src\dashboard_realtime.py

CREATE TABLE crypto_realtime_prices (
    id SERIAL PRIMARY KEY,
    symbol VARCHAR(20),
    price NUMERIC(18,8),
    ts TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
