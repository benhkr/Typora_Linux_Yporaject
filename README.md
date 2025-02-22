## TYpora 最新版激发教程

> Yporainject（[复制自 NodeInject 项目 Copy from repo NodeInject](https://github.com/DiamondHunters/NodeInject)）

> **[查看 Node_inject 项目说明书 See the README of that repo](./NodeInject_README.md)**
>
> 作者：叶月绘梨依
> 日期：2023年6月10日
---

<span color="red">
该方法无法支持 最新版本 1.10，请注意安装包版本号！
</span>

#### 已通过测试平台(来自原项目 Node_inject)
- [x] Windows
- [x] Ubuntu
- [ ] MacOs
> Since macos may adopt different packaging methods and webkit as the execution environment, this tool does not support applications under macos.
#### 本仓库使用到的开源项目
- [Node_inject](https://github.com/DiamondHunters/NodeInject)
- [Node_inject_example](https://github.com/DiamondHunters/NodeInject_Hook_example)

### **[怎么提问 how to issue](./issue_template.md)**

请您提问之前，请自行确认:
- 尝试通过网络解决遇到的问题，你确信网络不能解决你的问题
- 确定已有的 **issue** 不能解决你的问题
- 确定 **issue** 按照如下格式: [问题]: 问题描述

**请您按照提问模板填写(文件位于仓库 issue_template.md)<br/>
谢谢您的配合，祝您生活愉快!**


---

## 最新方法
**激活时请勾选国内服务器，否则会激活不成功**
**特别提示：** 当前两个脚本可能有不完备的地方，使用时请格外注意
#### 1. 使用 [`Python 脚本 inject.py`](./inject.py)
```bash
# 在当前项目目录下(Yproject)
python inject.py
```
#### 2. 使用 [`Bash 脚本 inject.sh`](./inject.sh)
```bash
# 在当前项目目录下(Yproject)
./inject.sh
```
![inject.sh 使用效果图](./img/image-202405070106.png)



### **Windows 平台**

**当前仅在 win10 下 powershell(管理员运行模式) 测试通过,可能仍有不足之处**
**使用前，请谨慎通读脚本，或备份 typora 安装包以便重新安装**

[GBK 编码版批处理文件 inject_gbk.bat ](./inject_gbk.bat) 

[UTF 编码版批处理文件 inject_utf.bat ](./inject_utf.bat)

```bash
# 请 搜索 powershell,并以管理员权限运行

## 以下均假定在 管理员模式 powershell 终端下运行!!
# 移动至当前项目处
# 比如 当前项目为 D:\Yproject

d: #切换到 D 盘
cd Yproject # 移动到相关目录
.\inject_gbk.bat
```



**脚本依赖要求**: 以上脚本均依赖 node 运行库, 故请安装 node(亦可通过 nvm 管理器安装 node)

```bash
#arch 
sudo pacman -S nodejs
#ubuntu
sudo apt install nodejs

#windows
#请先安装 nodejs
# 推荐：https://github.com/coreybutler/nvm-windows
# 或者参考：https://zhuanlan.zhihu.com/p/442215189
# 找到安装路径下的node.exe，复制路径
# 然后更改 inject_gbk.bat或 inject_utf.bat 中的 NODE_INSTALLED_PATH 值

```



#### 3. 若不想使用以上两个脚本，或使用以上脚本运行失败者，则请参照 **原方法** 进行。

**注意**：license_code 文件内置有已经生成的序列码，可直接使用。若出现意外，那么还请安装 rust 环境，并通过以下步骤以获得激活序列：

```bash
# 假设您已经在 Yproject 目录下
# 并成功配置 rust 环境
cd ./license-gen
cargo build
./target/debug/license-gen
输出 License for you: xxxxxx...
```


---





## 原方法

#### 1. 下载最新版 Typora 安装包

- [前往 Typora 中文官网下载](https://typoraio.cn/releases/all)

- 在终端下输入以下命令直接下载(我电脑是 X86 架构的，请根据自己电脑自行选择)

  ```bash
  # 查看电脑架构
  uname -m
  
  # 下载 Typora 安装包
  # X86(Amd) 架构 
  wget https://download2.typoraio.cn/linux/typora_1.7.4_amd64.deb --output-document typora.deb
  
  # Arm 架构
  wget https://download2.typoraio.cn/linux/typora_1.7.4_arm64.deb --output-document typora.deb
  
  # 安装 Typora 软件包
  sudo dpkg -i typora.deb
  ```

  

#### 2. 克隆 Yporaject 项目

可以直接克隆本项目仓库(本项目对原两个项目进行了合并)，好处是一键编译即可，坏处是本项目并未和原项目代码同步

```bash
# 可以直接克隆本项目的仓库, depth=1 表示仅克隆最新版本,以减少等待时间
git clone https://github.com/hazukieq/Yporaject.git --depth=1
```

或者克隆原项目仓库

```bash
# 原项目仓库, depth=1 表示仅克隆最新版本,以减少等待时间
git clone https://github.com/DiamondHunters/NodeInject --depth=1 

git clone https://github.com/DiamondHunters/NodeInject_Hook_example --depth=1

# 建立 Yproraject 文件夹
mkdir Yporaject

# 将两个项目资源合并
# 将 NodeInject 项目代码复制到 Yproraject 文件夹
cp NodeInject/* Yporaject -r

# 将 NodeInject_Hook_example/hook.js 复制到 Yporaject/src 文件夹
cp NodeInject_Hook_example/hook.js Yporaject/src

# 将 NodeInject_Hook_example/license_gen 文件夹复制到 Yporaject 文件夹
cp NodeInject_Hook_example/license_gen Yporaject -r
```



#### 3. 配置 Rust 编译环境

由于编译项目需要 **Rust** 的支持，所以我们需要配置相关环境(若已有，则可跳过该步骤)

```bash
# 运行官方脚本安装即可
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

# 检查 cargo，若看到如下版本信息，则说明配置成功
cargo -V
cargo 1.70.0 (ec8a8a0ca 2023-04-25)
```

注：若安装过程中出现其他问题，请自行网上搜索相关安装教程，关键字 `ubuntu ` `cargo  ` `rust`   `install`



#### 4. 编译 Yporaject 项目

```bash
# 进入 Yporaject 项目
cd Yporaject
# 运行编译命令
cargo build
# 查看二进制是否生成,程序名称为 node_inject
ls target/debug
# 尝试运行该二进制程序
cargo run
output: 
no node_modules.asar found
move me to the root of your typora installation(the same directory as executable of electron)
```

请务必确认当前项目目录 **target/debug 下** 是否生成了 **node_inject 二进制程序**



#### 5. 复制二进制程序到安装目录下

```bash
# 记录当前目录路径，待会返回需要用到
cur=`pwd`

# 复制二进制程序到相关目录下
sudo cp target/debug/node_inject /usr/share/typora
# 进入相关目录
cd /usr/share/typora
# 给予二进制程序执行权限
sudo chmod +x node_inject

# 运行二进制程序
# (请注意程序运行输出信息，观察是否运行成功！！)
# 若无读写权限,建议使用 sudo ./node_inject
sudo ./node_inject
```



#### 6. 获取许可证激发码

```bash
# 返回项目
cd $cur
# 进入 license-gen 文件夹
cd license-gen
# 编译代码
cargo build
# 运行二进制程序
cargo run
# 你将会得到以下输出
output:
    Finished dev [unoptimized + debuginfo] target(s) in 0.00s
     Running `target/debug/license-gen`
License for you: xxxxxx-xxxxxx-xxxxxx-xxxxxx
```

复制 **License for you: xxxxxx-xxxxxx-xxxxxx-xxxxxx** 的那一串激发码，待会需要用到

#### 7. 激活软件

```bash
#运行 Typora (你也可以在桌面上点击相关图标)
typora &
```

依次点击界面上方菜单栏选项 **help > my license(帮助 > 我的许可证...)** 

![image-20230611002616301](./img/image-20230611002616301.png)





![image-20230611002645270](./img/image-20230611002645270.png)



邮箱可以随便填

然后在第二输入框中，**粘贴刚才得到的激发码**

点击 `激活` 按钮后，你将会看到以下界面



![image-20230611002933127](./img/LICENSE.png)



#### 结语

经过几番查找，好多教程都不怎么符合我的需求，且在 `CSDN` 等平台上各种转载、胡乱复制的帖子...看得真是心累。不知是不是由于我用的软件比较新的缘故， 比如 **poraCracker 就没有用。后面看到了NodeInject这个项目，我抱着尝试的态度按照项目指南操作，没想到竟然真的激活成功了。为了以后自己能想起这个方法，特此记录。



##### 参考资料

1. [**(Linux/Windows) Typora 理论多版本兼容破解方案**](https://www.52pojie.cn/thread-1710146-1-1.html)
2. [RUST 安装](https://www.rust-lang.org/zh-CN/learn/get-started)
