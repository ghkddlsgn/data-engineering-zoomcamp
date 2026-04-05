FROM python:3.13.11-slim
COPY --from=ghcr.io/astral-sh/uv:latest /uv /bin/

WORKDIR /code
ENV PATH="/code/.venv/bin:$PATH"

COPY pyproject.toml .python-version uv.lock ./
RUN uv sync --locked

COPY ingest_data.py .

ENTRYPOINT ["python", "ingest_data.py"]

# docker run -d `
#   -e POSTGRES_USER="root" `
#   -e POSTGRES_PASSWORD="root" `
#   -e POSTGRES_DB="ny_taxi" `
#   -v "$PWD/ny_taxi_postgres_data:/var/lib/postgresql" `
#   -p 5433:5432 `
#   postgres:18

# uv run pgcli -h localhost -p 5433 -u root -d ny_taxi