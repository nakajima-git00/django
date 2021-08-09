FROM python:3.9-slim

#パッケージのインストール
RUN apt-get update && apt-get install -y \
  tzdata \
  && rm -rf /var/lib/apt/lists/*

# モジュールのインストール
WORKDIR /tmp/work
COPY requirements.txt ${PWD}
RUN pip install -r requirements.txt

#環境変数の定義
ENV TZ=Asia/Tokyo
ENV USER=user1

# 一般権限ユーザを追加
RUN USERADD -M ${USER}
RUN gpasswd -a ${USER}
RUN echo "${USER}:password" | chpasswd

# ユーザの切り替え
USER ${USER}
