# 寄存器的位与位置
一开始狂神说什么32位的寄存器，16位的寄存器，8位的，还有什么高低吓我一跳，不过后来看了一张图，感觉应该不是寄存器，更像是位置。比如ah和al，就是15 ~ 8和7 ~ 0这个范围   

![image](https://user-images.githubusercontent.com/74129445/151594341-a3b77439-4fd4-4549-b800-60e3ecd14a86.png)   

参考：https://zhuanlan.zhihu.com/p/76950607

---------   
# 数据段寄存器的发展史   

[数据段段地址寄存器的历史](https://blog.csdn.net/michael2012zhao/article/details/5554023)   

> 段寄存器的产生源于Intel 8086 CPU体系结构中数据总线与地址总线的宽度不一致。

  为什么这么说呢？   
  其实很简单，数据总线宽度一般是和CPU内寄存器的位数直接挂钩的，比如数据总线宽度和寄存器位数都是16位，地址总线宽度也是16位，那就可以直接用一个寄存器找数,但16位的话，2^16个存储单元，也就是64KB的内存，太小了；可如果地址总线的宽度是20位，那么16位的寄存器肯定不能够找到（这个时候没有CS,DS,ES,SS）位数不对，所以决定定义一个新的寄存器专门用于存放地址的高4位，但是这样下来，每写一次地址，要用两个寄存器装，汇编代码就可能是```mov ax,1122H         mov bx,12H  ```，太麻烦，每找一个地址就要写两行汇编，但还必须要用这种方式，因为扩充到更高位寄存器的技术还没有，所以就得对这种找一个地址写两行汇编的方式进行优化，这时候就分类了，四种段，指令、数据、其它和堆栈，并设计了新的四个寄存器CS，DS，ES和SS用来保存前面的四种段地址（当然这些段地址寄存器还是16位的，而且是由于后加的原因，所以硬件的布局比较草率，不让直接往段地址寄存器存数，而是要通过寄存器来做中间人赋值 ```mov ax,1000H         mov ds,ax```）。



