FROM python:3.11-slim

RUN apt-get update && apt-get install -y \
    default-libmysqlclient-dev \
    build-essential \
    pkg-config \
    libssl-dev \
 && rm -rf /var/lib/apt/lists/*

RUN pip install --upgrade pip

WORKDIR /app
COPY requirements.txt /app/

RUN pip install -r requirements.txt
RUN pip install "uvicorn[standard]"

COPY . /app/

CMD ["gunicorn", "library.asgi:application", "--bind", "0.0.0.0:8000"]



