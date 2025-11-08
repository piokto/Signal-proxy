## Signal内置代理搭建
此脚本有什么作用：
Signal 的简单 TLS 代理在 Signal Android 和 Signal iOS 上均受支持，还可以绕过网络阻止并安全地将流量路由到 Signal 服务。部署完成后，您将获得一个URL，他人只需点击该链接，即可轻松使Signal通过代理连接。

而搭建 Signal 代理并不复杂，只需几步即可完成。建议在搭建前先查看 Signal-TLS-Proxy，我以 Ubuntu 24.04 LTS (Noble Numbat) 为例，一步步搭建 Signal 代理。
### 手动安装

#### 1. 安装 Docker
首先运行以下命令安装 Docker：
```
snap install docker
```
#### 2. 克隆 Signal TLS Proxy 仓库
使用以下命令克隆官方仓库：
```
git clone https://github.com/signalapp/Signal-TLS-Proxy.git
cd Signal-TLS-Proxy/
```
#### 3. 生成证书
运行以下脚本生成证书：
```
./init-certificate.sh
```
脚本会提示：
```
Enter domain name ([eg.www.example.com](http://eg.www.example.com/)):
```
输入你想要绑定的域名（请确保你的 VPS 已与该域名绑定）。

#### 4. 启动服务
运行以下命令启动 Signal TLS Proxy 服务：
```
docker compose up -d && docker compose logs -f
```
如果没有错误提示，服务即已成功运行。

#### 5. 配置 Signal 客户端
访问以下 URL 并将 # 后面的内容替换为你刚刚设置的域名：
```url
https://signal.tube/#<your_host_name>
```
完成后，就代表你的 Signal 代理可以使用了！你可以将这个代理供自己使用或分享给需要的人。
### 使用脚本说明
系统建议使用Debian|Ubuntu
1. 检测系统环境并根据需要更换源为阿里云源
2. 安装必要的依赖（curl、git、openssl）
3. 检测并安装Docker和docker-compose（如果尚未安装）
4. 检查是否存在端口冲突（80和443端口）
5. 克隆Signal TLS Proxy仓库
6. 运行证书生成脚本，提示用户输入域名
7. 启动Signal TLS Proxy服务
8. 显示服务状态、域名和IP信息
9. 检查BBR状态并提供开启指南
10. 显示常用管理命令
11. 使用时，您需要有一个已经解析到服务器IP的域名，并在生成证书时输入该域名

### 一键脚本
```shell
curl -fsSL https://raw.githubusercontent.com/piokto/Signal-proxy/refs/heads/main/signal-proxy.sh | bash
```
