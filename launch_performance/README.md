## 应用启动优化

方案:

> 异步加载、延迟加载、按需加载、

> 冷启动优化([http://blog.csdn.net/chdjj/article/details/50296105](http://blog.csdn.net/chdjj/article/details/50296105))


#### 关于延迟加载

如下代码可保证`updateText()`的逻辑在应用第一帧显示完后立即执行。

代码清单1

```
private Handler myHandler = new Handler();
private Runnable mLoadingRunnable = new Runnable() {

  @Override
  public void run() {
    updateText(); //更新UI线程
  }
};

//Activity#onCreate()
getWindow().getDecorView().post(new Runnable() {

  @Override
  public void run() {
    myHandler.post(mLoadingRunnable);
  }
});

```

TODO

参考资料:

1. http://www.androidperformance.com/2015/11/18/Android-app-lunch-optimize-delay-load.html
