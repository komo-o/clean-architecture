FROM golang:1.24

WORKDIR /app

# 依存関係ファイルだけを先にコピー
COPY go.mod go.sum* ./

# 依存関係解消
RUN go mod tidy

# Airのインストール
RUN go install github.com/air-verse/air@latest

# ホットリロード用の設定ファイルをコピー
COPY .air.toml ./

# アプリケーションのソースコードをコピー
COPY . .

# ポートの公開
EXPOSE 8080

# Airを実行
CMD ["air"] 