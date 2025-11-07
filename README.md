# NBA_Analysis_Project
Track, analyze, and visualize NBA team and player statistics. This is a minimal but production-minded starter. It includes FastAPI, Streamlit, a PostgreSQL schema with Liquibase, and CI with GitHub Actions.

## Quickstart

### 1) Requirements
- Docker and Docker Compose installed
- Make sure port 8000 and 8501 are available
- fastapi==0.115.2
- uvicorn[standard]==0.30.6
- pydantic==2.9.2
- SQLAlchemy==2.0.35
- psycopg2-binary==2.9.9
- python-dotenv==1.0.1
- requests==2.32.3
- pandas==2.2.3
- numpy==2.1.2
- plotly==5.24.1
- streamlit==1.39.0
- nba_api==1.4.1
- structlog==24.1.0
- redis==5.1.1

# Dev
- pytest==8.3.3
- black==24.10.0
- flake8==7.1.1
- mypy==1.13.0

### 2) Environment
Copy `.env.example` to `.env` and adjust as needed.

```bash
cp .env.example .env
```

### 3) Run services
```bash
docker compose up --build
```

- API available at http://localhost:8000
- API docs at http://localhost:8000/docs
- Streamlit app at http://localhost:8501

### 4) Run tests locally
```bash
pip install -r requirements.txt
pytest -q
```

### 5) Daily ETL
A scheduled GitHub Actions workflow (`.github/workflows/refresh.yml`) is provided.
Locally, you can run:
```bash
bash scripts/refresh_daily.sh
```

## Structure
```
nba-analytics/
  api/                 FastAPI service and routers
  analytics/           Advanced metrics and helpers
  app/                 Streamlit app
  etl/                 Ingest jobs for games and box scores
  infra/liquibase/     Schema migrations
  docker/              Dockerfiles
  scripts/             Utility scripts
  tests/               Unit tests
  .github/workflows/   CI and scheduled ETL
```

## Notes
- Liquibase changesets define a baseline schema for teams, players, games, box scores, and derived stats.
- ETL scripts are skeletons you can extend with nba_api calls and upserts.
- Keep secrets in environment variables. Never commit plaintext secrets.
