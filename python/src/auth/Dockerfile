FROM python:3.11-slim-bullseye

RUN apt update && apt install -y --no-install-recommends --no-install-suggests pkg-config gcc python3-dev build-essential default-libmysqlclient-dev \
    && pip install --no-cache-dir --upgrade pip

WORKDIR /app
COPY ./requirements.txt /app
RUN pip install --no-cache-dir --requirement /app/requirements.txt
RUN sed -i 's/from collections import Mapping/try:\n    from collections.abc import Mapping\nexcept ImportError:\n    from collections import Mapping/' /usr/local/lib/python3.11/site-packages/jwt/api_jwt.py && \
    sed -i 's/from collections import Mapping/try:\n    from collections.abc import Mapping\nexcept ImportError:\n    from collections import Mapping/' /usr/local/lib/python3.11/site-packages/jwt/api_jws.py

COPY . /app

EXPOSE 5001

CMD ["python3", "server.py"]