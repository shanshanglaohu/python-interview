# Pyhton面试题及答案

> python面试题来自[博客](https://www.cnblogs.com/wupeiqi/p/9078770.html)

## 第一部分：python基础篇

1. 通过代码实现如下转换：
    二进制转换成十进制：v = “0b1111011”
    十进制转换成二进制：v = 18
    八进制转换成十进制：v = “011” 
    十进制转换成八进制：v = 30
    十六进制转换成十进制：v = “0x12” 
    十进制转换成十六进制：v = 87 

    python 进制之间转换如下：
    ```python
    # 二进制转换成十进制：v = “0b1111011”
    int("0b1111011", 2)
    # 十进制转换成二进制：v = 18
    bin(18)
    # 八进制转换成十进制：v = “011”
    int("011", 8)
    # 十进制转换成八进制：v = 30
    oct(30)
    # 十六进制转换成十进制：v = “0x12” 
    int("0x12", 16)
    # 十进制转换成十六进制：v = 87
    hex(87)
    ```

2. 请编写一个函数实现将IP地址转换成一个整数。
    如 10.3.9.12 转换规则为：

    |转码前|转码后|
    |:--:|:--:|
    |10|00001010|
    |3|00000011|
    |9|00001001|
    |12|00001100|

    再将以上二进制拼接起来计算十进制结果：00001010 00000011 00001001 00001100 = ？

    ```python
    # 定义IP数字到二进制表达式的转换函数
    def ipnumber2bin(num):
        if num < 0 or num > 255:
            raise OverflowError("IP值必须大于等于0小于等于255")
        else:
            tmp = '' if num else '0'
            while num:
                tmp += str(num % 2)
                num = num // 2
            return "{:0>8}".format(tmp[::-1])
    
    # 定义IP值到整数的转换函数
    def ip2int(ip):
        return int(''.join(ipnumber2bin(int(num)) for num in ip.strip().split(".")), 2)


    # 当然，使用python标准库ipaddress能更加快捷方便的处理这个问题
    form ipaddress import ip_address
    int(ip_address("10.3.9.12"))
    ```

3. python递归最大层数？
    ```python
    # python最大递归深度根据不同的python版本和系统有所不同
    import sys
    print(sys.getrecursionlimit())
    ```
## 第二部分：网络编程和并发
## 第三部分：数据库和缓存
## 第四部分：前端、框架和其它