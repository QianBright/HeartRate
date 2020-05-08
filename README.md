# HeartRate
> 调研报告：基于光电传感器技术的心率/脉率检测方法研究<br />

一个Arduino为微处理器的心率检测仪，传感器为光电传感器，实时显示心率。<br>

# 基于光电传感器的心率/脉率检测方法研究
## 基本原理
### 光电转化原理
&emsp;&emsp;[光电二极管][photodiode]的基础结构通常是一个PN结或者PIN结。当一个具有充足能量的光子冲击到二极管上，它将激发一个电子，从而产生自由电子（同时有一个带正电的空穴）。这样的机制也被称作是内光电效应。如果光子的吸收发生在结的耗尽层，则该区域的内电场将会消除其间的屏障，使得空穴能够向着阳极的方向运动，电子向着阴极的方向运动，于是光电流就产生了。实际的光电流是暗电流和光照产生电流的综合，因此暗电流必须被最小化来提高器件对光的灵敏度。<br>
#### *光电导模式*
&emsp;&emsp;当工作在这一模式时，光电二极管常常被反向偏置，急剧的降低了其响应时间，但是噪声不得不增加作为代价。同时，耗尽层的宽度增加，从而降低了结电容，同样使得响应时间减少。反向偏置会造成微量的电流（饱和电流），这一电流与光电流同向。对于指定的光谱分布，光电流与入射光照度之间呈线性比例关系。<br>
&emsp;&emsp;尽管这一模式响应速度快，但是它会引发更大的信号噪声。一个良好PIN二极管的泄漏电流很小（小于1nA），因此负载电阻的约翰逊·奈奎斯特噪声（Johnson–Nyquist noise）会造成较大的影响。<br>

### 光电容积法
&emsp;&emsp;[光电容积法(PPG)][PPG]是一种简单且价格低廉的光学技术，可以探测微血管的血液体积变化，进而测量心率，具有方法简单、佩戴方便、可靠性高等特点。<br>
&emsp;&emsp;光电容积法是利用人体组织在血管搏动时产生透光率不同来进行心率测量的。其传感器由光源和光电变换器两部分组成，通过绑带或夹子固定在人体的手指或耳垂上。传感器光源的选择有一定的讲究，一般采用对人体动脉血中的氧和血红蛋白有选择性的一定波长（500~700nm）的发光二极管。当光束透过人体外周血管时，由于动脉搏动充血容积变化导致光束的透光率发生改变，同时，光电变换器接收到经过人体组织反射的光线，将其转变为电信号并将其放大和输出。由于心率是随心脏的搏动而周期性变化的信号，动脉血管容积也周期性的变化，因此光电变换器输出的电信号的变化周期就是心率。<br>

## 项目设计方案
基于光电传感器，小型便携家用心率测量，使用三个七段数码管显示。（戒指/指套？太小可能实现不了）<br>
肤色不同、手指粗细不同，绿光与红光的区别，光电容积法PPG<br>
光电传感器采集到的原始心率信号极其微弱（变化幅值在＋10mV之间）<br>
信号采集电路：
放大电路：
滤波电路：
中央处理器电路：
显示电路：

## 系统结构设计

# 基于光电传感器的心率/脉率检测系统具体器件选型
发光二极管LED：AM2520(绿)<br>
光接收器：APDS-9008 //光敏电阻or光电二极管<br>
运放：MCP6001<br>
差分放大：<br>
滤波：<br>
微处理器：arduino uno<br>
显示：LCD 16X2<br>
电源：<br>

# 参考
1. [Pulse sersor][sersor]<br>
2. [TINKERCAD][tinkercad]<br>
3. [proteus仿真arduino中使用PCF8574以I2C方式操作LCD1602][xiHe]
4. [手指检测心跳设计——传感器制作篇][shouZhi]
5. [基于uFUN开发板的心率计（一）DMA方式获取传感器数据][wangchao1]
6. [基于uFUN开发板的心率计（二）动态阈值算法获取心率值][wangchao2]
7. [基于uFUN开发板的心率计（三）Qt上位机的实现][wangchao3]

# 测量仪器设计拓展
## 一般结构
* **传感器：** 实现生理信号从非电量到电量的变换；<br>
* **传感器接口电路：** 将传感器输出信号转换成低输出电阻的电压信号；<br>
* **放大滤波器：** 获得纯净可识别信号；<br>
* **ADC：** 模拟/数字变换，得到数字信号；<br>
* **微处理器/微控制器：** 实现信号输出显示、存储、控制，以及改变电路参数。<br>

## 设计原则
确定目标，总体框架，功能模块，具体技术，具体型号，参数选择<br>
先从整体考虑，逐步精细化，直至达成目标。(自上而下)<br>
1. 被测量的量是什么？信号的大小与频率是多少？（心率，很小，60~100次/min）<br>
2. 输出是什么？如何与使用者传达信息？（通过显示屏输出）<br>
3. 仪器的测量的精度、性能<br>
4. 仪器的使用条件<br>
5. 仪器的功能（测量心率）<br>
6. ~~成本、工艺条件~~<br>

[photodiode]:"https://zh.wikipedia.org/wiki/%E5%85%89%E7%94%B5%E4%BA%8C%E6%9E%81%E7%AE%A1 "光电二极管"
[PPG]:https://www.cdstm.cn/gallery/media/mkjx/wxd/201605/t20160525_321684.html "光电容积法"
[sersor]:https://pulsesensor.com/ "光电传感器模块"
[tinkercad]:https://www.tinkercad.com/ "Arduino仿真"
[xiHe]:https://blog.csdn.net/haigear/article/details/88935697 "proteus仿真arduino中使用PCF8574以I2C方式操作LCD1602"
[shouZhi]:https://blog.csdn.net/qq_34445388/article/details/79781181/ "手指检测心跳设计——传感器制作篇"
[wangchao1]:http://www.wangchaochao.top/2019/03/23/uFun-3/ "基于uFUN开发板的心率计（一）DMA方式获取传感器数据"
[wangchao2]:http://www.wangchaochao.top/2019/03/31/uFun-5/ "基于uFUN开发板的心率计（二）动态阈值算法获取心率值"
[wangchao3]:http://www.wangchaochao.top/2019/04/05/uFun-6/ "基于uFUN开发板的心率计（三）Qt上位机的实现"