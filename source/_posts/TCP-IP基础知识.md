---
title: TCP/IP基础知识（一）
date: 2017-11-18 23:08:32
tags: [编程,网络]
categories: 网络
---

- 什么是IP，IP地址是什么

  互联网协议地址（英语：Internet Protocol Address，又译为网际协议地址），缩写为IP地址（英语：IP Address），是分配给网络上使用网际协议（英语：Internet Protocol, IP）的设备的数字标签。

- IPv4到IPv6

  常见的IP地址分为IPv4与IPv6两大类。IP地址由32位二进制数组成，为便于使用，常以**XXX.XXX.XXX.XXX**形式表现，每组XXX代表小于或等于255的10进制数。例如维基媒体的一个IP地址是208.80.152.2。地址可分为**A、B、C、D、E**五大类，其中E类属于特殊保留地址。IP地址是唯一的。目前IP技术可能使用的IP地址最多可有**4,294,967,296个（即2的32方）**。骤看可能觉得很难会用尽，但由于早期编码和分配上的问题，使很多区域的编码实际上被空出或不能使用。加上互联网的普及，IPv4的42亿个地址的分配最终于2011年2月3日用尽**。相应的科研组织已研究出128位的IPv6，其IP地址数量最高可达3.402823669 × 1038个，届时每个人家居中的每件电器，每件对象，甚至地球上每一粒沙子都可以拥有自己的IP地址。从IPv4到IPv6最显著的变化就是网络地址的长度。RFC 2373和RFC 2374定义的IPv6地址，就像下面章节所描述的，有128位长；IPv6地址的表达形式，一般采用32个十六进制数。IPv6中可能的地址有**2的128方≈3.4×1038**个，具体数量为****340,282,366,920,938,463,463,374,607,431,768,211,456**个。在很多场合，IPv6地址由两个逻辑部分组成：一个64位的网络前缀和一个64位的主机地址，主机地址通常根理地址自动生成，叫做EUI-64（或者64-位扩展唯一标识）

- IP地址的表示方法

  把整个Internet网堪称单一的网络，IP地址就是给每个连在Internet网的主机分配一个在全世界范围内唯一的标示符，Internet管理委员会定义了A、B、C、D、E五类地址，在每类地址中，还规定了**网络编号和主机编号**。在 TCP/IP协议中，IP地址是以二进制数字形式出现的，共32bit，1bit就是二进制中的1位，但这种形式非常不适用于人阅读和记忆。因此Internet管理委员会决定采用一种点分十进制表示法表示IP地址：面向用户的文档中，由四段构成的32 比特的IP地址被直观地表示为四个以圆点隔开的十进制整数，其中，每一个整数对应一个字节（8个比特为一个字节称为一段）。A、B、C类最常用，下面加以介绍。本文介绍的都是版本4的IP地址，称为IPv4.

  ![img](/img/tcp-ip-3.gif)

从上图可以看出：

- A类地址：**A类地址的网络标识由第一组8位二进制数表示**， A类地址的特点是网络标识的第一位二进制数取值必须为0。不难算出，A类地址第一个地址为00000001，最后一个地址是01111111，换算成十进制就是127，其中127留作保留地址，A类地址的第一段范围是：1～126，A类地址允许有27 -2=126个网段（减2是因为0不用，127留作它用，127.0.0.1），网络中的主机标识占3组8位二进制数，每个网络允许有224-2=16777216台主机（减2是因为全0地址为网络地址，全1为广播地址，这两个地址一般不分配给主机）。通常分配给拥有大量主机的网络。
- B类地址：**B类地址的网络标识由前两组8位二进制数表示**，网络中的主机标识占两组8位二进制数，B类地址的特点是网络标识的前两位二进制数取值必须为10。 B类地址第一个地址为10000000，最后一个地址是10111111，换算成十进制B类地址第一段范围就是128～191，B类地址允许有214 =16384个网段，网络中的主机标识占2组8位二进制数，每个网络允许有216-2=65533台主机，适用于结点比较多的网络。
- B类地址：B类地址的网络标识由前两组8位二进制数表示，网络中的主机标识占两组8位二进制数，B类地址的特点是网络标识的前两位二进制数取值必须为10。 B类地址第一个地址为10000000，最后一个地址是10111111，换算成十进制B类地址第一段范围就是128～191，B类地址允许有214 =16384个网段，网络中的主机标识占2组8位二进制数，每个网络允许有216-2=65533台主机，适用于结点比较多的网络。
- C类地址：**C类地址的网络标识由前3组8位二进制数表示**，网络中主机标识占1组8位二进制数C类地址的特点是网络标识的前3位二进制数取值必须为110。C类地址第一个地址为11000000，最后一个地址是11011111，换算成十进制C类地址第一段范围就是192～223，C类地址允许有221 =2097152个网段，网络中的主机标识占1组8位二进制数，每个网络允许有28-2= 254台主机，适用于结点比较少的网络。

越到后面网络，主机就越少，网络编号越长，主机编号越少。

有些人对范围是2x不太理解，举个简单的例子加以说明。如C类网，每个网络允许有28-2= 254台主机是这样来的。因为C类网的主机位是8位，变化如下:

​    00000000

​    00000001

​    00000010

​    00000011

​    ……

​    11111110

​    11111111

 除去00000000和11111111不用外，从00000001到11111110共有254个变化，也就是28-2个。下图是IP地址的使用范围

![img](/img/tcp-ip-0.gif)

- 几个特殊的IP地址

  - **私有地址**

   上面提到IP地址在全世界范围内唯一，看到这句话你可能有这样的疑问，**像192.168.0.1这样的地址在许多地方都能看到，并不唯一，这是为何**？Internet管理委员会规定如下地址段为**私有地址，私有地址可以自己组网时用，但不能在Internet网上用**，Internet网没有这些地址的路由，有这些地址的计算机要上网必须转换成为合法的IP地址,也称为公网地址，这就像有很到的世界公园，**每个公园内都可命名相同的大街，如香榭丽舍大街**，**但对外我们只能看到公园的地址和真正的香榭丽舍大街**。下面是A、B、C类网络中的私有地址段。你自己组网时就可以用这些地址了。

  ```
  10.0.0.0～10.255.255.255

  172.16.0.0～172.131.255.255

  192.168.0.0～192.168.255.255
  ```

  - **回送地址**

   A类网络地址127是一个保留地址，用于网络软件测试以及本地机进程间通信，叫做回送地址（loopback address）。无论什么程序，一旦使用回送地址发送数据，协议软件立即返回之，不进行任何网络传输。含网络号127的分组不能出现在任何网络上

  - Ping 127.0.0.1,如果反馈信息失败,说明IP协议栈有错,必须重新安装TCP/IP协议。如果成功,ping本机IP地址,如果反馈信息失败,说明你的网卡不能和IP协议栈进行通信。
  - 如果网卡没接网线，用本机的一些服务如Sql Server、IIS等就可以用127.0.0.1这个地址
  - **网络地址**

    TCP/IP协议规定，各位全为0的网络号被解释成本网络。由上可以看出：一、含网络号127的分组不能出现在任何网络上；二、主机和网关不能为该地址广播任何寻径信息。由以上规定可以看出，主机号全0全1的地址在TCP/IP协议中有特殊含义，一般不能用作一台主机的有效地址。

  - **广播地址**

   TCP/IP规定，主机号全为1的网络地址用于广播之用，叫做广播地址。所谓广播，指同时向同一子网所有主机发送报文。

- 子网掩码

  从上面的例子可以看出，子网掩码的作用就是和IP地址与运算后得出网络地址，子网掩码也是32bit，并且是一串1后跟随一串0组成，其中1表示在IP地址中的网络号对应的位数，而0表示在IP地址中主机对应的位数。

  **标准子网掩码**

   A类网络（1 - 126） 缺省子网掩码：255·0·0·0

   255·0·0·0 换算成二进制为 11111111·00000000·00000000·00000000

   可以清楚地看出前8位是网络地址，后24位是主机地址，也就是说，如果用的是标准子网掩码，看第一段地址即可看出      是不是同一网络的。如21.0.0.0.1和21.240.230.1，第一段为21属于A类，如果用的是默认的子网掩码，那这两个地址就是一个网段的。

   B类网络（128 - 191） 缺省子网掩码：255·255·0·0

   C类网络（192 - 223） 缺省子网掩码：255·255·255·0

   B类、C类分析同上

  **特殊的子网掩码**

  标准子网掩码出现的都是255和0的组合，在实际的应用中还有下面的子网掩码

  255·128·0·0

  255·192·0·0

  。。。。。。

  255·255·192·0

  255·255·240·0 

  。。。。。。

   255·255·255·248

  255·255·255·252

  这些子网掩码又是什么意思呢？这些子网掩码的出现是为了把一个网络划分成多个网络。

  还记得上面的例子吗？如下所示：192·168·0·1和192·168·0·200如果是默认掩码255.255.255.0两个地址就是一个网络的，如果掩码变为255.255.255.192这样各地址就不属于一个网络了。下面的子网划分将作详细介绍。

![img](/img/tcp-ip-1.jpg)

​     表1是几个子网掩码计算过程中非常有用的十进制和二进制的对照

![img](/img/tcp-ip-2.jpg)

- IPv4与IPv6的转换

  IPv6地址为128位长但通常写作8组每组四个十六进制数的形式。例如：

  2001:0db8:85a3:08d3:1319:8a2e:0370:7344 是一个合法的IPv6地址。

  **如果四个数字都是0，可以被省略**。例如：

  2001:0db8:85a3:0000:1319:8a2e:0370:7344 等价于 2001:0db8:85a3::1319:8a2e:0370:7344

  遵从这些规则，如果因为省略而出现了两个以上的冒号的话，可以压缩为一个，但这种零压缩在地址中只能出现一次。因此：

  2001:0DB8:0000:0000:0000:0000:1428:57ab

  2001:0DB8:0000:0000:0000::1428:57ab

  2001:0DB8:0:0:0:1428:57ab

  2001:0DB8:0::0:1428:57ab

  2001:0DB8::1428:57ab

  都是合法的地址，并且他们是等价的。但

  2001::25de::cade 是非法的。（因为这样会使得搞不清楚每个压缩中有几个全零的分组）同时前导的零可以省略，因此：2001:0DB8:02de::0e13 等价于 2001:DB8:2de::e13 如果这个地址实际上是IPv4的地址 后32位可以用10进制数表示；因此：

  **IPv4地址可以很容易的转化为IPv6格式**。举例来说，如果IPv4的一个地址为135.75.43.52（十六进制为0x874B2B34），它可以被转化为0000:0000:0000:0000:0000:0000:874B:2B34或者::874B:2B34。同时，还可以使用混合符号（IPv4-compatible address），则地址可以为::135.75.43.52。