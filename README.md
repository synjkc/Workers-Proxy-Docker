<div align="center">
 <h1>Workers-Proxy-Docker</h1>
</div>

<div style="text-align: center">
  <p align="center">
      <br>
      <i>这个项目是一个基于 Cloudflare Workers 的 Docker 镜像下载和搜索代理工具。它能够中转对 Docker 官方镜像仓库的请求，解决镜像下载和搜索的问题。
.</i>
  </p>
</div>

<div align="center">
📢 <a href="https://t.me/+ghs_XDp1vwxkMGU9" style="font-size: 15px;">交流群</a>
</div>

## 📦 部署方式
### Workers 部署：
<table>
    <tr>
        <td width="50%" align="center"><img src="https://github.com/user-attachments/assets/4796e71e-61e6-4759-9099-355914fdb71f?raw=true"></td>
    </tr>
</table>

<table>
    <tr>
        <td width="50%" align="center"><img src="https://github.com/user-attachments/assets/8357eb97-1613-40bb-8ae5-06928eb0ec6f?raw=true"></td>
    </tr>
</table>


- 复制 `_worker.js` 代码，保存并部署即可

<table>
    <tr>
        <td width="50%" align="center"><img src="https://github.com/user-attachments/assets/5d4e9cc7-a260-41ab-bd2b-c72954aacb50?raw=true"></td>
    </tr>
</table>

<table>
    <tr>
        <td width="50%" align="center"><img src="https://github.com/user-attachments/assets/2d044b69-db29-4862-b888-f8f9f47e8869?raw=true"></td>
    </tr>
</table>


- 绑定自己的域名

<table>
    <tr>
        <td width="50%" align="center"><img src="https://github.com/user-attachments/assets/8b21f446-3abd-48cf-a6a0-ceb500820bba?raw=true"></td>
    </tr>
</table>

## ✨ 如何使用
- 例如您的Workers项目自己绑定域名为：`hub.dqzboy.io`，直接打开域名搜索镜像即可（也可以使用worker的域名，但是国内不开梯子访问不了）

<table>
    <tr>
        <td width="50%" align="center"><img src="https://github.com/user-attachments/assets/edbb4531-29d6-4165-9f0e-1bb4f489d744?raw=true"></td>
    </tr>
</table>

<table>
    <tr>
        <td width="50%" align="center"><img src="https://github.com/user-attachments/assets/81b488d4-2c71-472e-9773-b97a8e22e568?raw=true"></td>
    </tr>
</table>


### 方式一、指定代理域名下载
```
# 第三方组织和个人镜像下载
docker pull hub.dqzboy.io/stilleshan/frpc:latest

# 官方进行下载，需要在镜像名称前面添加 library
docker pull hub.dqzboy.io/library/nginx:latest
```

### 方式二、配置daemon.json
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

## ❤ 鸣谢
感谢以下项目的开源的付出：
[cmliu/CF-Workers-docker.io](https://github.com/cmliu/CF-Workers-docker.io/) 

- 重搞了Docker Hub 镜像搜索页面

---

[![Star History Chart](https://api.star-history.com/svg?repos=dqzboy/Workers-Proxy-Docker&type=Date)](https://star-history.com/#dqzboy/Workers-Proxy-Docker&Date)
