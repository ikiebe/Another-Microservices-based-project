FROM python:3.11-slim

# Set work directory
WORKDIR /app

# Install system dependencies required for MySQL client and building wheels
RUN apt-get update && apt-get install -y \
    default-libmysqlclient-dev \
    build-essential \
    pkg-config \
    && rm -rf /var/lib/apt/lists/*

# Install python dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy project files
COPY . .

# Expose port
EXPOSE 8000

# Default command to run the development server
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]