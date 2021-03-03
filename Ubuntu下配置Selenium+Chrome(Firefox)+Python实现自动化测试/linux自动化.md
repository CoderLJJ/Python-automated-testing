## Ubuntu下配置Selenium+Chrome(Firefox)+Python实现自动化测试

## 1 安装ubuntu系统

- 下载ubuntu64位版本

**https://releases.ubuntu.com/16.04.7/**

记得安装ubuntu64位的版本，因为chrome浏览器32位的linux版本已经停止更新了

- 创建虚拟机

![1](C:\Users\81316\Desktop\自动化\img\1.png)

![2](C:\Users\81316\Desktop\自动化\img\2.png)

![3](C:\Users\81316\Desktop\自动化\img\3.png)

![4](C:\Users\81316\Desktop\自动化\img\4.png)

![5](C:\Users\81316\Desktop\自动化\img\5.png)

![6](C:\Users\81316\Desktop\自动化\img\6.png)

![7](C:\Users\81316\Desktop\自动化\img\7.png)

![8](C:\Users\81316\Desktop\自动化\img\8.png)

![9](C:\Users\81316\Desktop\自动化\img\9.png)

![10](C:\Users\81316\Desktop\自动化\img\10.png)

![11](C:\Users\81316\Desktop\自动化\img\11.png)

![12](C:\Users\81316\Desktop\自动化\img\12.png)

![13](C:\Users\81316\Desktop\自动化\img\13.png)

![14](C:\Users\81316\Desktop\自动化\img\14.png)

- 虚拟机中安装 ubuntu系统

![15](C:\Users\81316\Desktop\自动化\img\15.png)

![16](C:\Users\81316\Desktop\自动化\img\16.png)

![17](C:\Users\81316\Desktop\自动化\img\17.png)

![18](C:\Users\81316\Desktop\自动化\img\18.png)

![19](C:\Users\81316\Desktop\自动化\img\19.png)

![20](C:\Users\81316\Desktop\自动化\img\20.png)

![21](C:\Users\81316\Desktop\自动化\img\21.png)

![22](C:\Users\81316\Desktop\自动化\img\22.png)

![23](C:\Users\81316\Desktop\自动化\img\23.png)

#### 安装vmware tools

![24](C:\Users\81316\Desktop\自动化\img\24.png)

#### 移动到home路径下获得权限，手动解压并安装

![25](C:\Users\81316\Desktop\自动化\img\25.png)

![26](C:\Users\81316\Desktop\自动化\img\26.png)

#### 重启虚拟机

![27](C:\Users\81316\Desktop\自动化\img\27.png)

## 2 安装chrome浏览器

```
sudo apt-get install libxss1 libappindicator1 libindicator7
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome*.deb
```

如果上面运行sudo dpkg -i google-chrome*.deb命令之后报错，使用如下命令修复一下：sudo apt-get install -f,之后再次运行sudo dpkg -i google-chrome*.deb命令就可以了

![29](C:\Users\81316\Desktop\自动化\img\29.png)

#### 可以看得chrome安装成功

![28](C:\Users\81316\Desktop\自动化\img\28.png)

## 3 安装python，selenium

```
sudo apt-get install python-pip
sudo pip install selenium -i http://pypi.douban.com/simple/
```

![30](C:\Users\81316\Desktop\自动化\img\30.png)

## 4 安装chromedriver并配置到环境变量中

建议安装最新版本的chromedriver，下载页面：
**http://chromedriver.storage.googleapis.com/index.html**

在这个页面里列出了chromedriver的各个版本，因为chrome浏览器默认下载的是最新版本，我们选择目前最新的版本（2.29），使用命令行安装：

```
wget -N http://chromedriver.storage.googleapis.com/2.29/chromedriver_linux64.zip
unzip chromedriver_linux64.zip
chmod +x chromedriver
sudo mv -f chromedriver /usr/local/share/chromedriver
sudo ln -s /usr/local/share/chromedriver /usr/local/bin/chromedriver
sudo ln -s /usr/local/share/chromedriver /usr/bin/chromedriver
```

当然也可以到官网手动下载chromedriver linux64位版本驱动

**http://chromedriver.storage.googleapis.com/index.html?path=2.9/**

## 5 简单测试

手动创建py文件,linux终端输入 touch 文件名.py

```
#coding:utf-8
from selenium import webdriver
driver = webdriver.Chrome()
driver.get("https://www.baidu.com/")
```

运行py文件

python 文件名.py

可以看到

![33](C:\Users\81316\Desktop\自动化\img\33.png)

## 下载火狐浏览器驱动

- https://github.com/mozilla/geckodriver/releases下载linux64位版本驱动

- tar zxvf geckodriver-v0.29.0-linux64.tar.gz

- sudo mv geckodriver /usr/bin

- touch huohu.py

- gedit huohu.py

```
#coding:utf-8
from selenium import webdriver
driver = webdriver.Firefox()
driver.get("https://www.baidu.com")
```

- python huohu.py

可以运行成功

![35](C:\Users\81316\Desktop\自动化\img\35.png)

## 6 参考文档

- https://releases.ubuntu.com/16.04.7/
- https://blog.csdn.net/Candyys/article/details/111667584
- https://cloud.tencent.com/developer/article/1543285
- https://blog.csdn.net/Candyys/article/details/111667584
- https://blog.csdn.net/qq_48589662/article/details/107121011
- http://chromedriver.storage.googleapis.com/index.html?path=2.9/
- https://blog.csdn.net/xsfqh/article/details/89448976
- https://www.cnblogs.com/sophia201552/p/11765179.html