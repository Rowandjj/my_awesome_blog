## adb command

1. 查看进程列表

	```
	adb shell ps
	adb shell ps | grep com.xxx.yyy
	```

2. 列出可用设备

	```
	adb devices
	```

3. 安装/卸载应用

	```
	adb install/uninstall xxx.apk
	adb -s device_name install xxx.apk
	```

4. 列出所有包

	```
	adb shell pm list packages -f
	adb shell pm list packages -f | grep xxx
	```

5. 拷贝

	```ß
	//device to computer
	adb pull /data/data/ua.slando/databases/ /OurLocalPath
	//computer to device
	adb push /OurLocalPath/ourFile.txt /data/data/our.package.name/databases/
	```

6. 清除应用数据

	```
	adb shell pm clear package_name
	```
