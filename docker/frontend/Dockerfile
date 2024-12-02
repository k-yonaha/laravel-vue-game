FROM node:20-alpine

# 作業ディレクトリ
WORKDIR /app

# インストール
COPY ./frontend/package*.json ./
# RUN yarn install
RUN npm install

# プロジェクトファイルをコピー
COPY ./frontend/ ./

EXPOSE 5173
# デフォルトコマンド（開発モードで起動）
CMD ["npm", "run", "dev"]