# Workers-Proxy-Docker
这个项目是一个基于 Cloudflare Workers 的 Docker 镜像下载和搜索代理工具。它能够中转对 Docker 官方镜像仓库的请求，解决镜像下载和搜索的问题。

## 部署方式
### Workers 部署：
![image](https://github.com/user-attachments/assets/4796e71e-61e6-4759-9099-355914fdb71f)
![image](https://github.com/user-attachments/assets/8357eb97-1613-40bb-8ae5-06928eb0ec6f)

- 复制 `_worker.js` 代码，保存并部署即可
![image](https://github.com/user-attachments/assets/5d4e9cc7-a260-41ab-bd2b-c72954aacb50)
![image](https://github.com/user-attachments/assets/2d044b69-db29-4862-b888-f8f9f47e8869)

- 绑定自己的域名
![image](https://github.com/user-attachments/assets/8b21f446-3abd-48cf-a6a0-ceb500820bba)


## 如何使用
- 例如您的Workers项目自己绑定域名为：`hub.dqzboy.io`，直接打开域名搜索镜像即可（也可以使用worker的域名，但是国内不开梯子访问不了）
![image](https://github.com/user-attachments/assets/0dc7501d-e8ea-46ce-b623-8282a91d7369)
![image](https://github.com/user-attachments/assets/81b488d4-2c71-472e-9773-b97a8e22e568)

### 1、指定代理域名下载
```
# 第三方组织和个人镜像下载
docker pull hub.dqzboy.io/stilleshan/frpc:latest

# 官方进行下载，需要在镜像名称前面添加 library
docker pull hub.dqzboy.io/library/nginx:latest
```

### 2、配置daemon.json
- 修改文件 `/etc/docker/daemon.json` **（如果不存在则创建）**

```
mkdir -p /etc/docker

vi /etc/docker/daemon.json
{
  "registry-mirrors": ["https://hub.dqzboy.io"]  # 请替换为您自己的Worker自定义域名
}

systemctl restart docker

# 确认镜像源生效
docker info | grep -A 10 "Registry Mirrors"
```
