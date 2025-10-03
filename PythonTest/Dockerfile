# Use official Python Windows Nano Server image
FROM mcr.microsoft.com/windows-cssc/python:3.11-nanoserver-ltsc2022

ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1
ENV FLASK_APP=hello.py
ENV FLASK_RUN_HOST=0.0.0.0

WORKDIR /app

COPY requirements.txt ./

# Remove this line to avoid permission error:
# RUN python -m pip install --upgrade pip

RUN python -m pip install -r requirements.txt

COPY . .

EXPOSE 8000

CMD ["flask", "run"]
