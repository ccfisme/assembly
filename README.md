此为汇编每日学习笔记，助我记忆并理解汇编的各种操作  

[王爽汇编答案](https://github.com/sanmianti/AssemblyLanguageTest/blob/master/%E3%80%8A%E6%B1%87%E7%BC%96%E8%AF%AD%E8%A8%80%E3%80%8B%E7%AC%AC%E4%B8%89%E7%89%88%E6%A3%80%E6%B5%8B%E7%82%B9%E7%AD%94%E6%A1%88.md)

# 视频主目录

* [进制，本质还是科学计数法（八进制12 = 1 * 8的一次方 + 2 * 8的0次方）](https://www.bilibili.com/video/BV1ni4y1G7B9?p=3&spm_id_from=pageDriver)

* [数据宽度](https://www.bilibili.com/video/BV1ni4y1G7B9?p=6&spm_id_from=pageDriver)  

* [原码反码补码，有符号的二进制运算。（其实计算机所有的正负数加减运算都用的是补码，如果>0,就是正原码的补码，还是原码；如果<0，就是负原码的补码，则计算原理可参考https://www.zhihu.com/question/20159860）](https://www.bilibili.com/video/BV1ni4y1G7B9?p=8&spm_id_from=pageDriver)  

注：计算机网络的数据链路层CRC检验部分用的规则是模二运算，即加和减不进位也不借位，是独立于加减法则之外的运算规则，遵循异或门法则，即相同为0，相反为1，所以一直让我有疑惑，是否加减都对应着与门或门异或门的逻辑，实则不然，因为这些单独的门的运算没有结合**进位和借位**，所以单独的与或非等门和正常的加减没有关系，[正常的加减乘除都是用多个门结合来计算](https://baike.baidu.com/item/%E5%85%A8%E5%8A%A0%E5%99%A8),现在已知的就是模二运算和单独的异或门有关系。 

```
模二运算  

1111 + 0001 = 1110  

1110 - 0001 = 1111
```

* [位运算介绍](https://www.bilibili.com/video/BV1ni4y1G7B9?p=9&spm_id_from=pageDriver)  

* [位运算在加减法中起到的作用](https://www.bilibili.com/video/BV1ni4y1G7B9?p=10&spm_id_from=pageDriver)  

位运算在加法中主要是与门运算后如果有值，则此值左移一位后与异或门运算后的值进行异或门运算  

![屏幕快照 2022-01-26 下午5 52 32](https://user-images.githubusercontent.com/74129445/151141338-2448ea9d-f0d1-4269-8fbd-3867043b86e3.png)  

此图为加法的运算，更详细的介绍在视频里，而减法则是取补码相加，乘法是成倍的相加，除法是成倍的相减（但实际运算还是根据进制乘法表找最接近的带进去），那么又用补码，则还是加法，总之计算机只会加法

* [汇编操作，C语言和c++必须先申请地址，然后汇编才能在申请的地址内部操作数据，以及一些操作内存数据的方法，为什么要定义数据类型等答案可以在这个视频看到](https://zhuanlan.zhihu.com/p/76950607)
---------

学习网址：https://www.bilibili.com/video/BV13J41117b9?p=1&share_medium=android&share_plat=android&share_session_id=3ec5ac21-b9f0-44a7-9548-d2fcd445825c&share_source=COPY&share_tag=s_i&timestamp=1633078433&unique_k=l2DChi  

[狂神说视频](https://www.bilibili.com/video/BV1ni4y1G7B9?p=3&spm_id_from=pageDriver)

