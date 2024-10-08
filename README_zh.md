# OpenSBI加载器

## 概述

OpenSBI Loader是OpenSBI的一个简单加载器。它假设Flash中的镜像分布如下：

|地址|图像名称|
|---|---|
|0x80010000|OpenSBI|
|0x80040000|Linux内核|
|0x80310000|LinuxDTB|

如果Flash中的镜像地址不一致，可以修改源代码中的宏定义以满足您自己的需要。

## 必须做的事情
- 设置uart0 pinmux并将其时钟频率设置为24MHz，因此opensbi当前可以初始化uart0。否则OpenSBI的控制台可能无法工作。
- 初始化SDRAM
- 将OpenSBI映像复制到地址0x00000000
- 复制Linux内核映像到地址0x40000000
- 复制LinuxDTB图像到地址0x40300000
- 禁用中断矢量模式
- 确保加载器不使用其他图像使用的内存区域

## 板设置

没有特殊设置

## 运行示例
```
OpenSBI v0.6-4-gc335500
   ____                    _____ ____ _____
  / __ \                  / ____|  _ \_   _|
 | |  | |_ __   ___ _ __ | (___ | |_) || |
 | |  | | '_ \ / _ \ '_ \ \___ \|  _ < | |
 | |__| | |_) |  __/ | | |____) | |_) || |_
  \____/| .__/ \___|_| |_|_____/|____/_____|
        | |
        |_|

```
