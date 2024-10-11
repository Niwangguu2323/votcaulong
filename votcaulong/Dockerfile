# Chọn base image từ Python
FROM python:3.9-slim

# Thiết lập thư mục làm việc
WORKDIR /app

# Cài đặt các gói hệ thống cần thiết cho psycopg2
RUN apt-get update && \
    apt-get install -y gcc libpq-dev && \
    apt-get clean

# Sao chép các file cần thiết vào hình ảnh
COPY requirements.txt ./

# Cài đặt các thư viện cần thiết
RUN pip install --no-cache-dir -r requirements.txt

# Sao chép toàn bộ mã nguồn vào hình ảnh
COPY . .

# Cài đặt Java cho PySpark
RUN apt-get update && \
    apt-get install -y openjdk-17-jre-headless && \
    pip install pyspark

# Thiết lập biến môi trường JAVA_HOME cho PySpark
ENV JAVA_HOME="/usr/lib/jvm/java-11-openjdk-amd64"

# Chạy lệnh Scrapy để cào dữ liệu
CMD ["scrapy", "crawl", "mycaulong"]
