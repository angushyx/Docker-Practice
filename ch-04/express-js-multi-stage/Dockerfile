# FROM node:16-alpine

# EXPOSE 3000

# CMD ["node", "app.js"]

# WORKDIR /app

# COPY . /app/

# RUN yarn install

# 第一階段 --> 將需要的套件安裝完
FROM node:16-alpine AS builder

COPY package.json yarn.lock ./

RUN yarn install

# 第二階段 --> 複製第一階段安裝完成的套件 
FROM node:16-alpine 

EXPOSE 3000

CMD ["node", "app.js"]

WORKDIR /app

COPY --from=builder /node_modules /app/node_modules

# 只複製了主要的檔案
COPY app.js ./
