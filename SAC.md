## SAC 是什么？

Seismic Analysis Code，简写为 SAC，是天然地震学领域使用最广泛的数据分析软件包之一。

## sac的linux安装

```sh
SAC在Linux系统下的安装 (2016-09-13 16:22:56)转载▼
标签： sac linux	分类： Linux
1、解压
$ tar -xvf sac-101.6a-linux_x86_64.tar.gz

2、移动到目录
$ mv sac /usr/local

3、配置环境变量
$ vi ~/.bashrc
或者使用gedit编辑器
$ gedit ~/.bashrc

添加一下内容
export PATH=/usr/local/sac/bin:$PATH
export SACAUX=/usr/local/sac/aux

4、使配置生效
$ source ~/.bashrc

5、启动SAC
$ sac

SEISMIC ANALYSIS CODE [11/11/2013 (Version 101.6a)]
Copyright 1995 Regents of the University of California 

SAC>

出现版本信息，则说明成功安装该软件了。输入：q 即可退出。
```

## [为win10的linux子系统搭载图形界面(WSL安装桌面)](https://www.cnblogs.com/liangxuran/p/14274847.html)

https://www.cnblogs.com/liangxuran/p/14274847.html

Xlaunch  WSL的图形界面软件

## SAC 命令长什么样？

一个完整的 SAC 命令一般由“命令+选项+参数”构成，其中命令必须有，选项和参数可以成对出现，也可以只出现其中一个。命令、选项以及参数之间用空格分开。如果要将多个命令写在一行，要用**分号**隔开每个命令。例如：

```sh
SAC> funcgen random delta 0.1 npts 1000
SAC> rmean; rtrend; taper                 # 一行内多个命令用分号隔开
SAC> write rand.SAC
```

`delta` 代表的是采样周期。也称为采样时间，即两次数据采样的时间间隔，本文档将统一使用“采样周期”。

## funcgen

[funcgen](https://seisman.github.io/SAC_Docs_zh/commands/funcgen/)（简写为 `fg`）表示“function generator”，即该命令可以生成一些特定的函数，比如脉冲、阶跃、正弦等等，还可以生成一个地震波形样本:

```sh
SAC> fg impulse         # 生成脉冲函数
```

![image-20210505111124203](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210505111124203.png)

`funcgen` 可以生成地震波形样本:

```sh
SAC> fg seismogram      # 生成地震波形样本，简写为 fg seis
```

![image-20210505111415521](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210505111415521.png)

## datagen

[datagen](https://seisman.github.io/SAC_Docs_zh/commands/datagen/)（简写为 `dg`）表示“data generator”。顾名思义，就是用来生成数据的。

下面的示例在内存中生成了 CDV 台站记录到的一个近震的三分量波形数据[1](https://seisman.github.io/SAC_Docs_zh/basis/funcgen-and-datagen/#id3)，并用 [plot1](https://seisman.github.io/SAC_Docs_zh/commands/plot1/)（简写`p1`）将三个波形画在一张图上:

```sh
SAC> dg sub local cdv.?
SAC> p1
```

![image-20210505111954904](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210505111954904.png)

## 读和写

SAC 的读命令是 [read](https://seisman.github.io/SAC_Docs_zh/commands/read/)（简写为 `r`），写命令为 [write](https://seisman.github.io/SAC_Docs_zh/commands/write/)（简写为 `w`）。读和写是紧密联系的，所以把这两者放在一起讲。

SAC 中，在指定文件名的时候，可以使用绝对路径，也可以使用相对路径。可以使用其全名，也可以使用通配符。SAC 的通配符与 Unix 定义的通配符一致，只包含如下三种：

1. “`*`” 匹配任意长度的字符串（包括零长度）；
2. “`?`” 匹配任意单个非空字符；
3. “`[]`” 匹配列表中的任意单一字符；
   - “`[ABC]`” 或 “`[A,B,C]`” 匹配单个字符 A 或 B 或 C
   - “`[0-9]`” 匹配任意一位数字
   - “`[a-g]`” 匹配从 a 到 g 范围内的任意单个字符

## 绘图

SAC 中有四个常用的绘图命令，分别是 [plot](https://seisman.github.io/SAC_Docs_zh/commands/plot/)、[plot1](https://seisman.github.io/SAC_Docs_zh/commands/plot1/) 、[plot2](https://seisman.github.io/SAC_Docs_zh/commands/plot2/)、[plotpk](https://seisman.github.io/SAC_Docs_zh/commands/plotpk/)。

## SAC 数据处理

有些时候，从SEED或miniSEED中提取出的同一台站同一分量的连续波形数据，会被分割成多个等长或不等长的文件，数据断开的可能原因是仪器在某些时刻存在问题导致连续数据出现间断，也可能是出于其它考虑将数据进行切割。此时需要首先对数据进行合并。

## 去毛刺

地震仪器偶尔会出现问题，导致连续地震数据流中出现尖锋或者数据丢失。这些所谓的毛刺，肉眼很容易识别，但是在使用程序自动处理数据时却很容易被误认为是地震信号，因而需要在数据分析之前将毛刺去除。`rglitches` 命令可以在某种程度上检测并去除地震信号中的毛刺。毛刺在模拟地震记录中很常见，现在的数字地震记录中则很少见到，因而实际上很少需要执行这一步操作。

![地震波形去毛刺](https://seisman.github.io/SAC_Docs_zh/_images/rglitches.png)

上图为包含 glitches 的地震信号，下图为去除 glitches 后的地震信号。

## 去均值、去线性趋势和波形尖灭

通常，波形数据总会存在一个非零的均值或者存在一个长周期的线性趋势，这会影响到数据的分析，必须在数据分析前去除。另一方面，在对数据进行谱域操作（如FFT、滤波等）时，若数据的两端不为零，则会出现谱域假象，因而实际数据经常需要做尖灭处理，使得数据两端在短时间窗内逐渐变成零值。

```sh
SAC> fg seis
SAC> rmean; rtr; taper
```

波形从上到下依次为原始波形、去均值、去线性趋势、和尖灭之后的波形。

![去均值、去线性趋势和波形尖灭](https://seisman.github.io/SAC_Docs_zh/_images/rmean-rtrend-taper.png)



## obspy



## 其它

r读，p绘图，w写

bandpass简写bp带通滤波命令

xlim设定图中x轴的范围

sac读取文件之后想要修改最后必须用w写入

saclst kzdate kztime f *
