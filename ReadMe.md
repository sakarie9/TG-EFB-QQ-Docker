# TG-EFB-QQ-Docker

EFB和Go-CQHTTP的Docker Compose部署方式

使用项目

- [TG-EFB-QQ-Docker](https://github.com/xzsk2/TG-EFB-QQ-Docker)

  - [EFB-Docker](https://github.com/xzsk2/EFB-Docker)
    - [EH Forwarder Bot](https://github.com/ehForwarderBot/ehForwarderBot)
    - [Telegram Master](https://github.com/ehForwarderBot/efb-telegram-master)
    - [QQ Slave](https://github.com/milkice233/efb-qq-slave)
    - [QQ Plugin Mirai](https://github.com/milkice233/efb-qq-plugin-mirai)
    - [QQ Plugin go-cqhttp](https://github.com/XYenon/efb-qq-plugin-go-cqhttp)
    - [efb-filter-middleware](https://github.com/xzsk2/efb-filter-middleware)

  - [Go-CQHttp-Docker](https://github.com/xzsk2/Go-CQHTTP-Docker)
    - [go-cqhttp](https://github.com/Mrs4s/go-cqhttp)

## 使用

### 克隆项目

```bash
# 克隆
git clone -b go-cqhttp https://github.com/xzsk2/TG-EFB-QQ-Docker.git
# 进入文件夹
cd TG-EFB-QQ-Docker
```

### 修改配置文件

可参考 [Telegram收发QQ信息-EFB和Mirai的Docker部署教程](https://sakari.top/2021/05/05/tg-qq/) 或各项目的文档

1. 修改 `blueset.telegram/config.yaml` 内的 `token` 及 `admins`，如不能访问Telegram则需要在此配置代理

2. 生成配置文件 `gocq/config.yml` ，选择1HTTP模式
   
    ```bash
    docker run --rm -it --name="gocq" -v $PWD/gocq:/data xzsk2/gocqhttp-docker:latest
    ```

3. 编辑 `gocq/config.yml` 配置文件，注意修改如下部分

    ```bash
    account:         # 账号相关
      uin: 000000000 # QQ 账号
      password: ''   # QQ 密码，为空时使用扫码登录

    message:
      # 上报数据类型
      # efb-qq-plugin-go-cqhttp 仅支持 array 类型
      post-format: array
      # 为Reply附加更多信息
      extra-reply-data: true


    # 默认中间件锚点
    default-middlewares: &default
      # 访问密钥，强烈推荐在公网的服务器设置
      access-token: ''

    servers:
      # HTTP 通信设置
      - http:
          # 服务端监听地址
          host: 127.0.0.1
          # 服务端监听端口
          port: 5700
          # 反向 HTTP 超时时间, 单位秒
          # 最小值为 5，小于 5 将会忽略本项设置
          timeout: 5
          middlewares:
            <<: *default # 引用默认中间件
          # 反向 HTTP POST 地址列表
          post:
            - url: 'http://127.0.0.1:8000' # 地址
              secret: ''                   # 密钥保持为空
    ```

4. （可选）修改登陆协议，运行如下命令，待提示生成 `device.json` 后 `ctrl+c` 退出，编辑 `gocq/device.json`

    ```bash
    docker run --rm -it --name="gocq" -v $PWD/gocq:/data xzsk2/gocqhttp-docker:latest
    ```

### 运行

```bash
docker-compose up -d
```

如需扫码登陆输入 `docker logs gocq` 查看二维码

### 停止

```bash
docker-compose down
```
