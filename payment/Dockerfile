FROM python:3.9-slim
WORKDIR /app
COPY requirements.txt .
RUN apt-get update \
    && apt-get install -y --no-install-recommends gcc \
    && pip3 install --no-cache-dir -r requirements.txt \
    && apt-get purge -y --auto-remove gcc \
    && rm -rf /var/lib/apt/lists/*
COPY payment.ini .
COPY *.py .
EXPOSE 8080
CMD ["uwsgi", "--ini", "payment.ini"]






# FROM python:3.9
# WORKDIR /app
# COPY requirements.txt .
# COPY payment.ini .
# COPY *.py .
# RUN pip3 install -r requirements.txt
# EXPOSE 8080
# CMD ["uwsgi", "--ini", "payment.ini"]