#### 一、首先，官网下载python3的所需版本。

[wget https://www.python.org/ftp/python/3.6.0/Python-3.6.0.tgz](https://www.python.org/ftp/python/3.6.0/Python-3.6.0.tgz)

想下载到那个文件夹下就先进入到那个文件夹下——cd /home/download

#### 二、然后，解压缩文件

tar -xvf Python-3.6.0.tgz

#### 三、创建安装文件的路径。

mkdir /usr/local/python3

#### 四、编译。

./configure --prefix=/usr/local/python3

#### 五、安装。

1、make

2、make install

3、完毕

#### 六、创建新版本的软连接。

1、修改旧版本

mv /usr/bin/python /usr/bin/python_bak

2、创建新的软连接

ln -s /usr/local/python3/bin/python3 /usr/bin/python

3、检查python的版本

python -V

python-3.6.0

软连接创建成功

#### 七、配置成功后，pip3用不了，需进一步配置。

1、PATH=$PATH:$HOME/bin:

2、PATH=$PATH:$HOME/bin:/usr/local/python3/bin

3、完成

这时pip3就可以使用了。

pyenv

创建虚拟环境

```shell
$ pip install virtualenv
$ virtualenv venv  #创建一个venv名字的虚拟环境
$ source venv/bin/activate  #激活虚拟环境
$ virtualenv -p /usr/bin/python3 venv  # -p参数指定Python解释器程序路径
$ deactivate  # 退出虚拟环境
$ rm -rf venv  # 删除虚拟环境
```

 使用虚拟环境

```python
$ pyenv virtualenv 2.7.10 env-2.7.10  # 创建虚拟环境
$ pyenv activate env-2.7.10  # 激活虚拟环境
$ pyenv deactivate  # 退出虚拟环境
$ pyenv uninstall env-2.7.10 # 删除虚拟环境
$ rm -rf ~/.pyenv/versions/env-2.7.10  #删除真实目录
```

```shell
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.bashrc
source .bashrc 
```

```shell
pyenv versions

pyenv global 3.6.8

virtualenv venv 

source venv/bin/activate
```



vim配置

安装neovim

```shell
yum install neovim
```

第一步:下载

```shell
git clone https://github.com/Python-project-aggregate/vimrc.git
```

第二步:脚本安装

```shell
sh setup.sh
```

**安装oh-my-zsh**

查看当前环境shell

```shell
echo $SHELL
```

查看系统自带那些shell

```shell
cat /etc/shells
```

安装zsh

```shell
yum install zsh
```

将zsh设置为默认shell

```shell
chsh -s /bin/zsh
```

安装oh-my-zsh

自动安装

```shell
wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | sh
```

zsh主题

```shell
ls ~/.oh-my-zsh/thems
```

编辑`~/.zshrc`文件，将`ZSH_THEME="candy"`,即将主题修改为`candy.我采用的`agnoster

安装node

```shell
curl -sL https://rpm.nodesource.com/setup_10.x | bash -
yum install -y nodejs
```

安装tldr

```shell
npm install -g tldr
```



