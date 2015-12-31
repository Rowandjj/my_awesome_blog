## 字符串格式化在android上的应用
------


#### 1. string.xml中使用特殊符号

- 在string.xml中显示带有双引号的字符串，比如``"hello world"``,需要加反斜杠转义

 ```
 <string name="test">\"hello world\"</string>
 ```

- 在string.xml中显示带单引号的字符串,比如`I'm Rowandjj`,有两种方法，一种是加反斜杠转义，另一种是在字符串前后加双引号

  ```
  <string name="test">"I'm Rowandjj"</string>
  <string name="test">I\'m Rowandjj</string>
  ```
- 在string.xml中使用html标签格式化字符串

  支持`<u>`、`<b>`、`<i>`等标签,但是需要注意的是，标签需要转义，比如`<`需要转成`&lt;`,另外，引用该资源的时候需要通过`Html.fromHtml()`转化。

  ```
  <string name="test">&lt;b>Welcome to&lt;/b> &lt;u>Android&lt;/u>!</string>
  ```

#### 2. 使用String placeHolder 避免字符串拼接

 `String`类的`format`方法支持格式化字符串,比如我们希望显示一个动态的字符串:

   ```
   my name is xxx,my age is yyy
   ```
 `xxx`和`yyy`由服务端动态返回，那么我们可以这样格式化,并将格式化后的字符串放到string.xml中:

  ```
  <string name="test">my name is %1$s,my age is %2$d</string>
  ```

然后在代码中通过如下方法设置字符串的值:

```
textView.setText(String.format(getResources().getString(R.string.test),"Rowandjj",21));
```

常见的转换符:


| 转换符 | 说明 | 示例 |
| ------ | ------ | ------ |
|%s|字符串类型|"Rowandjj"|
|%c|字符类型|'c'|
|%b|布尔类型|true|
|%d|整数类型（十进制）|99|
|%x|整数类型（十六进制）|FF|
|%o|整数类型（8进制）|77|
|%f|浮点类型|9.99|
|%e|指数类型|9.1e+7|
|%n|换行符|换行|
|%%|百分比类型|%d%%==>80%|

标识：

|标识|说明|示例|结果|
|---|---|---|---|
|+|为正数或者负数添加符号|("%+d",15)|+15|
|0|数字前面补0|("%04d",99)|0099|
|,|以逗号分隔数字|("%,d",1000000)|1,000,000|
|$|被格式化的参数索引|	("%1$d,%2$s",99,"abc")|99,abc|
