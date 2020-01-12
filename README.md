## 矢量图UI + 9-Patch适配
github：
[https://github.com/Gong-Shijie/icon-9-Patch](https://github.com/Gong-Shijie/icon-9-Patch)  

首先矢量图网站：
[https://www.iconfont.cn/](https://www.iconfont.cn/)  
里面提供了丰富的矢量图标，供开发者使用  

![矢量图库](https://upload-images.jianshu.io/upload_images/19741117-ef37e2db3dab612f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
### 下载图标 + 导入到Android Studio
![图标](https://upload-images.jianshu.io/upload_images/19741117-887d23b8c8c12265.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
![插入矢量图](https://upload-images.jianshu.io/upload_images/19741117-5d121991c00a610c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![Android Studio导入方法](https://upload-images.jianshu.io/upload_images/19741117-263669219abbc8d0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
![这就是你导入的资源](https://upload-images.jianshu.io/upload_images/19741117-b17ae76418c5df8a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
***  
### 9-Patch  
9-patch图是可以根据内容来自动适配的图片资源  
可以根据设置的内容来伸缩  
利用这一特性可以设计出自适应屏幕时出现的拉伸不适于拉伸部分导致的变形问题  
比如我们的message发送的气泡始终会根据信息长度自动的伸缩   
![通过png创建9-Patch文件](https://upload-images.jianshu.io/upload_images/19741117-0fbbf4426851593a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
![上下左右四边](https://upload-images.jianshu.io/upload_images/19741117-160dd8cc155fa1e5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
##### 左边和上边框用来标记需要被拉伸的区域  
##### 右边和下边的边框用来标记内置的内容对齐的区域  
**使用9-Patch来作为View或者Layout的background可以用来适配不同尺寸的屏幕**  



***  
### 主要代码  
**XML**  
```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"

    android:layout_height="match_parent"
    tools:context=".MainActivity">
    <LinearLayout
        android:id="@+id/l1"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"

        android:layout_marginTop="100dp">

        <ImageView
            android:layout_width="50dp"
            android:layout_height="50dp"
            android:layout_marginLeft="20dp"
            android:src="@drawable/ic_course"
            android:layout_gravity="top|left"
            ></ImageView>
        <ImageView
            android:layout_width="50dp"
            android:layout_height="50dp"
            android:layout_marginLeft="40dp"
            android:src="@drawable/ic_back"></ImageView>
        <ImageView
            android:layout_width="50dp"
            android:layout_height="50dp"

            android:layout_marginLeft="50dp"
            android:src="@drawable/ic_0"></ImageView>
    </LinearLayout>
    <LinearLayout
        android:id="@+id/l2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@id/l1"
        android:layout_marginTop="30dp"
        android:orientation="horizontal">

            <ImageView
                android:layout_width="50dp"
                android:layout_height="50dp"
                android:src="@drawable/ic_1"
                android:layout_marginLeft="20dp"
                android:layout_gravity="left"
                ></ImageView>
            <ImageView
                android:layout_width="50dp"
                android:layout_height="50dp"
                android:layout_marginLeft="40dp"
                android:src="@drawable/ic_2"></ImageView>
            <ImageView
                android:layout_width="50dp"
                android:layout_height="50dp"

                android:layout_marginLeft="50dp"
                android:src="@drawable/ic_3"></ImageView>

    </LinearLayout>
    <LinearLayout
        android:layout_below="@id/l2"
        android:layout_width="match_parent"
        android:orientation="vertical"
        android:layout_marginTop="100dp"
        android:layout_height="wrap_content">
        <TextView
            android:id="@+id/t1"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:background="@drawable/message_left"
            android:text="hello world!">
        </TextView>
        <TextView
            android:id="@+id/t2"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:background="@drawable/message_left"
            android:text="这是一条长文本，测试伸缩效果。">
        </TextView>
    </LinearLayout>
</RelativeLayout>
```
