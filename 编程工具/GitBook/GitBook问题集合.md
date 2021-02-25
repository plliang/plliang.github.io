# Error: ENOENT: no such file or directory

这是GitBook已知的一个问题，解决方案如下：

1. 找到`copyPluginAssets.js`文件地址

   `C:\Users\MockingBird\.gitbook\versions\3.2.3\lib\output\website\copyPluginAssets.js`

2. 将`copyPluginAssets.js`文件中所有的`confirm`值修改为`false`

3. 重新执行`gitbook serve`即可



**参考文档**

[1]. [gitbook serve后报错：:Error: ENOENT: no such file or directory……/_book/gitbook/gitbook](https://www.cnblogs.com/liuting-1204/p/12742830.html)

