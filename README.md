# 注意事项   

* 汇编指令操作位数要一致    

![image](https://user-images.githubusercontent.com/74129445/152677475-04d0569c-00c5-4684-ab94-0d93c807eec6.png)   

* CS和IP的值只能用jmp指令修改，jmp改变有两种方式，，一个是CS和IP都可以改，用的是段地址加偏移地址的表示方法；一个是只改IP，用的是jmp+寄存器的表示方式   

```
方法一：改CS IP
jmp 3:45A  //跳到048AH，含义上类似于mov CS，3   mov IP，45A

方法二：改IP
jmp ax（其中ax = 10H）  //跳到0010H，含义上类似于mov IP ax
```

在jmp这里还有一个小点，就是jmp到指定指令后会顺序执行至最后一条，在最后一条的时候会自动再跳一次，跳回到最开始跳的指令的下一条

# 底层原理
* 程序运行的底层原理，比学过的计算机组成原理思路更清晰   
![image](https://user-images.githubusercontent.com/74129445/153238988-b9e7f101-abcd-4e72-97bf-b126ca8f8509.png)  

![image](https://user-images.githubusercontent.com/74129445/152995642-ffdca0cc-d90f-4b1e-bf71-30e8e6429e7f.png)  

![image](https://user-images.githubusercontent.com/74129445/152995090-efaa27cb-cb5f-483d-9208-2a087092ff9f.png)  

![image](https://user-images.githubusercontent.com/74129445/152995137-ec51f939-1da2-4ac4-941a-32a1352d2983.png)  

![image](https://user-images.githubusercontent.com/74129445/152995230-9240d8ec-e1bc-42ba-8a68-024f15090742.png)  

![image](https://user-images.githubusercontent.com/74129445/152995293-e3bf89f9-f32d-4417-857d-878165d4be36.png)  

![image](https://user-images.githubusercontent.com/74129445/152995330-7b2c3e14-fe53-4826-bf82-521cff41c0dc.png)  

![image](https://user-images.githubusercontent.com/74129445/152995385-106f1457-fd19-4108-a719-61daac947268.png)  

![image](https://user-images.githubusercontent.com/74129445/152995433-90a3c781-bb86-4089-abdf-591e9aa22639.png)  

![image](https://user-images.githubusercontent.com/74129445/152995492-c9e4fdff-a0b8-4e35-826a-4e6c1e290685.png)   


