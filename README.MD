# 客户端配置

**/opt/frp/docker-compose.yaml**文件
```yaml
version: '3.1'
services:
  frp-server:
    image: rimag/frp:client-0.22.0
    network_mode: host
    restart: always
    volumes:
      - /etc/localtime:/etc/localtime:ro
      - /opt/frp/conf:/conf
```

**/opt/frp/conf/frps.ini**文件
```ini
[common]
# server setting
server_addr = x.x.x.x
server_port = 7000
# the sample
[ssh]
# tcp | udp | http | https | stcp | xtcp, default is tcp
type = tcp
local_ip = 127.0.0.1
local_port = 22
# use server port
remote_port = 6001
```
[frpc.ini完整配置](https://github.com/fatedier/frp/blob/master/conf/frpc_full.ini)

# 服务器端配置

**/opt/frp/docker-compose.yaml**文件
```yaml
version: '3.1'
services:
  frp-server:
    image: rimag/frp:server-0.22.0
    network_mode: host
    restart: always
    volumes:
      - /etc/localtime:/etc/localtime:ro
      - /opt/frp/conf:/conf
```

**/opt/frp/conf/frps.ini**文件
```ini
# host setting
bind_addr = 0.0.0.0
bind_port = 7000
# dashboard setting
dashboard_addr = 0.0.0.0
dashboard_port = 7500
dashboard_user = xxxx
dashboard_pwd = xxxx
```
[frps.ini完整配置](https://github.com/fatedier/frp/blob/master/conf/frps_full.ini)