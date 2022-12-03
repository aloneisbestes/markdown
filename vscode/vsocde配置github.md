# vscode配置github保存当前配置

### 描述：

方便重新安装vscode时，可以从[github](https://so.csdn.net/so/search?q=github&spm=1001.2101.3001.7020)上下载安装这个保存的配置，不用辛苦重新配置。

### 配置步骤：

> 第一步：安装拓展[ Settings Sync](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync)，安装完成后，重启。
>
> 第二部：设置 Github Person Access Token
>
> 第三步：上传你的配置到 Github Gist。

#### 1. 安装 Settings Sync

![image-20221130214933290](..\image\image-20221130214933290.png)

#### 2. 设置 Github Person Access Token

```http
https://github.com/settings/tokens
```

![image-20221130215138768](..\image\image-20221130215138768.png)

写入 token 的描述，勾选 gist 选项，点击Generate token，生成access token。

> 注意：***access token 一定要保存，只会出现一次。***

**新创建一个Access Token**

![image-20221130215458551](..\image\image-20221130215458551.png)

![image-20221130215539983](..\image\image-20221130215539983.png)

> access token:   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

#### 3. vscode 中登录 github

![image-20221130220304891](..\image\image-20221130220304891.png)

![image-20221130220446544](..\image\image-20221130220446544.png)

**配置Gist ID**

![image-20221130220543230](..\image\image-20221130220543230.png)

> Gist ID: c7010066db739d6651e5128af0ca6e09