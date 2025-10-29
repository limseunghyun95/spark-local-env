# 베이스 이미지
FROM apache/spark:3.5.7

# root 권한으로 설치
USER root

# 필수 패키지 설치 + AWS CLI + Python 패키지
RUN apt-get update && \
    apt-get install -y unzip curl less groff && \
    curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "/tmp/awscliv2.zip" && \
    unzip /tmp/awscliv2.zip -d /tmp && \
    /tmp/aws/install && \
    pip3 install --no-cache-dir jupyterlab pandas pyarrow boto3 pyspark && \
    rm -rf /tmp/awscliv2.zip /tmp/aws

# 작업 디렉토리
WORKDIR /opt/workspace

# 포트 설정 (docker run 또는 compose에서 다시 열어야 함)
EXPOSE 8888 4040

# 컨테이너 시작 시 실행할 명령
CMD ["jupyter", "lab", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root", "--NotebookApp.token=''"]
