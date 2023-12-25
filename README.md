# 西安交通大学操作系统实验

## Exp1: 进程线程  
## Exp2: 信号内存  
## Exp3: 驱动聊天  
前两个的代码都比较简单易懂，仅介绍一下**聊天程序**的实现思路。  
聊天设计成了多线程(这是一个败笔，应该做成多进程)相互通信的形式，主线程负责从键盘接收输出选择当前在终端前台工作的用户线程，同时其他未被选中的用户线程轮询等待。被选中的用户线程开始对驱动设备执行写操作或者读操作。  
程序支持私聊和群聊，私聊的实现是在写入消息时输入“@用户下标”，群聊则是直接输入消息。用户下标就是在程序开始时分配的数组下标，从0开始。私聊结束的标志是目标用户读过消息。相关过程过程中设备会被占用，会显示出占用设备的用户。
