# Stage 1: Dependency Builder
FROM python:3.9-slim AS builder

WORKDIR /app

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

# Stage 2: Image Creation
FROM python:3.9-slim 

COPY --from=builder /app/lib/python3.9/site-packages app/lib/python3.9/site-packages

COPY src/myapp.py src/mytest.py .

EXPOSE 6666

CMD [ "gunicorn", "--bind", "0.0.0.0:6666", "myapp:app"]
