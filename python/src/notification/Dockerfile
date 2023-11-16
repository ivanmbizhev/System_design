FROM python:3.11-slim-bullseye

RUN apt update && apt install -y --no-install-recommends --no-install-suggests pkg-config gcc python3-dev build-essential \
    && pip install --no-cache-dir --upgrade pip

WORKDIR /app
COPY ./requirements.txt /app
RUN pip install --no-cache-dir --requirement /app/requirements.txt

COPY . /app

CMD ["python3", "consumer.py"]