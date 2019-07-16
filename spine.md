# spineL1安装和使用教程
## 步骤一 安装spine
1. 将spine源码clone下来：
   ```bash
   git clone https://github.com/bigegg-software/1905_spine.cli.git
   ```
2. 安装spine并链接到全局目录下，方便我们在1905_spine.cli以外的目录下使用spine：
   ```bash
   cd 1905_spine.cli
   npm install && npm link
   ```
3. 使用spine创建应用之前需要[开通阿里云RAM访问控制服务（免费的）](https://ram.console.aliyun.com/) (不开通创建会app会失败～)
4. 在使用spine创建app之前需要执行，效果如下图：
   ```bash
   spine config
   ```
   ![图片](https://uploader.shimo.im/f/9TVv5Eufe1YkyaEF.png!thumbnail)

## 步骤二 使用spine创建app
1. spine已经安装完毕，使用spine newapp xxx 创建一个新项目: 如下代码和截图演示
     ```bash
     spine newapp xxx
     注：ZygoteUrl ：默认的种子url，直接Enter就好
        Your app Git repo url：输入github创建新应用的地址
     ```
     ![图片](https://uploader.shimo.im/f/jojYptMT91oRaF2f.png!thumbnail)
2. 将上图中生成的ssh pubkey 添加到github账号setting中的pubkey中
3. Please confirm that ssh pubkey is added to the git repo：Y（确认ssh加入了github的setting SSH中了）
4. Set a password for IDE：设置IDE密码（字母或数字，不可为空）如："123456"
    ```bash
        Set a password for IDE：123456
    ```
5. 所有的配置完成后开始创建project，期间会要求输入github username和password，运行效果如图：
   ![图片](https://uploader.shimo.im/f/WaP1teK1gLgvRWjg.png!thumbnail)
   ![图片](https://uploader.shimo.im/f/BtOt8pLPLkwvvDA7.png!thumbnail)
   ![图片](https://uploader.shimo.im/f/WV2P8wfmoZMlZmoi.png!thumbnail)
   ![图片](https://uploader.shimo.im/f/cdwuzve2bFsulrvj.png!thumbnail)
   ![图片](https://uploader.shimo.im/f/SIef3SEKn6Qg2iZz.png!thumbnail)
6. 最终提示：Your IDE will be at: https://121.40.31.104:8443，我的IDE在这个生成地址上可以直接访问并部署了
  
## 步骤三 使用vsCode开发app
1. 访问我的IDE地址，可能会报不安全链接，但是没关系，直接点进去，如图：输入自己设置的密码，如：123456
     ![图片](https://uploader.shimo.im/f/jXSwRer1xgYJJS2F.png!thumbnail)
2. 输入密码后进入vscode主页：
     ![图片](https://uploader.shimo.im/f/pOBOOh9Ejt0qSQMw.png!thumbnail)
3. 新建Terminal：
     ![图片](https://uploader.shimo.im/f/7ldjlVZgrckJxWLc.png!thumbnail)
4. 在Terminal中的project目录下执行：npm install 安装依赖包，效果图如下：
    ```bash
    npm install
    ```
5. 执行 sh run_local.sh 启动服务
   ```bash
   sh run_local.sh
   ```
6. 注意：sh run_local.sh失败时，提示没有parse-server，缺什么module就安装什么就好了，
   如图：我的缺少parse-server，于是安装npm install parse-server，再尝试一下 sh run_local.sh 启动
命令就成功了
   ```bash
   npm install parse-server
   ```
   ![图片](https://uploader.shimo.im/f/VFXCTQpMhhQIHp2Y.png!thumbnail)

## 步骤四 本地部署
1. 服务启动后，打开本地相应端口页面：curl 'http://127.0.0.1:1337/' 测试本地服务，如图
    ```bash
    curl 'http://127.0.0.1:1337/'
    ```
2. 测试修改部分代码后，可以直接保存并启动本地服务再次执行：
    ```bash
    curl 'http://127.0.0.1:1337/'
    ```
3. 如图可以看出代码内容更改并生效了：
  ![图片](https://uploader.shimo.im/f/pi39tpBIr00w4Wql.png!thumbnail)
## spine使用注意事项
1. VSCode IDE需要及时保存，代码修改才能生效。
2. 如果不再使用ECI弹性容器，可以及时删除，以免产生不必要的费用支出
3. [删除ECI弹性容器](https://eci.console.aliyun.com/#/)
4. [删除vpc](https://eci.console.aliyun.com/#/)
5. [删除交换机](https://vpc.console.aliyun.com/vpc/cn-hangzhou/switches)

