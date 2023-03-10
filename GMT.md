## **生成脚本模板**

在终端中敲入:

```sh
gmt --new-script > myplot.sh
```

运行 GMT 脚本的基本流程，即：

• 生成脚本模板

• 编辑脚本，添加 GMT 绘图命令

• 运行脚本并查看绘图效果

**GMT中一条命令代表一个图层。**

GMT的命令要在begin和end之间，其它的可以在外面

##  **GMT** **命令格式**

一个 GMT 命令通常由 **gmt** + **模块名** + **选项** + **参数**构成。

```sh
gmt coast -Rg -JH15c -Gpurple -Baf -B+t"My First Plot"
```

要绘制地图，就需要将地球的三维球面投影到一个二维面上，投影的过程需要指定投影方式。

哈默投影（**Hammer projection**）

**哈默投影**是等积[伪圆柱投影](https://baike.baidu.com/item/伪圆柱投影/5833840)中的一种。由哈默拟定，故名。此投影的横坐标是等面积圆柱投影和桑生投影两者的算术平均值，纵坐标由等面积条件导出，使整个世界置于椭圆内。属等面积性质，可绘世界图。

GMT 中使用 **-J**选项指定地图投影参数以及地图的尺寸。同时，我们还需要使用 **-R** 选项指定要绘制的区域范围（即经纬度范围）。

GMT 中可以使用 **-B** 选项为地理底图加上边框并绘制经纬线。

```sh
# 有show结束时会自动展示
gmt end show
# 没有show结束后不会自动显示
gmt end
```

墨卡托投影（绘制区域地图最常用的投影方式）

**-Bafg** 表示绘制底图边框的标注（**a**nnotation）、刻度线（**f**rame，即图中黑白线段的间隔）和网格线（**g**rid）。

**coast**模块将岸线分为从1到4的四个级别，依次指海岸线、湖岸线、湖中岛，以及湖中岛内的湖边界。

因而，我们可以在使用 **-W** 选项时指定要绘制哪一个等级的岸线。下面的脚本中，我们使用 **-W1/0.5p,black** 表示用 0.5p 宽的黑色线条绘制1级海岸线。

```sh
gmt begin coastline png,pdf
    gmt coast -R-130/-50/20/60 -JM15c -Baf -W1/0.5p,black
gmt end show
```

## 填充陆地与水体

**-G** 设置了陆地区域的填充色，**-S** 设置水体的颜色， **-C** 则设置湖泊的颜色（若不指定 **-C**，则湖泊颜色由 **-S** 控制）。

```sh
gmt begin coastline png,pdf
    gmt coast -R-130/-50/20/60 -JM15c -Baf -A5000 -Gred -Slightblue -Clightred
gmt end show
```

## 绘制国界/州界

使用 **-N** 选项可以绘制国界/州界等行政边界。**-N1** 表示绘制国界线， **-N2** 表示绘制州界/省界线（目前只有美洲各国以及澳大利亚的国界的数据）。

```sh
gmt begin coastline png,pdf
    gmt coast -R-130/-50/20/60 -JM15c -Baf -A5000 -Gred -Slightblue -Clightred -N1/1p -N2/0.25p
gmt end show
```

## 添加比例尺

我们使用了 **-Lg-60/25+c25+w1000k+f+u** 增加比例尺，其中：

- **+w1000k** 表示比例尺长度为1000千米
- **+c25** 表示绘制纬度为北纬25°处的比例尺
- **g-60/25** 则表示将比例尺画在北纬25°西经60°处
- **+f** 表示比例尺的风格为图中所示黑白相间的铁轨形式
- **+u** 表示显示比例尺对应的单位

```sh
gmt begin coastline png,pdf
gmt coast -R-130/-50/20/60 -JM15c -Baf -A5000 -Gred -Slightblue -Clightred -Lg-60/25+c25+w1000k+f+u
gmt end show
```

```sh
#!/usr/bin/env -S bash -e
# GMT modern mode bash template
# Date:    2021-04-30T10:43:40
# User:    br
# Purpose: Purpose of this script
export GMT_SESSION_NAME=$$	# Set a unique session name
gmt begin test1 
	# Place modern session commands here
	# 画海岸线图层
	gmt coast -JH15c -Rg -Bafg -W0.1p -Cblue -Ggreen -Slightblue
	# 画地震台图层
	gmt plot -St0.5c stations.txt -Gred
	# 画连线图层
	gmt plot -W1p line.txt
	# 画震中图层
	gmt plot -Sa0.7c epicenter.txt -Gyellow -W1p,black
	# 添加文字图层
	gmt text name_en.txt -F+f9p,1,black+j -Dj0.1c/0.1c
gmt end 
```

![image-20210430162137275](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210430162137275.png)

```sh
#!/usr/bin/env -S bash -e
# GMT modern mode bash template
# Date:    2021-04-30T15:54:27
# User:    br
# Purpose: Purpose of this script
export GMT_SESSION_NAME=$$	# Set a unique session name
gmt begin test2 png
	# Place modern session commands here
	# -C cpt文件 颜色与地势的映射文件
	# -J -R -B要出现在第一行的命令中
	# 地势图层 @表示是远程数据
	gmt grdimage @earth_relief_30m -JM10c -R-100/100/-60/60 -Baf -B+t"PB2002" -Cgeo
	# 海岸线图层
	gmt coast -W1/1p,black -A1000
	# 绘制板块边界，利用已有地学数据集
	gmt plot PB2002_boundaries.dig.txt -W0.5p,red
gmt end 
```

![image-20210430162224445](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210430162224445.png)

## 时序图

时序图即时间序列图       x轴为时间或日期，y轴为数值

![img](https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fdocs-aliyun.cn-hangzhou.oss.aliyun-inc.com%2Fassets%2Fpic%2F58644%2Fcn_zh%2F1509509296167%2FSDKServer.jpg&refer=http%3A%2F%2Fdocs-aliyun.cn-hangzhou.oss.aliyun-inc.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1622363463&t=7e1c0994fcca552f940bb0bdad93b5b0)

```sh
#!/usr/bin/env -S bash -e
# GMT modern mode bash template
# Date:    2021-04-30T16:34:38
# User:    br
# Purpose: Purpose of this script
export GMT_SESSION_NAME=$$	# Set a unique session name
r=-R2020-10-06T05:55:00/2020-10-06T05:56:15/-3/3
gmt begin test3 png
	# Place modern session commands here
	# -JX 笛卡尔坐标系 
	# subplot画子图，3x1代表3行1列
	gmt subplot begin 3x1 -Fs18c/3c $r -Ba -A -SCb -SRl -BWStr

		gmt subplot set 0 -A'E' 
		gmt plot @waveform_AV.DOL.txt -i0,1+s1e-6 -Wred

		gmt subplot set 1 -A'N' 
		gmt plot @waveform_AV.DOL.txt -i0,2+s1e-6 -Wblue

		gmt subplot set 2 -A'Z' 
		gmt plot @waveform_AV.DOL.txt -i0,3+s1e-6 -Wgreen

	gmt subplot end 

gmt end 
```

![image-20210430165756960](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210430165756960.png)

```sh
#!/usr/bin/env -S bash -e
# GMT modern mode bash template
# Date:    2021-04-30T17:00:28
# User:    br
# Purpose: Purpose of this script
export GMT_SESSION_NAME=$$	# Set a unique session name
gmt begin test4 png
	# Place modern session commands here
	# 画主图层
	gmt grdimage @earth_relief_05m.grd -R70/130/10/60 -JQ15c -Ba 
	# 画鹰眼视图，即内嵌图
	gmt inset begin -DjTR+w6c+o-2c/-2c
		gmt grdimage @earth_relief_20m.grd -Rg -JG103/31/? -Bag
		echo 70 10 130 60 | gmt plot -Sr+s -W1p,red
	gmt inset end
gmt end 
```

![image-20210430171624001](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210430171624001.png)

```sh
#!/usr/bin/env -S bash -e
# GMT modern mode bash template
# Date:    2021-04-30T17:20:45
# User:    br
# Purpose: Purpose of this script
export GMT_SESSION_NAME=$$	# Set a unique session name
gmt begin test5 png
	# Place modern session commands here
	gmt coast -JD105/35/36/42/7.5i -R70/140/3/60 -G244/243/239 -S167/194/223 -Ba10f5g10 -Lg85/11+c11+w900k+f+u
	# 绘制省界
	gmt plot CN-border-La.dat -W0.5p
	# 绘制断层
	gmt plot CN-faults.dat -W0.5p,red
gmt end 
```

![image-20210430174543947](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210430174543947.png)

dat文件：.*dat*并不是一种标准*文件*。许多*文件*都使用这个扩展名，但*文件*含义不同。而许多数据分析软件也用这个扩展名保存数据。

使用 **plot** 模块的 **-W** 选项设置画笔属性。画笔属性包括三个部分：线宽、颜色以及线型，三者之间用逗号隔开。

下面的脚本中，我们给 **plot** 模块添加了 **-W2p,red,-** 选项，即设置了画笔属性为 **2p** 宽的红色虚线。**p** 是GMT中的一个长度单位。

```sh
cat > points.dat << EOF
2   2
8   2
5   7
EOF

gmt begin SimpleLine png,pdf
    gmt basemap -JX10c -R0/10/0/10 -Baf
    gmt plot points.dat -W2p,red,-
gmt end show
```

## 绘制一个多边形

**plot** 在绘制线段时默认是不将线段首尾连接起来的，可以使用 **-L** 选项将线段的首尾连接起来，构成了一个闭合多边形。

```sh
cat > points.dat << EOF
2   2
8   2
5   7
EOF

gmt begin polygon png,pdf
    gmt basemap -JX10c -R0/10/0/10 -Baf
    gmt plot points.dat -W4p,lightblue -L
gmt end show
```

## 大圆弧路径

在笛卡尔坐标系下，绘制线段时，任意两点之间会以直线方式连接；而在地理投影下，任意两点之间则使用大圆弧路径方法会连接。如果想要在地理投影下也是要直线连接两点，则需要使用 **-A** 选项。

下面的命令中，我们首先使用 **coast** 绘制了一张全球地图，接着使用 **plot** 模块绘制了地球上两点之间的连线（红色，以大圆弧路径方式连接），然后，我们加上了 **-A** 选项再次绘制了这两点之间的连线（蓝色，以直线方式连接）。从中可以看到 **-A** 选项的效果。

```sh
cat > twopoints.dat << EOF
115         30
250         30
EOF

gmt begin map png,pdf
    gmt coast -JH180/12c -Rg -B0 -W0.5p -A10000
    gmt plot twopoints.dat -W2p,red
    gmt plot twopoints.dat -W2p,blue -A
gmt end show
```

![image-20210501185300789](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210501185300789.png)

## 颜色变化的符号

前面提到，使用 **-G** 选项可以为符号填充颜色，但其只能同时为所有符号指定单一的颜色。如果想要让符号的颜色根据某个数值的不同而使用不同的颜色，则需要使用 **-C** 选项。 **-C** 选项表示符号的填充色由某个数值以及CPT颜色表所控制。CPT颜色表给出了数值与颜色之间的对应关系。因而对于任意一个符号，我们都可以给其一个数值，GMT会根据该数值从CPT颜色表中找到对应的颜色作为该符号的填充色。因而，在输入数据中，我们需要在 X和Y坐标的基础上额外加一列Z值，用于控制符号的填充色。

下面的示例中，我们首先使用 **makecpt** 模块，以GMT内置CPT颜色表 **hot** 为基础，生成了一个新的CPT颜色表。关于CPT颜色表的具体细节在后面会介绍到。此处，读者只需要知道，我们制作了一个CPT文件供后面的命令使用。该CPT颜色表为0到3之内的每个数值都对应了一个颜色。

同时，对于输入数据，我们额外增加一列（通常称这一列为Z值），该列的值决定了符号的填充色。

```sh
gmt begin symbols png,pdf
gmt makecpt -Chot -T0/3/1
gmt plot -R0/10/0/10 -JX10c/10c -Baf -Sc0.5c -W1p,black -C << EOF
2   3   0
5   6   1
8   2   2
EOF
gmt end show
```

## 全球地形起伏数据

要绘制全球或区域地形起伏图，首先需要拥有地形起伏数据，即不同经纬度处的高程或海深数据。GMT收集整理并提供了一套全球地形起伏数据，供用户直接使用。这套地形起伏数据分为包含了从60弧分到1弧秒的多种不同精度的全球地形起伏数据，以满足不同的绘图区域大小的需求。

GMT用户可以通过给定文件名 `@earth_relief_xxx` 的方式来指定要使用某个精度的地形。*xxx* 用于指定数据精度，例如 **15m**、**01m**和 **15s** 分别表示数据分辨率为15弧分、1弧分和15弧秒。

文件名前的 **@** 表示该数据是由GMT官方提供并维护的数据，当第一次使用该文件时，GMT会自动从服务器下载该数据并保存到本地的GMT数据目录中，当以后再使用该文件时，则直接读取本地文件，而无需重新下载该数据。

```sh
gmt begin global_relief png,pdf
gmt grdimage @earth_relief_05m -JH180/10c
gmt end show
```

![../../_images/earth-relief-gmtplot-01.png](https://docs.gmt-china.org/latest/_images/earth-relief-gmtplot-01.png)

## 湖南省地形图

```sh
#!/usr/bin/env -S bash -e
# GMT modern mode bash template
# Date:    2021-05-02T19:14:37
# User:    br
# Purpose: Purpose of this script
export GMT_SESSION_NAME=$$	# Set a unique session name
gmt begin test4 png
	# Place modern session commands here
	# gmt grdimage @earth_relief_05m -JH110/10c 
	gmt grdimage @earth_relief_01m -JM15c -R108.5/114.5/24/30.5 -Baf -BWSen -I+d -Cdem2
	gmt plot ../CN-border-La.dat -W4p,red
	gmt colorbar -Bxaf+l'elevation(m)'
gmt end 
```

![image-20210502200612147](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210502200612147.png)

```sh
#!/usr/bin/env -S bash -e
# GMT modern mode bash template
# Date:    2022-10-15T15:05:00
# User:    br
# Purpose: Purpose of this script
export GMT_SESSION_NAME=$$	# Set a unique session name
gmt begin hunan_topography png
	# Place modern session commands here
	# 制作cpt
	gmt makecpt -T-50/1000/10 -Crainbow
	# 裁剪全球的grd文件以获取指定区域的grd文件
	gmt grdcut @earth_relief_01m -Gout.grd -R108.5/114.5/24/30.5
	# 对指定区域的grd文件进行重采样
	gmt grdsample out.grd -I0.01/0.01 -Gout1.grd
	# 绘制地形图
	gmt grdimage out1.grd -JM20c -R108.5/114.5/24/30.5 -Baf -BWSEN -I+d 
	# 绘制边界线
	gmt plot CN-border-La.gmt -W4p,red
	# 绘制子图
	gmt inset begin -DjBL+w5c/6c+o0.1c -F+gwhite+p1p
        gmt coast -R73.66/135.05/3.86/53.55 -JM? -ECN+glightbrown+p0.2p -A10000 # CN是中国的英文简称
        # Plot a rectangle region using -Sr+s
        echo 108.5 24 114.5 30.5 | gmt plot -Sr+s -W1p,blue
    gmt inset end
	# 绘制colorbar
	gmt colorbar -Bxaf+l'elevation(m)' 
gmt end show
```

![image-20221015160443178](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20221015160443178.png)

## 直方图

直方图根据直方的方向可以分为垂直直方图和水平直方图，也可以根据直方的长度的意义不同分为计数直方图和百分比直方图。

```sh
#!/usr/bin/env -S bash -e
# GMT modern mode bash template
# Date:    2021-05-03T10:42:18
# User:    br
# Purpose: Purpose of this script
export GMT_SESSION_NAME=$$	# Set a unique session name
gmt begin test5 png
	# Place modern session commands here
	# gmt histogram eq.dat -JX15c/6c -R0/40/0/600 -Bxaf+l'depth' -Byaf+l'counts' -BWSen -W1p -Gred -T5 -i2 -D -A
	gmt histogram eq.dat -JX15c/9c -Bxaf+l"Depth" -Byaf+l"Counts"+u'%' -BWSen -Z1 -W1p -Gred -T5 -i2 
gmt end 
```

![../../_images/index-gmtplot-3.png](https://docs.gmt-china.org/latest/_images/index-gmtplot-3.png)

## python提供了gmt的接口库PyGMT

## 子图布局

![../../_images/subplot-gmtplot-01.png](https://docs.gmt-china.org/latest/_images/subplot-gmtplot-01.png)

## 灰色

用RGB表示灰度

灰色本质上就是 *R*=*G*=*B* 的一种颜色。因而 **128/128/128** 代表灰度为 128 ，**200/200/200** 代表灰度是 200。

## 模块

xyz2grd将xyz文件转换为grd文件

grdsample可以将grd文件插值

grd2xyz将grd文件转为xyz文件获取经纬度和高程数据

grdcut将grd文件裁剪为指定区域的grd文件

## geo3al:中国及邻区地质图数据

geo3al 数据是由 U.S. Geological Survey (USGS) 提供的中国及邻区地质图数据，是“[世界地质地图](https://certmapper.cr.usgs.gov/data/apps/world-maps/)”的一部分，数据分辨率为 1:5,000,000。
