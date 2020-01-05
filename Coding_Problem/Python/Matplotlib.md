### Introduction

Matplot是Python的一个绘图库。可以使用它来进行函数的绘制以及对数据进行可视化工作。

### 折线图

```js
import matplotlib.pyplot as plt
import numpy as np
x = np.array([1,5,10,12,15,18,20,22,26])
y = np.array([50,100,120,140,150,170,172,174,174])

#plt.plot(x, y,'g',linewidth=2,linestyle='--') #虚线
plt.plot(x, y,'b',linewidth=2,linestyle='-') #实线
plt.show()
```

单条线画法：plot([x], y, [fmt], data=None, **kwargs)
* []代表参数为可选参数，x:横坐标，y：纵坐标，fmt：基本属性字符串
* 形式：fmt = '[color][marker][line]'（color：颜色，marker：点型，linestyle：线型）当属性用的是全名就不可以用fmt参数来组合，应该用关键字参数对单个属性赋值

举例：
1. 
 ```js
 plot(x, y, 'bo-')  # 蓝色圆点实线
 ```

1. 
 ```js
 plot(x,y2,color='green', marker='o', linestyle='dashed', linewidth=1,markersize=6)

 plot(x,y3,color='#900302',marker='+',linestyle='-')    
 ```

### 函数图

```js
import matplotlib.pyplot as plt
import numpy as np 

def function():
    x = np.linspace(0,2*np.pi,50)

    siny = np.sin(x)
    cosy =np.cos(x)
    y = 0*x
    plt.plot(x,siny,label = "sin")
    plt.plot(x,cosy,'r',label = 'cos')
    plt.plot(x,y,'g')
    
    #设置说明框
    legend = plt.legend(loc='best', shadow=True)
    frame = legend.get_frame()
    frame.set_facecolor('0.90') #frame的颜色
    
    plt.show()
    
function()
```

### 柱状图

```js
def barPicture() :
    #简单画法
    x = np.array(range(1,13))
    y = np.array([2,5,15,18,20,27,30,31,32,25,17,10])
    plt.bar(x,y,0.8, color = 'y')
    plt.xlabel("month")
    plt.ylabel("temp")
    plt.ylim(0,38)
    for x1, y1 in zip(x,y):
        plt.text(x1,y1+0.1,'%.2f' %y1, ha = 'center',va = "bottom")
    plt.show()
barPicture()
```

### 直方图

```js
    p = np.random.rand(1000)
    plt.hist(p,bins=30,color='g',edgecolor='k')
    plt.show()
```

### 散点图

```js
import numpy as np
import matplotlib.pyplot as plt

x = np.random.normal(0,1.0,1024)
y = np.random.normal(0,1.0,1024)
print(x)
print(y)
color = np.arctan2(y, x)
plt.scatter(x, y, s=30, alpha=0.8, c=color)  #s 表示圆点的大小
# 设置坐标轴范围
plt.xlim((-1.5, 1.5))
plt.ylim((-1.5, 1.5))

# 不显示坐标轴的值
plt.xticks(())
plt.yticks(())
plt.show()
```

### 等高线

```js
x = np.linspace(-3, 3, 256)
y = np.linspace(-3, 3, 256)

# 生成网格线
X, Y = np.meshgrid(x, y)
Z =X**2 + Y**2
plt.contourf(X, Y, Z, levels=8, alpha=0.75, cmap=plt.cm.gist_earth)
# 绘制等高线
C = plt.contour(X, Y, Z, 8, colors='red')
# 添加数值
plt.clabel(C, inline=True, fontsize=10)
plt.show()
```

### 3D立体图

```js
import numpy as np
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D
x = np.arange(-5, 5, 0.25)
y = np.arange(-5, 5, 0.25)

X, Y = np.meshgrid(x, y)

# 计算每个点对的长度
R = np.sqrt(X**2+Y**2)
# 计算Z轴的高度
Z = np.sin(R)

fig = plt.figure()
ax = Axes3D(fig)

ax.plot_surface(X, Y, Z, rstride=1, cstride=1, cmap=plt.get_cmap('rainbow'))


ax.contour(X,Y,Z,zdim = 'z',offset=-2,cmp = "rainbow")
ax.set_zlim(-2,2)
plt.show()
```

### color参见参数

```js
=============    ===============================
    character        color
    =============    ===============================
    ``'b'``          blue 蓝
    ``'g'``          green 绿
    ``'r'``          red 红
    ``'c'``          cyan 蓝绿
    ``'m'``          magenta 洋红
    ``'y'``          yellow 黄
    ``'k'``          black 黑
    ``'w'``          white 白
    =============    ==============================
```

### Marker常见参数

```js

=============    ===============================
    character        description
    =============    ===============================
    ``'.'``          point marker
    ``','``          pixel marker
    ``'o'``          circle marker
    ``'v'``          triangle_down marker
    ``'^'``          triangle_up marker
    ``'<'``          triangle_left marker
    ``'>'``          triangle_right marker
    ``'1'``          tri_down marker
    ``'2'``          tri_up marker
    ``'3'``          tri_left marker
    ``'4'``          tri_right marker
    ``'s'``          square marker
    ``'p'``          pentagon marker
    ``'*'``          star marker
    ``'h'``          hexagon1 marker
    ``'H'``          hexagon2 marker
    ``'+'``          plus marker
    ``'x'``          x marker
    ``'D'``          diamond marker
    ``'d'``          thin_diamond marker
    ``'|'``          vline marker
    ``'_'``          hline marker
    =============    ===============================
```

### linstylr常见参数

```js
=============    ===============================
    character        description
    =============    ===============================
    ``'-'``          solid line style 实线
    ``'--'``         dashed line style 虚线
    ``'-.'``         dash-dot line style 点画线
    ``':'``          dotted line style 点线
    =============    ===============================

```