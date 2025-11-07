## Signal内置代理搭建
此脚本有什么作用：
可以在服务器上自建内置代理让被signal限制封锁的地区也能使用

### 使用说明
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
