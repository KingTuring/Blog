## 导入模块失败
```js
import os
import sys
 
os.chdir('E:\library\LibSVM\libsvm-3.24\libsvm-3.24\python')
from svmutil import *
```
这段代码中，显示错误为：

> _ImportError: No module named svmutil_

代码中的_os.chdir()_函数使对当前文件的目录进行改变，所以排查错误时

1. 将当前目录输出检查_os.chdir()_是否成功对当前目录进行了改变（确实成功对当前目录进行了改变）

2. 试着读取当前目录下的文件，看是否可以对文件进行读取（确实可以对文件进行读取）

3. 试着对其他模块进行操作

* 最后发现问题是：

当要使用一个_Module_需要先将其路径导入到_sys.path_中，_sys.path_是_python_搜索模块的路径集，是一个_list_列表

* 解决方法

在_python_环境下使用_sys.path.append(path)_添加相关的路径，但是在退出_python_环境后自己添加的路径就会自动消失

* 代码如下

```js
import sys
sys.path.append('E:\library\LibSVM\libsvm-3.24\libsvm-3.24\python')
from svmutil import *
```
* 参考资料

[Python 之 LIBSVM 使用小结（二）](https://blog.csdn.net/u013630349/article/details/47322303)

## pip安装时出现了未找到Pip模块
想要安装_Matplotlib_模块，打开了_Python_命令行，在其中输入
```js
pip install matplotlib
```
* 出现错误

> NameError: name 'pip' is not defined

* 错误原因：

1. 平常在使用命令行时，指令是有他默认的文件地址的，如果进去时是
  ```js
  c:user\***\python
  ```
  那么其实说明你已经进入了_Python_这个软件中去了，所以不可以再_pip_模块了，因为_pip_并不是_Python_环境中的模块

1. 我们在使用命令行时，需要在系统环境变量中添加要使用的文件或者模块的地址，这样才可以直接使用
  
   而_pip_模块其实就相当于一个小的插件、小的软件，并非只能绑定在_Python_上使用，他只是帮助_Python_运行的更好的一个另一个独立软件，并且它的执行存在于_Script_文件路径中，而我们配置环境变量时，对应的是系统的命令行，所以我们操作_pip_时应该用的是系统自带的命令行，如果想用_Python_的，那么应该先配置才对。 

* 参考资料

[python pip NameError：name 'pip' is not defined](https://blog.csdn.net/weixin_33724059/article/details/86004694)
[NameError: name 'pip' is not defined 使用pip时报错](https://blog.csdn.net/qq_41800366/article/details/86066496)
