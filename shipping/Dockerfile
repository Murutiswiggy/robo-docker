FROM python:3.9.25-alpine3.22 AS builder
WORKDIR /app
COPY requirements.txt .
# COPY payment.ini .
# COPY *.py .
RUN apk add --no-cache --virtual .build-deps gcc musl-dev linux-headers python3-dev \
    && pip3 install --prefix=/install -r requirements.txt \
    && apk del .build-deps

FROM python:3.9.25-alpine3.22
WORKDIR /app
EXPOSE 8080
RUN addgroup -S roboshop && adduser -S -G roboshop roboshop && \
    chown -R roboshop:roboshop /app
COPY  --from=builder /install /usr/local
COPY --chown=roboshop:roboshop payment.ini *.py requirements.txt .
USER roboshop
CMD ["uwsgi", "--ini", "payment.ini"]







# FROM maven:3.9.16
# WORKDIR /app
# COPY pom.xml .
# COPY src ./src
# RUN mvn clean package
# RUN mv target/shipping-1.0.jar shipping.jar
# EXPOSE 8080
# CMD ["java", "-jar", "shipping.jar"]