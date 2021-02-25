1. 安装NodeJS

   https://nodejs.org/en/  下载NodeJS并安装

2. 安装GitBook

   ```shell
   npm install -g gitbook-cli
   ```

3. 创建gitbook文件夹

   在需要创建gitbook的位置执行如下命令

   ```shell
   gitbook init
   ```

   > SUMMARY.md：目录文件
   >
   > README.md：项目说明文件

4. 编译并访问

   ```shell
   gitbook serve
   ```

   使用上述命令进行编译，会生成一个_books文件夹，访问本机4000端口或者直接访问其中的Index.html

