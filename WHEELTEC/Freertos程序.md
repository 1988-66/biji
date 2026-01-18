1.![[Pasted image 20260115102621.png]]
BootLoader程序占64kb。
2.记得没有写自动复位时，要手动复位。
**3.FreeRTOS**
（1）
![[Pasted image 20260115161127.png]]
![[Pasted image 20260115161145.png]]
（2）
![[Pasted image 20260115161719.png]]
![[Pasted image 20260115161749.png]]
（3）
![[Pasted image 20260115162140.png]]
![[Pasted image 20260115162323.png]]
当检测到栈溢出时，函数的`pcTaskName`参数会传入**发生溢出的任务名称**，`xTask`是该任务的句柄。你可以在这个函数里添加打印（比如用串口输出），把`pcTaskName`显示出来，就能知道是哪个任务栈不够了。
如果需要更详细的信息（比如建议栈大小），得自己手动调试：比如先增大该任务的栈空间，再观察是否还溢出。
（4）
![[Pasted image 20260115163042.png]]
总的空间：
![[Pasted image 20260115163152.png]]
![[Pasted image 20260115162955.png]]
（5）打印栈的占用情况
![[Pasted image 20260116200858.png]]
其中空闲任务占大头。
（6）freertos提醒
![[Pasted image 20260116203634.png]]
只要不特意在stm32cubemx修改过，5就不会发生
（6）Freertos的常用API函数
![[Pasted image 20260116204524.png]]
