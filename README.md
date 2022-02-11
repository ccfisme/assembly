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

# 操作win7debug  

* r指令  

这个r是用来查看和改变**寄存器**里存的地址的   

  * 查看为 ```-r ``` 

  图片为  

![image](https://user-images.githubusercontent.com/74129445/153582213-b7f1f29f-3179-4a88-b001-4057deaef569.png)  
上两行为寄存器和寄存器里面的地址，下面正常应该是只有一行，```CS:IP 机器数 汇编指令```，但这个机器有两行，不知道为什么，等着问问  

  * 修改寄存器里的存地址为 ```-r 寄存器```  
  图片为  
  
  ![image](https://user-images.githubusercontent.com/74129445/153582720-bd2ee338-51b0-4a88-93a1-c8866d04d1b8.png)  
  输入完```-r 寄存器```回车后，会另起一行出来一个冒号，输入想改变的地址，按回车  
* d指令  
这个d只能用来**查看内存**  
  * 查看128个为 ```-d CS:IP```(该CS:IP是当前单元行的首地址)  
  
  图片为  
  ![image](https://user-images.githubusercontent.com/74129445/153584630-36975565-8c6a-4e3f-8783-e62ae7c4e3d9.png)  
  三部分 
   * 左边的是当前单元行的首地址
   * 中间的是16个存储单元里面存储的机器码，中间的-没有实际意义，就是为了便于看中间  
   * 右边的是ASCII代码
  * 查看单元行内指定范围的存储单元```-d CS:IP1 IP2```(IP1为行首地址，IP2为范围)

  图片为   
  ![image](https://user-images.githubusercontent.com/74129445/153596153-0195698e-8267-405e-8a12-1a25e001cda2.png)  
  
  
  
  
  


