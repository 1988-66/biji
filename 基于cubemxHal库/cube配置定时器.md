1.`Error_Handler()` **不是 HAL 库核心源码里自带的通用函数**，而是**CubeMX 生成工程时自动创建的 “用户自定义错误处理函数”**，函数体默认是 “禁用中断 + 死循环”，你可以根据需求修改（比如加 LED 闪烁、串口打印错误信息）。

![[Pasted image 20260108094950.png]]
![[Pasted image 20260108095108.png]]
（1）定时中断控制LED

![[Pasted image 20260108095304.png]]
开启中断
![[Pasted image 20260108095405.png]]
**选择PA9为LED工作引脚（推挽输出）：**
HAL_TIM_Base_Start_IT(&htim2);//开始定时器中断
 
 
//中断回调函数
void HAL_TIM_PeriodElapsedCallback(TIM_HandleTypeDef *htim)
{
	HAL_GPIO_TogglePin(GPIOA, GPIO_PIN_9);
	
	
}
- `HAL_TIM_Base_Start_IT(&htim2);`：属于初始化后启动定时器中断的代码，要放在 `/* USER CODE BEGIN 2 */` 和 `/* USER CODE END 2 */` 之间（main 函数中初始化外设之后、死循环之前）；
- `HAL_TIM_PeriodElapsedCallback` 回调函数：属于用户自定义函数，要放在 `/* USER CODE BEGIN 4 */` 和 `/* USER CODE END 4 */` 之间（这个区域专门用于存放用户自定义的回调函数、辅助函数）。