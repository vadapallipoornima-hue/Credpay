FROM python:3.14-slim AS build
ENV PYTHONDONTWRITEBYTECODE=1   
ENV PYTHONUNBUFFERED=1     
WORKDIR /build
COPY requirements.txt .
RUN pip3 install --no-cache-dir -r requirements.txt 
COPY app ./app
ENV DB_USERNAME=postgres
ENV DB_HOST=localhost
ENV DB_PORT=5432
FROM DB_NAME=credpay
USER appuser
EXPOSE 8000
ENTRYPOINT ["uvicorn","app.main:app","--host","0.0.0.0","--port","8000"]

#//multiple stage is not needed in python. no complition is needed.
