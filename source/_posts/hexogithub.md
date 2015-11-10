title:hexo+github搭建个人blog详细教程
---
###github page 搭建博客

1、点击“New repository”，新建一个版本库
2、输入Repository name:yourname.github.io(yourname与你的注册用户名一致,这个就是你博客的域名了)
3、点击“create repository”
4、点击右边的“Setting”菜单进入设置,点击“Launch automatic page generator”
5、点击底部的”Continue to layouts”
6、最后点击”Publish page”,发布github默认生成的一个静态站点
7、验证邮箱
此时就可以访问yourname.github.io了。

###安装hexo

1、git bash 进入命令窗口 
  
  ```javascript
      npm install -g hexo-cli
  ```
  ```javascript
      npm install hexo --save
  ```
2、安装完成后，在输入命令，验证是否安装正确
  
  ```javascript
      hexo -v
  ```
3、本地运行hexo
 
  ```javascript
      hexo init
  ```
  ```javascript
      npm install
  ```
  ```javascript
      hexo g
  ```
  ```javascript
      hexo s
  ```
  在浏览器中输入http://localhost:4000，就能看到个人blog了。
  
###hexo+github联调
  
 1、 打开blog/_config.yml文件，进行配置
    ```javascript
      url: http://yourname.github.io
    ```
    ```javascript
       deploy:
            type: git
            repository: https://github.com/yourname/yourname.github.io.git
            branch: master
    ```
2、设置git身份信息
    ```javascript
        git config --global user.name "你的用户名"
        git config --global user.email "你的邮箱"
    ```
3、安装hexo git插件
    ```javascript
        npm install hexo-deployer-git --save
    ```
4、发布更新博客

  ```javascript
      hexo g
  ```
  ```javascript
      hexo d
  ```
###hexo+github 多pc同步
1、删除文件夹内原有的.git 缓存文件夹

2、初始话仓库
  ```javascript
     git init
     git remote add origin <server> git@github.com:yourname/name.git
  ```
  如果删除remote link
   ```javascript
     git remote rm origin 
  ```
3、添加本地文件到仓库并同步到git上
 ```javascript
     git add .
     git commit -m "description"
     git push -u origin master
  ```
  在执行这步之前一定要注意检查下.gitignore文件的内容，看看是否正确的把一些文件夹忽略掉了。如果加错了的话可以用
  ```javascript
     git rm -r --cached .
  ```
  撤销添加操作
  
4、将git的内容同步到本地
  ```javascript
     git init
     git remote add origin <server>
     git fetch --all
     git reset --hard origin/master
  ```
5、以后操作只需要
  ```javascript
     git push //推送到远程仓库
  ```
  ```javascript
     git pull //从远程仓库同步文件
  ```
More info: [关于我](http://sdbzlsm.github.com)
