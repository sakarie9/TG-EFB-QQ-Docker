# TG-EFB-QQ-Docker

EFB和Mirai的Docker Compose部署方式

>**请优先使用 [go-cqhttp](https://github.com/xzsk2/TG-EFB-QQ-Docker/tree/go-cqhttp) 分支，使用 [go-cqhttp](https://github.com/Mrs4s/go-cqhttp) 代替mirai，拥有更高的性能及更低的占用**

使用项目

- [TG-EFB-QQ-Docker](https://github.com/xzsk2/TG-EFB-QQ-Docker)

  - [EFB-Docker](https://github.com/xzsk2/EFB-Docker)
    - [EH Forwarder Bot](https://github.com/ehForwarderBot/ehForwarderBot)
    - [Telegram Master](https://github.com/ehForwarderBot/efb-telegram-master)
    - [QQ Slave](https://github.com/milkice233/efb-qq-slave)
    - [QQ Plugin Mirai](https://github.com/milkice233/efb-qq-plugin-mirai)
    - [efb-filter-middleware](https://github.com/xzsk2/efb-filter-middleware)

  - [Mirai-Docker](https://github.com/xzsk2/Mirai-Docker)
    - [Mirai Console Loader](https://github.com/iTXTech/mirai-console-loader)
    - [mirai-api-http](https://github.com/project-mirai/mirai-api-http)

**完整教程 [Telegram收发QQ信息-EFB和Mirai的Docker部署教程](https://sakari.top/2021/05/05/tg-qq/)**

以下为简易教程

## 使用

### 克隆项目

```bash
# 克隆
git clone https://github.com/xzsk2/TG-EFB-QQ-Docker.git
# 进入文件夹
cd TG-EFB-QQ-Docker
```

### 修改配置文件

参考 [Telegram收发QQ信息-EFB和Mirai的Docker部署教程](https://sakari.top/2021/05/05/tg-qq/) 或各项目的文档

### 运行

```bash
docker-compose up -d
```

### 停止

```bash
docker-compose down
```
