Sure! Here’s a clean and professional README.md file tailored for your real-time Kafka + ClickHouse + FastAPI + Streamlit pipeline for Jira-style ticket analytics:

⸻

🧠 AI-Powered Jira Ticket Analytics Pipeline

This project is an end-to-end real-time analytics pipeline for processing, analyzing, and visualizing Jira-style consumer complaint tickets (e.g., food bank issues). It includes:
	•	FastAPI for RESTful ingestion
	•	Kafka for message queuing
	•	Avro + Schema Registry for serialization
	•	ClickHouse for ultra-fast OLAP-style storage
	•	Streamlit for rich, multi-page dashboards
	•	Agentic AI (via Gemini or Ollama) for summarization and urgency/prioritization

⸻

📁 Project Structure

.
├── Ingest/<br>
│   ├── app/<br>
│   │   ├── services/              # Kafka producer & ClickHouse consumer<br>
│   │   ├── routes/                # FastAPI routes (ticket ingestion)<br>
│   │   ├── schemas/               # Avro schema file<br>
│   │   └── main.py                # FastAPI app entry point<br>
│   ├── docker-compose.yml        # Kafka & Zookeeper Docker setup<br>
│   └── ticket.avsc               # Avro schema for Kafka serialization<br>
├── Modules/<br>
│   ├── db.py                     # ClickHouse query connector<br>
│   ├── preprocessing.py          # Data cleaning<br>
│   ├── forecasting.py            # Time series logic<br>
│   ├── agent_insights.py         # Agentic AI pipeline<br>
├── Pages/<br>
│   ├── Home.py<br>
│   ├── Priority_and_Escalation.py<br>
│   └── Time_Insights.py<br>
├── streamlit_app.py              # Streamlit entry point<br>
└── requirements.txt              # Python dependencies<br>


⸻

🚀 Getting Started

1. Clone the Repository

git clone https://github.com/yourusername/ai-jira-analytics.git
cd ai-jira-analytics



⸻

2. Start Kafka + ClickHouse via Docker

cd Ingest
docker compose up -d

Ensure the following containers are running:

docker ps



⸻

3. Create the ClickHouse Table

Login to the ClickHouse container:

docker exec -it clickhouse clickhouse-client

Run the schema:

CREATE TABLE jira_issues_raw (
    `Summary` String,
    `Issue key` String,
    `Issue id` Int64,
    `Issue Type` String,
    ...
    `Comment.20` String
) ENGINE = MergeTree ORDER BY `Status`;



⸻

4. Launch FastAPI (Kafka Producer)

cd Ingest
uvicorn app.main:app --reload

Test the endpoint at:

http://127.0.0.1:8000/docs



⸻

5. Send Sample Data to Kafka

You can use your CSV loader script or test with:

python app/services/kafka_producer.py



⸻

6. Start Kafka Consumer to Insert into ClickHouse

python app/services/clickhouse_sink.py

Watch logs for:

Inserted message into ClickHouse



⸻

7. Launch Streamlit Dashboard

streamlit run streamlit_app.py



⸻

💡 Features
	•	Real-time ingestion from CSV/API
	•	Sentiment analysis and urgency scoring
	•	ClickHouse-based time filtering and escalation trends
	•	Gemini/Ollama-powered agentic AI bullet summaries
	•	Global filters and rich dashboards using Streamlit + Plotly


⸻

 License

This project is licensed under the MIT License. Feel free to use, contribute, and fork!

⸻

Let me know if you’d like me to tailor this README to include badges, CI instructions, or demo images/gifs.
