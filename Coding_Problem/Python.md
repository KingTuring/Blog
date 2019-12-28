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

*当要使用一个*_Module_*需要先将其路径导入到*_sys.path_*中，*_sys.path_*是*_python_*搜索模块的路径集，是一个*_list_*列表*

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