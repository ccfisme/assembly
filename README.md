# 注意事项   

* 汇编指令操作位数要一致    

![image](https://user-images.githubusercontent.com/74129445/152677475-04d0569c-00c5-4684-ab94-0d93c807eec6.png)   

* 本书用的是倒着存的内存   
 ![image](https://user-images.githubusercontent.com/74129445/153713191-ef6656f9-278e-432e-b044-70cf4dd48ddd.png)   
 


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

> CS和IP的值只能用jmp指令修改，jmp改变有两种方式，，一个是CS和IP都可以改，用的是段地址加偏移地址的表示方法；一个是只改IP，用的是jmp+寄存器的表示方式   

```
方法一：改CS IP
jmp 3:45A  //跳到048AH，含义上类似于mov CS，3   mov IP，45A

方法二：改IP
jmp ax（其中ax = 10H）  //跳到0010H，含义上类似于mov IP ax
```

## r指令  

这个r是用来查看和改变**指定寄存器**里存的地址的   

  * 查看为 ```-r ``` 

  图片为  

![image](https://user-images.githubusercontent.com/74129445/153582213-b7f1f29f-3179-4a88-b001-4057deaef569.png)  
上两行为寄存器和寄存器里面的地址，下面正常应该是只有一行，```CS:IP 机器数 汇编指令```，但这个机器有两行，不知道为什么，等着问问  

  * 修改寄存器里的存地址为 ```-r 指定寄存器```  
  图片为  
  
  ![image](https://user-images.githubusercontent.com/74129445/153582720-bd2ee338-51b0-4a88-93a1-c8866d04d1b8.png)  
  输入完```-r 寄存器```回车后，会另起一行出来一个冒号，输入想改变的地址，按回车  
## d指令  
这个d只能用来**查看指定IP后128范围内的内存或者查看指定IP范围内的内存**  
  * 查看128个为 ```-d CS:IP```(该CS:IP是当前单元行的首地址)  
  
  图片为  
  ![image](https://user-images.githubusercontent.com/74129445/153584630-36975565-8c6a-4e3f-8783-e62ae7c4e3d9.png)  
  三部分 
   * 左边的是当前单元行的首地址
   * 中间的是16个存储单元里面存储的机器码，中间的-没有实际意义，就是为了便于看中间  
   * 右边的是ASCII代码
  * 查看单元行内指定范围的存储单元```-d CS:IP1 IP2```(IP1为范围首地址，IP2为范围末地址)

  图片为   
  ![image](https://user-images.githubusercontent.com/74129445/153596153-0195698e-8267-405e-8a12-1a25e001cda2.png)  
  
  
  * 查看指定存储单元```-d CS:IP IP```(两个IP必须一致，才能锁定一个，为什么不能用CS:IP直接表示指定的存储单元呢？因为这是表示指定存储单元后128位的表示方法)    
  图片为  
  ![image](https://user-images.githubusercontent.com/74129445/153598327-04f55fdf-a85e-4116-aad5-03ec88dc7520.png)  
  
## e指令
这个e可以用来**改指定IP后的所有的机器字**，e和其他所有的指令都不同。别的指令在指令行确定首地址或者是范围，然后回车输入要做的改变；而e指令则是在指令行确定范围，然后继续在指令行输入改变的数。

  * e正常改机器数
    * 改机器数```-e CS:IP 1 2 3 4 5 6......```
     图片为   
     
     ![image](https://user-images.githubusercontent.com/74129445/153657165-5377cc87-dab3-42d5-93f5-3bbb9ab7e157.png)  
     
    * 改字符串```-e CS:IP 'a' 'b' 'asdfew'.........```  
     图片为   
     
      ![image](https://user-images.githubusercontent.com/74129445/153657331-b9eada26-3783-433d-bd33-9dc48c3bcaaa.png)  
      
  * e提问式改机器数```-e CS:IP```,回车后会逐个问是否修改当前机器字，修改完后按空格迭代至下一个，不管有没有操作或改动，只要摁空格，就会迭代到下一个  
    图片为   
    
    ![image](https://user-images.githubusercontent.com/74129445/153657583-d3888770-b387-4219-861b-8018a625ef71.png)   
    
    
## u指令(范围限定和d指令一样)  
把内存中的机器字转换为汇编  
如图：  

  ![image](https://user-images.githubusercontent.com/74129445/153657957-701bfe90-64a7-4284-ba28-6910a7137dd3.png)  
  
  如果范围内的机器字中在尾端的机器字不足以组成一句汇编，那么就会自动舍弃这个机器字   
  
## t指令
执行当前CS:IP的指令，并在执行结束后IP自增，用r指令查看时寄存器下的汇编会跳至下一句汇编   
如图:   

![image](https://user-images.githubusercontent.com/74129445/153658871-c8338fee-4a1b-4cec-bdb1-c484e1134f1c.png)  

## a指令  
直接写汇编，```-a CS:IP```,然后从当前地址开始写，想结束就回车,没办法用范围来限制结束  

如图:  

![image](https://user-images.githubusercontent.com/74129445/153659361-277cfdc6-db89-4a7a-abb1-029a1da868ab.png)  



