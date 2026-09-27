FROM python:3.13-slim

WORKDIR /app

# Install system dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    libpq-dev \
    ffmpeg \
    curl \
    && rm -rf /var/lib/apt/lists/*

# Copy requirements from root
COPY requirements.txt .

# Install Python packages
RUN pip install --no-cache-dir -r requirements.txt

# Copy backend application code
COPY backend /app

EXPOSE 8000

# Run uvicorn on $PORT (or 8000 default)
CMD ["sh", "-c", "uvicorn app.main:app --host 0.0.0.0 --port ${PORT:-8000}"]
