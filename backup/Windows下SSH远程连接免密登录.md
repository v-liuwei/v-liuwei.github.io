## Step1: 生成SSH密钥

> [!NOTE]
> 如果你的用户目录（`C:\Users\xxxxxx\`）下的`.ssh`文件夹内已经有`id_rsa`文件，你可能曾经生成过密钥了，可以跳过这一步。

打开cmd，输入如下命令：
```cmd
ssh-keygen
```
然后它会提示你将要生成的密钥文件放在什么位置等等，不用管，一路按回车就好。

## Step2: 将生成的公钥上传到远程服务器上

将刚才生成的`id_rsa.pub`文件的内容写入服务器上的`~/.ssh/authorized_keys`文件中。

你可以手动复制过去，也可以可以在cmd里输入如下命令来完成：
```cmd
type %USERPROFILE%\.ssh\id_rsa.pub | ssh {USER}@{HOST} -p {PORT} "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"
```
注意分别将命令中的`{USER}`, `{HOST}`, `{PORT}`替换为{% label 你的用户名 %}、
{% label 服务器的IP地址 %}、{% label 服务器的端口号 %}（如果你不知道端口号，那么可能是默认的`22`）。

输入命令后回车并输入你在服务器上的密码，**输入密码是看不到回显的**，输入完回车就好。如果你没有看到任何输出，则说明设置成功了。
