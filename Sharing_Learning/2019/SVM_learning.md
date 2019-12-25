## SVM(Support Vector Machine)


### libsvm 在Python下的安装步骤
1.  在[Libsvm](https://www.csie.ntu.edu.tw/~cjlin/libsvm/)下载Libsvm压缩包，解压在合适位置

1.  确定本机Python的版本
    打开Python ILDE，查看版本
    
    ```js
    import sys
    
    sys.version
    ```

1.  导入执行文件到*C:\Windows\System32*中

    - 如果版本为32位

    那么将*libsvm-3.24\libsvm-3.24\windows*中的*libsvm.dll*拷贝到*C:\Windows\System32*中

    - 如果版本为64位

    那么我们需要首先编译64位的动态链接库*libsvm.dll*文件的动态,首先打开*Visual studio*的*Conmmand prompt*，*cd*到*Libsvm*文件，生成动态链接库后，将生成的*libsvm.dll*文件拷贝到*C:\Windows\System32*中
    
    ```js
    cd "E:\libsvm-3.24
    nmake -f Makefile.win clean all
    ```

    如果成功会返回消息说，已经成功安装了*windows/libsvm.dll*

1.  测试
    
    ```js
    from svmutil import *
    
    os.chdir('E:\libsvm-3.24\python')
    ```
    

1.  使用svm
    
    ```js
    y,x=svm_read_problem('../heart_scale')
    
    m=svm_train(y[:200,x[:200],'-c 4'])

    p_label,p_acc,p_val=svm_predict(y[200:],x[200:],m)
    ```

### 参考文献
[SVM （一）Libsvm 在Python下的安装和使用](https://blog.csdn.net/sinat_32362701/article/details/49490193)




