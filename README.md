## 微信交易记录（支出）导出工具

### 写在前面的话：
1. 自用工具，由于本人只对微信支出记录感兴趣，所以只提供导出支出记录。后续如果有空，会添加收入记录的导出。
2. 本工具的技术核心是`Man-in-the-Middle`,如果介意安全问题的您就别用了。

### 依赖
1. node.js > 8.0
2. yarn || npm

### 使用步骤
1. 下载项目 根目录执行 yarn || npm install 
2. 控制台执行 sudo npm install node-mitmproxy -g
3. 生成CA证书
  - mac : `sudo security add-trusted-cert -d -r trustRoot -k /Library/Keychains/System.keychain ~/node-mitmproxy/node-mitmproxy.ca.crt`
  - windows: `start %HOMEPATH%/node-mitmproxy/node-mitmproxy.ca.crt` (我没试过)
4. 生成CA根证书的默认路径：%用户名%/node-mitmproxy,把生成好的`node-mitmproxy.ca.crt`导入安装微信的设备，我的是安卓手机。不同的设备导入证书的方法不同。具体请自行百度 `XXX手机如何导入CA证书`。
5. 在文件config.json中配置好端口和导出文件名，默认不需要变动，如果有这块的需要的可以自行更改。
6. 开启pac服务 `npm run start-pac`
7. 开启proxy服务 `npm run start`
8. 设备和电脑保证在同一个局域网下，设备配置代理，代理方式是自动配置类型，pac网址填写pac服务开启时提示的url。
9. 打开微信,打开我的钱包，打开支付中心，打开交易记录。
