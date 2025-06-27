# ✅ Stage 1: Build dependencies
FROM python:3.10-slim AS builder

WORKDIR /app

COPY requirements.txt .

RUN pip install --user -r requirements.txt

# ------------------------------------------------

# ✅ Stage 2: Runtime image
FROM python:3.10-slim

ENV PATH=/root/.local/bin:$PATH

WORKDIR /app

COPY --from=builder /root/.local /root/.local

COPY . .

# ✅ Load environment variables automatically (used by dotenv)
ENV PYTHONUNBUFFERED=1

# ✅ Open the Flask port
EXPOSE 5000

# ✅ Run the app
CMD ["python", "app.py"]
