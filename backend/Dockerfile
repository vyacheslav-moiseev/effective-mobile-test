FROM python:3.11-slim

RUN useradd -m appuser

WORKDIR /app

COPY app.py .

RUN chown -R appuser:appuser /app

USER appuser

EXPOSE 8080

HEALTHCHECK --interval=10s --timeout=2s --retries=3 CMD \
    python -c "import urllib.request; urllib.request.urlopen('http://localhost:8080')" || exit 1

CMD ["python", "app.py"]