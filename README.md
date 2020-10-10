# Android布局的知识点汇总
Android各大组件
Activity Server (服务)        BroadCastReceive(广播)         ContentProvider(内容提供者)
-----------------------------------------------------------------------------------------------


Android基本
src Java源码
gen 自动生成的java文件
R.java （Resource）静态内部类
assets 资产 包括：音频、视频、 比较大的、不需要修改
不会在R.java中自动生成，它的访问必须通过路径
bin 二进制的文件(Apk)
----------------------------------------------------------------------------------------


res Resource 资源
drawable _hipi 高分辨率的图片
drawable_ldpi 低分辨率的图片
drawable_mdpi 中分辨率的图片
drawable_xhdpi 超高清辨率的图片
drawable_xxhdpi 特高清分辨率的图片


layout 布局 
XMl的文件,高速Activity要显示什么样的内容
menu 菜单 xml文件 安卓底层用到的解析都是(PULL解析) 
values 数据文件 没有对应的静态的内部类
dimens.xml 尺寸
string,xml 常量值 
styles.xml 样式
values-sw7200dp 横屏 一般后缀加(-L)
AndroidMainfest.xml 项目清单文件.(包含以下关键字)
package: 包名 应用程序的唯一标识符
android:versionCode: 当前版本号
application: 
android:icon 图标 
android:label 名称
android:theme 样式
<activity></activity> 当前activity的路径
<!-- --> 注释格式
<intent-filter></intent-filter> 程序入口(意图 过滤器)
----------------------------------------------------------------------------------------


DVM和JVM的比较
1,编译后的文件不同
2,基于的架构不同
3,.class的文件存在很多重复信息, .dex工具会去除重复的信息. 
----------------------------------------------------------------------------------------


四,Android的布局
-res/layout/存放的是 .xml 的布局文件,告诉Activity应该显示那些内容
----------------------------------------------------------------------------------------


1,线性布局 LinearLayout (垂直方向 和 水平方向)
分水平和垂直两个方向：horizontal / vertical
如设置线性布局控件竖直方向放置 android:orientation=”vertical”
在线性布局中实现控件位于整个屏幕的正中央
除了设置宽高全屏外，还得有这句 android:gravity=”center” 设置重心
如果放置在正中央的控件不止一个，默认所有控件是水平放置的
-android:layout_width="match_parent" 设置布局的宽度(通用属性)(长度宽度的值都设为dp)
android:layout_height="match_parent" 设置布局的高度(通用属性)
属性值:match_parent 填充父容器的宽度和高度
fill_parent 填充父容器的宽度和高度(2.2之前的版本)
wrap_content 包裹内容的宽度和高度
-android:orientation="" 设置线性布局的排列方式
属性值:vertical 垂直排列
horizontal 水平排列(默认的) 
<!-- android:text 显示内容
在String.xml 中增加的常量值;
1,java代码中引用:R.string.名称
2,xml中引用:@string/名称 
-->
-android:gravity 父容器内所有子控件的位置
android:gravity="bottom|right" 多个属性直接必须"|"分割
-android:layout_weight 权重 (子控件在父容器剩余空间中所占的比例) 
属性值越大,所占的比例值就越大 
----------------------------------------------------------------------------------------


2,相对布局 RelativeLayout 指子控件与父容器,控件与控件 相对位置的来进行布局
-子控件相对于父容器的位置
控件在不做任何处理时，默认放置在左上角
常用的
layout_margin+Left/Right=”xxdp” 设置控件在布局中距离左边/右边多少个dp的距离
layout_alignParentBottom=”true” 设置控件显示在布局的底部左下角
*注意：如果用layout_marginBottom来设置控件放在底部是不能成功的
layout_align+Left/Right/Top/Bottom=”@id/某一个控件的id值” 设置该控件与给定id的控件左/右/上/下方对齐
layout_toLeft/RightOf=”@id/某一个控件的id值” 设置控件在给定id的控件的左/右方
/*
英文解释
align adj. 对齐的
margin n. 边缘
*/ 居中对齐:
android:layout_centerHorizontal="true" 子控件相对于父容器水平居中
android:layout_centerVertical="true" 子控件对于父容器垂直居中
android:layout_centerInParent="true" 子控件相对于父容器相对居中

位置对齐:
android:layout_alignParentrRight="true" 子控件相对于父容器的右边对齐
android:layout_alignParentLeft="true" 子控件相对于父容器的左边对齐
android:layout_alignParentBottom="true" 子控件相对于父容器的底部对齐
android:layout_alignParentTop="true" 子控件相对于父容器的顶部对齐
-子控件与兄弟控件之间的位置
放置的位置:
android:layout_toRightOf="@id/对应定义的ID名" 子控件显示在ID为对应Id的右侧
android:layout_toLeftOf="@id/button_id" 子控件显示在ID为button_id的左侧
android:layout_below="@id/button_id" 子控件显示在ID为button_id的下方
android:layout_above="@id/button_id" 子控件显示在ID为button_id的上方
对齐的方式:
android:layout_alignRight="@id/button_id" 子控件与ID为button_id的右边对齐
android:layout_alignLeft="@id/button_id" 子控件与id为button_id的左边对齐
android:layout_alignButton="@id.button_id" 子控件与id为button_id的下部对齐
android:layout_alignTop="@id/button_id" 子控件与id为button_id的上方对齐
android:layout_alignBaseLine="@id/button_id" 子控件与Id为button_id的基准线对齐
-外间距(margin)所有组件通用的属性
android:layout_marginRight="30dp" 右边距
android:layout_marginLeft="30dp" 左边距
android:layout_marginTop="30dp" 上边距
android:layout_marginBottom="30dp" 下边距
android:layout_margin="30dp" 四个方向边距
-内边距(padding)所有的组件通用的属性
android:;paddingRight="10dp" 控件内部元素距离右侧的尺寸
android:;paddingLeft="10dp" 控件内部元素距离左侧的尺寸
android:;paddingTop="10dp" 控件内部元素距离顶部的尺寸
android:;paddingBottom="10dp" 控件内部元素距离底部的尺寸 ---------------------------------------------------------------------------------------- 
3,帧布局 (FrameLayout) 每个组件都为一帧,当前子控件会覆盖前一个子控件
实现显示的文字不可复制——就是在整个布局或者有文字上方的添加一层“透明的”布局
设置 visibility=”invisible” 则这一层就默认不显示出来了
----------------------------------------------------------------------------------------


4,表格布局
需要设置每一行的显示，即TableRow
还有一种是不显式地指定控件宽度，而用权重来控制控件在界面中占多少分量
layout_width=”0dp” //不显式地指定控件宽度
layout_height=”wrap_parent”
layout_weight=”1”
设置了权重weight值为1后，表示该控件宽度将会占满整个屏幕的宽度（仅有一个控件的情况下）
如果是两个控件
----------------------------------------------------------------------------------------


5,绝对布局
设定x，y的坐标值，即
layout_x=”xxdp”
layout_y=”yydp”
则该控件就会从（xx，yy）坐标开始显示
这种布局可用于游戏开发中的布局显示，获取屏幕的宽高来动态地计算显示的坐标值，显示在每个屏幕的比例就几乎一样了。
----------------------------------------------------------------------------------------


6,网格布局(4.0后出现的) GridLayout 
-设置组件的排列方式
android:orientation=""
属性值 : vertical 垂直
horizontal 水平
-设置这个布局为几行几列
android:rowCount="4" 设置网格布局有4行
android:columCount="4" 设置网格布局有4列
-设置控件位于几行几列
注意:都是从0开始算
android:Layout_row="1" 设置控件位于第二行显示 
android:Layout_column="2" 设置控件位于第三列显示
-设置某个主键横跨几行几列
android:Layout_rowSpan="2" 行的跨度 
android:layout_columnSpan="3" 列的跨度
android:layout_gravity="fill" 填充你所夸得整行或整列

常用控件
文本框 TextView 父类是View 文本的组件:显示文本信息 
-在xml布局文件中:
TextView属性:
android:text="文本信息 " 文本显示的内容
android:textSize="20sp" 显示内容的字体大小,单位是:sp
android:textColor="#000000" 显示内容的颜色,格式"#RGB"
android:background="" 设置背景色
RGB: a-z和0-9组成的
android:textStyle="bold" 文字的样式(可以叠加使用,必须用"|")
属性值: bold 加粗
italic 斜体
android:singleLine="true" 是否单行显示
android:ellipSize="" 用省略号显示超出文本宽度的内容
属性值: none 无
start 开始位置省略
middle 中间位置省略
end 结束位置省略
marquee 滚动显示
跑马灯:
step1:设置android:ellipSize="marquee"(或者加android:singleLine="true")
step2:设置焦点:
android:focusable="true"
android:InTouchMode="true"
step3:android:marqueeRepeatLimit="marquee_forever"
android:autoLink="" 自动连接(根据内容类型的不同,点击时自动打开相应的应用程序)
属性值: none 无连接
email 邮箱
phone 电话号码
map 地址位置
all 包括以上所有
输入框 EditText 父类:TestView
-属性:
android:hint="提示信息" 提示信息
android:textColorHint="#00000" 提示信息的颜色
android:inputType="输入的类型" 允许用户输入的内容
属性值:number 只能输入数字
date 只能输入日期
text 默认
textPassword 密码
phone 电话号码
android:layout_alignBaseLine="" 在一条基准线上
<requestFocus /> 请求焦点
按钮 Button 父类:TestView
android:text="" 设置按钮显示的文字
android:background="#00000" 设置按钮的背景色,设置按钮的背景图片.
android:background="@null" 去除按钮的灰色背景
android:drawableRight="@drawable/图片" 图片相对于文本的位置 放在文本的右侧
android:drawableLeft="@drawable/图片" 放在文本的左侧 
android:drawableBottom="@drawable/图片" 放在文本的底部
android:drawableTop="@drawable/图片" 放在文本的顶部
android:src="" 地址

------------恢复内容开始------------

Android各大组件
Activity Server (服务)        BroadCastReceive(广播)         ContentProvider(内容提供者)
-----------------------------------------------------------------------------------------------


Android基本
src Java源码
gen 自动生成的java文件
R.java （Resource）静态内部类
assets 资产 包括：音频、视频、 比较大的、不需要修改
不会在R.java中自动生成，它的访问必须通过路径
bin 二进制的文件(Apk)
----------------------------------------------------------------------------------------


res Resource 资源
drawable _hipi 高分辨率的图片
drawable_ldpi 低分辨率的图片
drawable_mdpi 中分辨率的图片
drawable_xhdpi 超高清辨率的图片
drawable_xxhdpi 特高清分辨率的图片


layout 布局 
XMl的文件,高速Activity要显示什么样的内容
menu 菜单 xml文件 安卓底层用到的解析都是(PULL解析) 
values 数据文件 没有对应的静态的内部类
dimens.xml 尺寸
string,xml 常量值 
styles.xml 样式
values-sw7200dp 横屏 一般后缀加(-L)
AndroidMainfest.xml 项目清单文件.(包含以下关键字)
package: 包名 应用程序的唯一标识符
android:versionCode: 当前版本号
application: 
android:icon 图标 
android:label 名称
android:theme 样式
<activity></activity> 当前activity的路径
<!-- --> 注释格式
<intent-filter></intent-filter> 程序入口(意图 过滤器)
----------------------------------------------------------------------------------------


DVM和JVM的比较
1,编译后的文件不同
2,基于的架构不同
3,.class的文件存在很多重复信息, .dex工具会去除重复的信息. 
----------------------------------------------------------------------------------------


四,Android的布局
-res/layout/存放的是 .xml 的布局文件,告诉Activity应该显示那些内容
----------------------------------------------------------------------------------------


1,线性布局 LinearLayout (垂直方向 和 水平方向)
分水平和垂直两个方向：horizontal / vertical
如设置线性布局控件竖直方向放置 android:orientation=”vertical”
在线性布局中实现控件位于整个屏幕的正中央
除了设置宽高全屏外，还得有这句 android:gravity=”center” 设置重心
如果放置在正中央的控件不止一个，默认所有控件是水平放置的
-android:layout_width="match_parent" 设置布局的宽度(通用属性)(长度宽度的值都设为dp)
android:layout_height="match_parent" 设置布局的高度(通用属性)
属性值:match_parent 填充父容器的宽度和高度
fill_parent 填充父容器的宽度和高度(2.2之前的版本)
wrap_content 包裹内容的宽度和高度
-android:orientation="" 设置线性布局的排列方式
属性值:vertical 垂直排列
horizontal 水平排列(默认的) 
<!-- android:text 显示内容
在String.xml 中增加的常量值;
1,java代码中引用:R.string.名称
2,xml中引用:@string/名称 
-->
-android:gravity 父容器内所有子控件的位置
android:gravity="bottom|right" 多个属性直接必须"|"分割
-android:layout_weight 权重 (子控件在父容器剩余空间中所占的比例) 
属性值越大,所占的比例值就越大 
----------------------------------------------------------------------------------------


2,相对布局 RelativeLayout 指子控件与父容器,控件与控件 相对位置的来进行布局
-子控件相对于父容器的位置
控件在不做任何处理时，默认放置在左上角
常用的
layout_margin+Left/Right=”xxdp” 设置控件在布局中距离左边/右边多少个dp的距离
layout_alignParentBottom=”true” 设置控件显示在布局的底部左下角
*注意：如果用layout_marginBottom来设置控件放在底部是不能成功的
layout_align+Left/Right/Top/Bottom=”@id/某一个控件的id值” 设置该控件与给定id的控件左/右/上/下方对齐
layout_toLeft/RightOf=”@id/某一个控件的id值” 设置控件在给定id的控件的左/右方
/*
英文解释
align adj. 对齐的
margin n. 边缘
*/ 居中对齐:
android:layout_centerHorizontal="true" 子控件相对于父容器水平居中
android:layout_centerVertical="true" 子控件对于父容器垂直居中
android:layout_centerInParent="true" 子控件相对于父容器相对居中

位置对齐:
android:layout_alignParentrRight="true" 子控件相对于父容器的右边对齐
android:layout_alignParentLeft="true" 子控件相对于父容器的左边对齐
android:layout_alignParentBottom="true" 子控件相对于父容器的底部对齐
android:layout_alignParentTop="true" 子控件相对于父容器的顶部对齐
-子控件与兄弟控件之间的位置
放置的位置:
android:layout_toRightOf="@id/对应定义的ID名" 子控件显示在ID为对应Id的右侧
android:layout_toLeftOf="@id/button_id" 子控件显示在ID为button_id的左侧
android:layout_below="@id/button_id" 子控件显示在ID为button_id的下方
android:layout_above="@id/button_id" 子控件显示在ID为button_id的上方
对齐的方式:
android:layout_alignRight="@id/button_id" 子控件与ID为button_id的右边对齐
android:layout_alignLeft="@id/button_id" 子控件与id为button_id的左边对齐
android:layout_alignButton="@id.button_id" 子控件与id为button_id的下部对齐
android:layout_alignTop="@id/button_id" 子控件与id为button_id的上方对齐
android:layout_alignBaseLine="@id/button_id" 子控件与Id为button_id的基准线对齐
-外间距(margin)所有组件通用的属性
android:layout_marginRight="30dp" 右边距
android:layout_marginLeft="30dp" 左边距
android:layout_marginTop="30dp" 上边距
android:layout_marginBottom="30dp" 下边距
android:layout_margin="30dp" 四个方向边距
-内边距(padding)所有的组件通用的属性
android:;paddingRight="10dp" 控件内部元素距离右侧的尺寸
android:;paddingLeft="10dp" 控件内部元素距离左侧的尺寸
android:;paddingTop="10dp" 控件内部元素距离顶部的尺寸
android:;paddingBottom="10dp" 控件内部元素距离底部的尺寸 ---------------------------------------------------------------------------------------- 
3,帧布局 (FrameLayout) 每个组件都为一帧,当前子控件会覆盖前一个子控件
实现显示的文字不可复制——就是在整个布局或者有文字上方的添加一层“透明的”布局
设置 visibility=”invisible” 则这一层就默认不显示出来了
----------------------------------------------------------------------------------------


4,表格布局
需要设置每一行的显示，即TableRow
还有一种是不显式地指定控件宽度，而用权重来控制控件在界面中占多少分量
layout_width=”0dp” //不显式地指定控件宽度
layout_height=”wrap_parent”
layout_weight=”1”
设置了权重weight值为1后，表示该控件宽度将会占满整个屏幕的宽度（仅有一个控件的情况下）
如果是两个控件
----------------------------------------------------------------------------------------


5,绝对布局
设定x，y的坐标值，即
layout_x=”xxdp”
layout_y=”yydp”
则该控件就会从（xx，yy）坐标开始显示
这种布局可用于游戏开发中的布局显示，获取屏幕的宽高来动态地计算显示的坐标值，显示在每个屏幕的比例就几乎一样了。
----------------------------------------------------------------------------------------


6,网格布局(4.0后出现的) GridLayout 
-设置组件的排列方式
android:orientation=""
属性值 : vertical 垂直
horizontal 水平
-设置这个布局为几行几列
android:rowCount="4" 设置网格布局有4行
android:columCount="4" 设置网格布局有4列
-设置控件位于几行几列
注意:都是从0开始算
android:Layout_row="1" 设置控件位于第二行显示 
android:Layout_column="2" 设置控件位于第三列显示
-设置某个主键横跨几行几列
android:Layout_rowSpan="2" 行的跨度 
android:layout_columnSpan="3" 列的跨度
android:layout_gravity="fill" 填充你所夸得整行或整列

常用控件
文本框 TextView 父类是View 文本的组件:显示文本信息 
-在xml布局文件中:
TextView属性:
android:text="文本信息 " 文本显示的内容
android:textSize="20sp" 显示内容的字体大小,单位是:sp
android:textColor="#000000" 显示内容的颜色,格式"#RGB"
android:background="" 设置背景色
RGB: a-z和0-9组成的
android:textStyle="bold" 文字的样式(可以叠加使用,必须用"|")
属性值: bold 加粗
italic 斜体
android:singleLine="true" 是否单行显示
android:ellipSize="" 用省略号显示超出文本宽度的内容
属性值: none 无
start 开始位置省略
middle 中间位置省略
end 结束位置省略
marquee 滚动显示
跑马灯:
step1:设置android:ellipSize="marquee"(或者加android:singleLine="true")
step2:设置焦点:
android:focusable="true"
android:InTouchMode="true"
step3:android:marqueeRepeatLimit="marquee_forever"
android:autoLink="" 自动连接(根据内容类型的不同,点击时自动打开相应的应用程序)
属性值: none 无连接
email 邮箱
phone 电话号码
map 地址位置
all 包括以上所有
输入框 EditText 父类:TestView
-属性:
android:hint="提示信息" 提示信息
android:textColorHint="#00000" 提示信息的颜色
android:inputType="输入的类型" 允许用户输入的内容
属性值:number 只能输入数字
date 只能输入日期
text 默认
textPassword 密码
phone 电话号码
android:layout_alignBaseLine="" 在一条基准线上
<requestFocus /> 请求焦点
按钮 Button 父类:TestView
android:text="" 设置按钮显示的文字
android:background="#00000" 设置按钮的背景色,设置按钮的背景图片.
android:background="@null" 去除按钮的灰色背景
android:drawableRight="@drawable/图片" 图片相对于文本的位置 放在文本的右侧
android:drawableLeft="@drawable/图片" 放在文本的左侧 
android:drawableBottom="@drawable/图片" 放在文本的底部
android:drawableTop="@drawable/图片" 放在文本的顶部
android:src="" 地址
