# ===============================
# Stage 1: Build
# ===============================
FROM node:24.12.0-alpine AS builder

WORKDIR /app
COPY package.json package-lock.json .
RUN npm ci

COPY . .

RUN npm run build

# ===============================
# Stage 2: Runtime
# ===============================
FROM nginx:alpine-slim

# 删除默认配置
RUN rm /etc/nginx/conf.d/default.conf

# 拷贝自定义 nginx 配置
COPY nginx.conf /etc/nginx/conf.d/default.conf

# 拷贝构建产物
COPY --from=builder /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
