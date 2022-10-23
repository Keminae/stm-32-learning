## stm-32 learning
###一.download
>keil MDK ,CH34驱动,stlink 驱动,ISO 串口
### 二.learning
1.  how to create new project 
2.  GPIO working principle
> - 操作寄存器CRL，CRH
> - 输入输出工作模式
> - 初始化GPIO格式
> GPIO_InitTypeDef GPIO_InitStructure;
GPIO_InitStructure.GPIO_Pin = GPIO_Pin_5; //LED0-->PB.5 端口配置
GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP; //推挽输出
GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;//速度 50MHz
GPIO_Init(GPIOB, &GPIO_InitStructure);//根据设定参数配置 GPIO
> - IO操作
>1） 使能 IO 口时钟。调用函数为 RCC_APB2PeriphClockCmd()。
2） 初始化 IO 参数。调用函数 GPIO_Init();
3） 操作 IO。
>- BRR BSRR 清除
3.  blink
> -
>int main(void)
{ 
	delay_init();		
	LED_Init();		    
	while(1)
	{
			GPIO_ResetBits(GPIOB,GPIO_Pin_5); 
			GPIO_SetBits(GPIOE,GPIO_Pin_5);  
			delay_ms(300);  		 
			GPIO_SetBits(GPIOB,GPIO_Pin_5);	  
			GPIO_ResetBits(GPIOE,GPIO_Pin_5);
			delay_ms(300);             
	}
} 