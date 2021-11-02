获取Apple 旧版本软件

- 以下操作均在**win**环境下操作，mac操作可参考，操作来源于网络。

## 1、降级iTunes

- **旧版本iTunes**下载地址：

  - Win版本 **iTunes 12.6.4** 地址：[32位下载](https://secure-appldnld.apple.com/itunes12/091-60766-201803029-1F70CB08-3131-11E8-9791-31052B2AA206/iTunesSetup.exe) ｜ [64位下载](https://secure-appldnld.apple.com/itunes12/091-60765-201803029-1F70CB08-3131-11E8-9791-31052B2AA206/iTunes64Setup.exe)

  - Mac版本 **iTunes 12.6.3 for Mac版：**[点我下载 ](http://secure-appldnld.apple.com/itunes12/091-33628-20170922-EF8F0FE4-9FEF-11E7-B113-91CF9A97A551/iTunes12.6.3.dmg) 

    ```
    降级iTunes步骤
    - 请按正确的顺序卸载 iTunes 的各个相关组件。
      1、iTunes 
      2、Apple Software Update 
      3、Bonjour 
      4、Apple Mobile Device Support 
      5、Apple Application Support（32-bit）【Apple应用程序支持(32位)】 
      6、Apple Application Support（64-bit）【Apple应用程序支持(64位)】 
      完成以上删除后，iTunes 就被彻底卸载了。
    注：重新安装 iTunes 之后搜索 iTunes Library.itl ，此文件在~/Music/iTunes/下，把它删除就可以了，如不删除，会出现第二步的错误，可按照第二步操作即可。
    ```

    


## 2、安装旧版本iTunes

- 注：iTunes版本必须低于**12.7**

  

  ![ICKdgX.jpg](https://s6.jpg.cm/2021/11/02/ICKdgX.jpg)

  

- 如出现上图所示错误，请按住**shift**后**左键**双击**iTunes快捷方式图标**，出现下图后直接选择**创建资料库**。

  

  ![ICKXeE.jpg](https://s6.jpg.cm/2021/11/02/ICKXeE.jpg)

  

## 3、安装抓包软件Fiddler

- 下载地址：
  - 官网链接：[点此](https://www.telerik.com/download/fiddler)
- 安装无脑下一步。

## 4、开始抓包

### **4.1、打开Fiddler**

- 出现两个弹窗，都选**no**

  - ![ICKUKh.jpg](https://s6.jpg.cm/2021/11/02/ICKUKh.jpg)
  - ![ICKtGH.jpg](https://s6.jpg.cm/2021/11/02/ICKtGH.jpg)

  

### **4.2、设置解析 https 请求**

- 打开 fiddler 软件的 核心功能：解析 https 请求 （decrypt https traffic）

  - 具体操作见下图
  - ![ICKseO.jpg](https://s6.jpg.cm/2021/11/02/ICKseO.jpg)
  - ![ICKoGy.jpg](https://s6.jpg.cm/2021/11/02/ICKoGy.jpg)

  

### **4.3、登入自己的apple id**

- **打开iTunes ，先登陆好苹果ID，然后进入商店主页**，按下图所示方法操作。

  - **注意：若登录出现错误，请关闭Fiddler软件的https解密，等登录过后在打开**

- **登录**

  - ![ICKfiC.jpg](https://s6.jpg.cm/2021/11/02/ICKfiC.jpg)

    

  

- **打开apple store**

  

  - ![ICK0ER.jpg](https://s6.jpg.cm/2021/11/02/ICK0ER.jpg)

    

  - 找到**notability**，点击下载

    

  - 注意：此时Fiddler**必须打开并且处于开启https解密**

    

  - ![ICK9cD.jpg](https://s6.jpg.cm/2021/11/02/ICK9cD.jpg)

    

  ### 4.4、Fiddler设置

  

- 此刻返回抓包软件**Fiddler**，查看左侧状态栏，会看到左边的列表里会有一个iTunes的购买请求，这个请求地址以 **P** 开头 ， **P** 后面的数字可能不一样，但是其他部分每个人是一样的。

  - 点击它右边的那个**黄色框框**。因为https请求内容是加密的，点击那个来解码。

    

  - ![ICKax6.jpg](https://s6.jpg.cm/2021/11/02/ICKax6.jpg)

    

  - 按照如图所示的步骤,保存一下 iTunes购买请求的内容，保存到桌面即可。

    

  - ![ICKxlT.jpg](https://s6.jpg.cm/2021/11/02/ICKxlT.jpg)

    

### 4.5、获取软件版本号



  - 使用记事本打开刚刚保存的xml文件，可以很轻易的找到里面如图所示的内容， 由两个 integer夹着一串数字的长长的排列，它们是 **旧版app** 每个版本对应的 id数值 ，每个不同的id可以让你下载到对应的版本。版本由旧到新，最新版本为**845074337**，未更新版本为**844215920**。

    - ![IChPI2.jpg](https://s6.jpg.cm/2021/11/02/IChPI2.jpg)

​    

### 4.6、阻断apple store下载并修改版本id来获取旧版本



- 回到抓包**fiddler**软件，在那个购买请求地址下面的黑色框框输入“`bpu MZBuy.woa`”这个代码，之后按一下回车键（Enter键）,如下图所示

  - **PS: 这个是用来中断接下来的 所有包含“MZBuy.woa”字符的https 的会话。顾名思义，输入了这个代码之后，接下来iTunes下载 notability 这个app 时 的 https请求的会话会被打断。**

    

  - ![IChRUH.jpg](https://s6.jpg.cm/2021/11/02/IChRUH.jpg)

  

- 这时候返回iTunes，再次下载**notability**，但是这时候你会发现**notability**并不能下载，与此同时，fiddler软件的左侧列表里会有一个红色logo的提示，这说明 fiddler 拦截 iTunes的会话成功。如下图所示

  

  - ![IChQjw.jpg](https://s6.jpg.cm/2021/11/02/IChQjw.jpg)

  

- 点击fiddler左边的那个**红色**提示，然后看右边，点击**textview**选项卡，最新版**notability**对应的下载ID就呈现在下面的文本之中。【**不难理解，你需要将它替换成旧的版本ID：844215920，就可以下载旧版的贴吧安装包了**】，下面有个绿色按钮，点击它就可以以启动iTunes的下载。

  

  - ![IChe58.jpg](https://s6.jpg.cm/2021/11/02/IChe58.jpg)

    

### 4.7、安装旧版本app



- 下载 **itools** 或者 **爱思助手** 之类的第三方软件（iTunes也可以）将抓好的app安装包（文件路径 C:\Users\你的yhm\Music\iTunes\iTunes Media\Mobile Applications）安装到你的iPhone或者iPad，大功告成。

  

## 5、注意



1、若网速太快，还没点暂停就下载完了————请用网速管理软件限速

2、下载软件显示已完成————删除~/Music/iTunes/下所有文件，重启iTunes

3、登录账号显示错误————请关闭Fiddler软件的https解密，等登录过后在打开

4、下载的ipa包在哪里————在文件路径 C:\Users\你的yhm\Music\iTunes\iTunes Media\Mobile Applications

5、若出现无法下载，多试几遍

6、下载的app具有你账号的信息，请勿传播
