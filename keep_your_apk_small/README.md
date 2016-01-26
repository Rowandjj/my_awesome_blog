### apk瘦身方案

1. 在gradle脚本中配置`minifiedEnabled`/`shrinkResource`

  ```
  release {
            minifyEnabled true //允许运行proguard
            shrinkResources true//自动清除无用资源

        }
  ```

2. release版本开启混淆

3. 清理无用的外部依赖,图片资源

4. 数据文件可以适当从网络拉取,尽量不要打到apk里面

5. 图片压缩

  - 部分大图如果没有透明效果可以用Jpeg替代png。jpeg是有损压缩，通常会比png小很多

  - 使用webp. (android4.0之后)

6. [微信资源压缩打包方案](http://mp.weixin.qq.com/s?__biz=MzAwNDY1ODY2OQ==&mid=208135658&idx=1&sn=ac9bd6b4927e9e82f9fa14e396183a8f#rd)

7. proguard去符号表

  ```

  -keepattributes SourceFile,LineNumberTable
  ```
  注意：会导致混淆后的包出现crash无法追查出现的行数，需要通过mapping.txt.

8.去除无用的语言资源

  通过配置resConfigs可以选择只打包哪几种语言，进而去掉各种aar包中全世界的语言，尤其是support包中的。选择保留什么语言要根据产品的用户和市场来定，如果只选择默认英语和中文语言，配置如下

  ```
  android {
      defaultConfig {
          resConfigs "zh"
      }
  }
  ```


9. 善用lint

### 参考资料:

> [http://www.jayfeng.com/2015/12/29/APK%E7%98%A6%E8%BA%AB%E5%AE%9E%E8%B7%B5/](http://www.jayfeng.com/2015/12/29/APK%E7%98%A6%E8%BA%AB%E5%AE%9E%E8%B7%B5/)
