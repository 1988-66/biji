1.开启编码器的引脚要复用对应TIM-CH，不然很难清楚引脚功能。
2.GPIO_InitStructure.GPIO_Mode = GPIO_Mode_AF;
    GPIO_InitStructure.GPIO_PuPd = GPIO_PuPd_NOPULL;
3.一个定时器只能运行**一个编码器模式**。