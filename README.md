# libcurl_test
libcurl库使用demo

若编译不通过，改为x86再编译



libcurl动态库及动态库Windows下编译使用步骤：

1 git clone git@github.com:curl/curl.git 下载源代码

2 进入projects文件夹，双击运行generate.bat，等待批处理命令执行完。

3 进入projects\Windows文件夹，编译器为vs2019则继续进入projects\Windows\VC14.10文件夹，双击打开curl-all.sln。

4 点击确定

![1654142164043](C:\Users\WangJian\AppData\Roaming\Typora\typora-user-images\1654142164043.png)

5 单击选中libcurl，编译选项选中DLL Release，右键libcurl项目，点击生成。

![1654142220891](C:\Users\WangJian\AppData\Roaming\Typora\typora-user-images\1654142220891.png)

6 libcurl.lib和libcurl.dll已生成，拷贝出来。

![1654142434269](C:\Users\WangJian\AppData\Roaming\Typora\typora-user-images\1654142434269.png)

7 vs2019创建新项目->c++空项目，在项目路径下新增include和lib两个文件夹，把curl\include下的内容拷贝进来，删掉除了h文件之外的内容。lib文件夹里放刚刚生成的libcurl.lib。

![1654149837024](C:\Users\WangJian\AppData\Roaming\Typora\typora-user-images\1654149837024.png)

修改工程属性，包含目录和库目录，添加刚刚的include文件夹和lib文件夹（注意使用相对路径，别使用绝对路径，否则在别人电脑跑不起来），然后链接器-输入-附加依赖项添加libcurl.lib，然后把libcurl.dll拷贝到EXE运行目录下，就可以运行成功了。