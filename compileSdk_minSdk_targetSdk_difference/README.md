### compileSdkVersion/targetSdkVersion/minSdkVersion区别

1. 三者含义:

  - `compileSdkVersion`: android编译版本，告诉gradle用哪个sdk编译你的应用

 - `minSdkVersion`: 应用可以运行的最低版本要求.google play商店用来判断用户设备是否可以安装某个应用的标识之一。如果你的代码使用了大于`minSdkVersion`版本的API，那么lint会警告。正确的方式是运行时检查版本。

   ```
   private void setUpActionBar() {
      // Make sure we're running on Honeycomb or higher to use ActionBar APIs
      if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.HONEYCOMB) {
          ActionBar actionBar = getActionBar();
          actionBar.setDisplayHomeAsUpEnabled(true);
      }
  }
   ```

 - `targetSdkVersion`:Android 提供向前兼容的主要依据，在应用的 `targetSdkVersion`没有更新之前系统不会应用最新的行为变化。

2. 规律: `compileSdkVersion`>= `targetSdkVersion`>=`minSdkVersion`

3. 区别:`compileSdkVersion`不会被打进apk，而`targetSdkVersion`和`minSdkVersion`会打进apk.
