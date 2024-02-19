FROM python:3.8-slim-buster

WORKDIR /app

RUN apt-get update && \
    apt-get install -y git wget unzip && \
    rm -rf /var/lib/apt/lists/*

RUN apt-get update && \
    apt-get install -y --no-install-recommends docker-compose && \
    rm -rf /var/lib/apt/lists/*

RUN git clone https://github.com/mitre-attack/tram.git /app/tram

WORKDIR /app/tram

RUN pip install --no-cache-dir -r requirements.txt

RUN mkdir -p /root/nltk_data/tokenizers && \
    cd /root/nltk_data/tokenizers && \
    wget https://github.com/nltk/nltk_data/raw/gh-pages/packages/tokenizers/punkt.zip -O punkt.zip && \
    unzip punkt.zip && \
    rm punkt.zip

EXPOSE 9999

WORKDIR /app/tram

CMD ["python3", "tram.py"]
