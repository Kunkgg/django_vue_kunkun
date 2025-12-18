## 部署说明

way1: 浏览器 kunkun.test -> 宿主机 nginx -> docker-compose 前端服务 nginx (只暴露前端) -> 后端服务 django (后端接口经过前端服务转发)
way2: 浏览器 kunkun.test -> 宿主机 nginx -> docker-compose [前端服务 nginx + 后端服务 django] (前后端服务均暴露，前端浏览器直接请求后端)

## 宿主机



## 后端

## nginx 反向代理配置示例

| location | proxy_pass  | 实际效果          | 是否推荐 |
| -------- | ----------- | ------------- | ---- |
| `/api/`  | `http://x/` | `/api/` → `/` | ✅    |
| `/api/`  | `http://x`  | `/api/` 保留    | ❌    |
| `/`      | `http://x`  | 原样            | ✅    |
| `/`      | `http://x/` | 无意义替换         | ❌    |

