# 今回はdebianベースのpythonイメージをベースとする
FROM python:3.8-alpine

# 設定ファイルの転送(適当な場所が思いつかないので/app直下)
RUN mkdir -p /app/config
COPY ./app2.py /app
COPY ./config /app
RUN ls /app
COPY ./requirements2.txt /app
ENV PYTHONUNBUFFERED 1
ENV PYTHONDONTWRITEBYTECODE 1


# パッケージのインストール
RUN pip install -r /app/requirements2.txt


EXPOSE 8765

WORKDIR /app

# run実行時のコマンド
# ENTRYPOINT->CMDでCMDはrunのときの引数で上書きすることが可能

ENTRYPOINT ["gunicorn", "app2:app" ]
CMD [ "-c", "guniconf2.py" ]