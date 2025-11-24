FROM python:3.10-slim
WORKDIR /app
#COPY queue_exporter.py /app/
RUN pip install flask requests
ENV TARGET_URL=""
EXPOSE 9000





CMD ["python3", "queue_exporter.py"]
