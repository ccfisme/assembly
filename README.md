一直对编译器是怎么编译成汇编的感到很困惑，因为编译器是C语言编的，那又怎么来实现由高级语言变成低级语言呢？后来参考了[一篇文章](https://kknews.cc/tech/rq452x.html)，发现语法分析后编程汇编的过程原来是一个递推，由汇编到C1语言、C2语言、、、、、Cn语言、C语言，是递推对应的  

![image](https://user-images.githubusercontent.com/74129445/139772740-7f1afe5b-b7b3-4d98-8d4d-4a73b1a1190b.png)
