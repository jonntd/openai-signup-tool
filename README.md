# openai注册机

## 介绍
基于浏览器方案的openai注册机

## 免责声明
本项目仅供学习交流使用，严禁用于商业用途，否则后果自负。

## 使用方法
### 前置准备
- 一个支持openai注册的域名，比如`example.com`
- 一个支持`catch all`的收件服务，比如cloudflare或者自建的邮箱服务器
- 一个用于接受`catch all`邮件的且支持imap协议的邮箱，比如`outlook`、`gmail`

### 开始使用

1. 配置邮箱  
配置好你前序准备的域名和邮箱，保证所有openai的邮件都会转发到你的支持imap协议的邮箱中。
2. 克隆本项目
```bash
git clone https://github.com/MagicalMadoka/openai-signup-tool.git

cd openai-signup-tool
```

3. 重命名`config/config.json.example`为`config/config.json`

- `domain`: 必填，你注册用的域名。
- `proxy`: 选填，代理地址。背后最好使用高质量的代理池，可以减少过cf和arkose的麻烦。如果代理服务器运行在你的本地，请使用`host.docker.internal`作为代理地址。
- `clientKey`: 选填，[yescaptcha](https://yescaptcha.com/i/oFmkQz)的clientKey，如果出现验证码，会尝试进行打码。
- `emailWorkerNum`: 必填，处理邮件的线程个数，根据机器的配置自行决定。
- `signupWorkerNum`: 必填，注册线程的个数，根据机器的配置自行决定。
- `emailAddr`: 必填，你的邮箱地址。
- `emailPassword`: 必填，你的邮箱密码，或应用密码。这取决于你的邮箱服务的提供方。
- `emailImapServer`: 必填，你的邮箱的imap服务器地址，一般可以在你邮箱服务的提供方的文档中找到。
- `emailImapPort`: 选填，你的邮箱的imap服务器端口，一般可以在你邮箱服务的提供方的文档中找到。

4. 运行
```bash
docker compose up -d
```
注册成功的账号会出现在`data/accounts.txt`中。如果账号被授权了额度，会额外提取sess到`data/sess.txt`中。

## 其他说明
- 本项目在一个正常延时的网络和一个配置正常的机器下测试运行正常，所以如果出现问题，可以先排查网络和机器的问题。当然也欢迎你补充一些异常处理的代码。
- 改方案是基于浏览器的方案，内存不要给的太少，否则会异常退出。

## 参考项目
- https://github.com/FlareSolverr/FlareSolverr

## 交流沟通
- 本项目相关的讨论请提issue
- 其他技术交流。逆向、验证码、深度学习、python、go都可以聊