

├── README.md
│
├── architecture/
│   └── architecture.png
│
├── src/
│   └── dataflow/
│       ├── config.py
│       ├── ingestion.py
│       ├── transformation.py
│       ├── quality.py
│       ├── database.py
│       └── warehouse.py
│
├── airflow/
│   └── dags/
│       └── dataflow_pipeline.py
│
├── sql/
│   ├── staging/
│   ├── warehouse/
│   └── analytics/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── tests/
│   ├── test_ingestion.py
│   ├── test_transformation.py
│   ├── test_quality.py
│   └── test_warehouse.py
│
├── docs/
│   ├── airflow-dag.png
│   ├── postgres-schema.png
│   ├── data-quality.png
│   └── pipeline-result.png
│
├── Dockerfile
├── docker-compose.yml
├── requirements.txt
├── .env.example
├── .gitignore
└── run_pipeline.py


Pipeline 

CSV / API
                  │
                  ▼
             ┌─────────┐
             │ Python  │
             │ Extract │
             └────┬────┘
                  │
                  ▼
             ┌─────────┐
             │ Quality │
             │  Gate   │
             └────┬────┘
                  │
                  ▼
             ┌─────────┐
             │ Pandas  │
             │Transform│
             └────┬────┘
                  │
                  ▼
          ┌───────────────┐
          │  PostgreSQL   │
          │    STAGING    │
          └───────┬───────┘
                  │
                  ▼
          ┌───────────────┐
          │  PostgreSQL   │
          │  DATA WAREHOUSE
          └───────┬───────┘
                  │
                  ▼
             ┌─────────┐
             │  SQL    │
             │Analytics│
             └─────────┘

        ↑
     Airflow
  Orchestration
