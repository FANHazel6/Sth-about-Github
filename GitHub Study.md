**GitHub Study**

U will learn:      

1. How to create a <u>new repository</u>.
2. How to generate <u>SSH keys.</u>
3. <u>Settings Configuration</u> (user name and email)
4. <u>git clone</u>
5. <u>git branch</u>
6. uploads local files to the specified branch.



​	--continuous updating--



1. **Create a new repository**

   **Method 1：**

   Download GitHub <u>Desktop</u>: [GitHub Desktop | Simple collaboration from your desktop](https://desktop.github.com/)

   File --> New Repository

   **Method 2：**

   GitHub <u>Website</u>:

   ![image-20210813015840536](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210813015840536.png)

2. **Generate SSH keys**

   If u don't <u>download git</u>, go and download it. [Git - Downloads (git-scm.com)](https://git-scm.com/downloads)

   If u don't sign up in GitHub, please get a GitHub account. (<u>Do not</u> use QQ email to sign up!) 

   ----咳咳，装b结束----

   1)检查一下是否已经有SSH keys

   运行git bash 客户端（Shift+F10+“s"+"Enter", 或者直接在桌面上，右键鼠标点击)，输入：

   $  ls -al ~/.ssh

   如果有文件 id_rsa.pub 或id_dsa.pub，则直接进入Step3将SSH key添加到GitHub中，否则进入Step 2，生成SSH key。

   2)生成新的SSH key

   ①生成public/private rsa key pair

   在命令行中输入ssh-keygen -t rsa -C "your_email@example.com"

   （默认会在相应路径下C:\Users\user生成id_rsa和id_rsa.pub两个文件）

   ②输入passphrase（直接回车Enter**“3次”**）

   收到如下代码提示，则说明SSH key创建成功。

   ```
   Your identification has been saved in /c/Users/you/.ssh/id_rsa.
   # Your public key has been saved in /c/Users/you/.ssh/id_rsa.pub.
   # The key fingerprint is:
   # 01:0f:f4:3b:ca:85:d6:17:a1:7d:f0:68:9d:f0:a2:db your_email@example.com
   ```

   3）将SSH key添加到GitHub中

   用任意一个编辑器打开id_rsa.pub文件，将里面的信息（SSH key）复制到GitHub的New SSH key页面即可。

   ![image-20210813162347664](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210813162347664.png)

   4）测试一下这个SSH key

   在git Bash中输入以下代码：

   $ ssh -T git@github.com

   ![image-20210813162751407](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210813162751407.png)

   如果出现上面这段话并且用户名是正确的话，恭喜你已经成功设置SSH key！如果你看到“access denied”，则表示拒绝访问，那么你需要用https去访问，而不是SSH。

3. **设置配置（用户名和邮箱）**

   $ git config --global user.name 你的英文名   #此英文名不需要跟GitHub账号保持一致

   $ git config --global user.email 你的邮箱    #此邮箱不需要跟GitHub账号保持一致

   安装好git后，在命令行或终端中使用下面的命令可以设置git自己的名字和电子邮件。这是因为Git是分布式版本控制系统，所以，每个机器都必须自报家门：你的名字和Email地址。
   注意git config命令的--global参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。

4. **git clone**命令

   **git clone** 拷贝一个 Git 仓库到本地，让自己能够查看该项目，或者进行修改。

   拷贝项目命令格式如下：

   ```
   $ git clone [url]
   ```

   **[url]** 是你要拷贝的项目。

   例如我们拷贝 GitHub 上的项目：

   $ **git clone** https:**//**github.com**/**FANHazel6**/**git-test
   Cloning into 'git-test'...
   remote: Enumerating objects: 12, done.
   remote: Total 12 **(**delta 0**)**, reused 0 **(**delta 0**)**, pack-reused 12
   Unpacking objects: 100**%** **(**12**/**12**)**, done.

   拷贝完成后，在当前目录下会生成一个 git-test 目录：

   ```
   $ cd simplegit/
   $ ls
   README.md     test.txt
   ```

5. git branch分支管理

   创建分支命令：

   ```
   git branch (branchname)
   ```

   切换分支命令:

   ```
   git checkout (branchname)
   ```

   我们也可以使用 git checkout -b (branchname) 命令来创建新分支并立即切换到该分支下，从而在该分支中操作。

   ```
   $ git checkout -b newtest
   Switched to a new branch 'newtest'
   ```

   删除分支命令：

   ```
   git branch -d (branchname)
   ```

6. git 把本地文件上传到指定分支中

   查看当前分支

   > git branch -a

   如果当前不在自己想要的分支上，则：

   > git checkout 想要操作的分支

   将本地文件复制到该分支下，然后：

   > git add 
   > git commit -m “你的注释”
   > git push -u origin 想要操作的分支

   （git commit --all → 进入编辑模式。

   其中，a是插入编辑，esc是命令模式，编辑模式下完成版本说明后，按esc，再输入“shift”+“:”，左下角会出现“:"，再输入wq，再Enter即可。)

   

   