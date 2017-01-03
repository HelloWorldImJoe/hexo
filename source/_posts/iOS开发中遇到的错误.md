---
title: 'iOS开发中遇到的错误'
date: 2016-12-26 23:33:32
tags: iOS错误集锦
categories: iOS之路
---

* **错误描述：** `Failed to chmod user/Library/Developer/CoreSimulator/Devices NO Such File Or directory `
**原因：** 在工程删除文件时,没有把文件的映射删除掉(一般都会自动删除)
**解决方法：** 查找`AddedLib` `Resources` `complied Resources`中是否还存在已经删除文件的映射并删除
**引用：**[StackOverFlow中Vikas Mishra的回答](http://stackoverflow.com/questions/40485155/failed-to-chmod-user-library-developer-coresimulator-devices-no-such-file-or-dir/40656606)
____
* **错误描述：**`directory not found for option '-F/Applications/···`
**原因：**工程文件中`Build Settings -> Search Paths`键的值有冲突
**解决方法：**将老的(引起冲突的)sarch path删除掉
**引用：**[StackOverFlow中King-Wizard的回答](http://stackoverflow.com/questions/30827022/xcode-7-library-search-path-warning)
____
