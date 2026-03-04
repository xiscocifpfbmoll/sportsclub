# docker/app/Dockerfile
FROM python:3.13-slim-trixie

EXPOSE 8080

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

# Set work directory
WORKDIR /app

# Install system dependencies for psycopg3
RUN apt-get update && apt-get install -y \
    curl \
    libpq-dev \
    gcc \
    && rm -rf /var/lib/apt/lists/*

# Install Python dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
RUN pip install --no-cache-dir uvicorn

# ----  HARDENING  ----

# Create non-root user
RUN useradd -m -r appuser

# Copy project
COPY sportsclub/ /app

# Change ownership to non-root user
RUN chown -R appuser:appuser /app

# Switch to non-root user
USER appuser

# --------------------------------------

# Collect static files (Django needs psycopg3/libpq)
RUN python manage.py collectstatic --noinput

# Run uvicorn
CMD ["uvicorn", "sportsclub.asgi:application", "--host", "0.0.0.0", "--port", "8080"]
