## 域名绑定
1. 购买域名，百度云、腾讯云、阿里云均可选择。

1. 域名解析
   * 阿里云->登陆->我的域名->解析->快速添加网站/邮箱解析
   * 打开命令行（win+R）->cmd->_ping -----.github.io_->可以看到github对应的主机的地址->将该地址添加至上一步的“快速添加网站/邮箱解析”
   * 两个主机记录@和www->将www的记录类型更改为CNAME->将记录值更改为_-----.github.io_
  
1. Github相应更改
   * 在_-----.github.io/Blog/_添加文件（命名为CNAME,文件不要添加后缀）->文件中写www.---.--
   * setting->Repositories->_-----.github.io_
   * _Customm domain_->_www.---.--_->_save_

1. 绑定成功

### 参考资料
[Github个人博客：绑定域名](https://blog.csdn.net/heimu24/article/details/81159099)