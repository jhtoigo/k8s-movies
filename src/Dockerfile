FROM python:3.8-slim-buster
WORKDIR /app
COPY requirements.txt .
RUN python -m pip install -r requirements.txt
COPY . /app
EXPOSE 5000
CMD ["gunicorn", "--workers=3", "--bind", "0.0.0.0:5000", "--error-logfile", "-", "--access-logfile", "-", "--capture-output", "--log-level", "debug", "-c", "config.py", "app:app"]