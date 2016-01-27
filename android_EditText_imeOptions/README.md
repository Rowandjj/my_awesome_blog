### 使用imeOptions控制EditText右下角按键的显示内容

1. 设置`android:imeOptions=""`属性即可,若发现不管用,再加上`android:singleLine="true"`.
2. `android:imeOptions=""`属性值选项：

  ```
  android:imeOptions="actionNone"  //输入框右侧不带任何提示
  android:imeOptions="actionGo"    //右下角按键内容为'开始'
  android:imeOptions="actionSearch"  //右下角按键为放大镜图片，搜索
  android:imeOptions="actionSend"    //右下角按键内容为'发送'
  android:imeOptions="actionNext"   //右下角按键内容为'下一步'
  android:imeOptions="actionDone"  //右下角按键内容为'完成'
  ```
3. 代码中捕获选项值,设置`setOnEditorActionListener`,并截获`actionId`与`EditInfo`比较.

```
((EditText)findViewById(R.id.et1)).setOnEditorActionListener(new TextView.OnEditorActionListener() {
           @Override
           public boolean onEditorAction(TextView v, int actionId, KeyEvent event) {//EditInfo
               Toast.makeText(NewActivity.this,"actionId:"+actionId,Toast.LENGTH_SHORT).show();
               return true;
           }
       });
```
