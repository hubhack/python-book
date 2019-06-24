vim配置

```shell
git clone https://github.com/Python-project-aggregate/vimrc.git
```

第二步:脚本安装

```shell
sh setup.sh
```

安装oh-my-zsh

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



