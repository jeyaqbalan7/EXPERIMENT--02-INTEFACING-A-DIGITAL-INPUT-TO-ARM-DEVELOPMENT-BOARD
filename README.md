# EX-02 INTEFACING A DIGITAL INPUT TO ARM DEVELOPMENT BOARD  
### Aim:  
To Interface a Digital Input  (userpush button ) to ARM   development board and write a  program to obtain  the data and flash the led.
### Components required:   
STM32 CUBE IDE, ARM IOT development board,  STM programmer tool.
### Theory: 
The full form of an ARM is an advanced reduced instruction set computer (RISC) machine, and it is a 32-bit processor architecture expanded by ARM holdings. The applications of an ARM processor include several microcontrollers as well as processors. The architecture of an ARM processor was licensed by many corporations for designing ARM processor-based SoC products and CPUs. This allows the corporations to manufacture their products using ARM architecture. Likewise, all main semiconductor companies will make ARM-based SOCs such as Samsung, Atmel, TI etc.
### Procedure:
<table>
  <tr>
    <td width="50%">
      1. click on STM 32 CUBE IDE, the following screen will appear.
    </td>
    <td>
      <img height=7% width=90% src="https://user-images.githubusercontent.com/36288975/226189166-ac10578c-c059-40e7-8b80-9f84f64bf088.png">
    </td>
  </tr>
  <tr>
    <td width="50%">
      2. click on FILE, click on new stm 32 project.
    </td>
    <td width="50%">
  <img src="https://user-images.githubusercontent.com/36288975/226189215-2d13ebfb-507f-44fc-b772-02232e97c0e3.png">
    <img src="https://user-images.githubusercontent.com/36288975/226189230-bf2d90dd-9695-4aaf-b2a6-6d66454e81fc.png">
    </td>
  </tr>
  <tr>
    <td width="50%">
      3. select the target to be programmed  as shown below and click on next.
    </td>
    <td width="50%">
      <img src="https://user-images.githubusercontent.com/36288975/226189280-ed5dcf1d-dd8d-43ae-815d-491085f4863b.png">
    </td>
  </tr>
   <tr>
    <td width="50%">
      4.select the program name.
    </td>
    <td >
      <img height=10% width=50% src="https://user-images.githubusercontent.com/36288975/226189316-09832a30-4d1a-4d4f-b8ad-2dc28f137711.png">
    </td>
  </tr>
     <tr>
    <td width="50%">
      5. corresponding ioc file will be generated automatically.
    </td>
    <td width="50%">
      <img src="https://user-images.githubusercontent.com/36288975/226189378-3abbdee2-0df6-470f-a3cd-79c74e3d3ad8.png">
    </td>
  </tr>
    <tr>
    <td width="50%">
      6.select the appropriate pins as gipo, in or out, USART or required options and configure.
    </td>
    <td width="50%">
      <img src="https://user-images.githubusercontent.com/36288975/226189403-f7179f1a-3eae-4637-826b-ab4ec35ba1e1.png">
    </td>
  </tr>
    <tr>
    <td width="50%">
      7.click on cntrl+S , automaticall C program will be generated.
    </td>
    <td width="50%">
<img src="https://user-images.githubusercontent.com/36288975/226189443-8b43451d-0b14-47e4-a20b-cc09c6ad8458.png">
	    <img src="https://user-images.githubusercontent.com/36288975/226189450-85ffa969-2ffb-4788-81e5-72d60fdda0f1.png">  
    </td>
  </tr>
    <tr>
    <td width="50%">
      8. edit the program and as per required.
    </td>
    <td width="50%">
      <img src="https://user-images.githubusercontent.com/36288975/226189461-a573e62f-a109-4631-a250-a20925758fe0.png">
    </td>
  </tr>
  <tr>
    <td width="50%">
      9. Add necessary library files of LCD 16x2 , write the program and use project and build.
    </td>
    <td width="50%">
      <img src="https://user-images.githubusercontent.com/36288975/226189554-3f7101ac-3f41-48fc-abc7-480bd6218dec.png">
    </td>
  </tr>   
  <tr>
    <td width="50%">
      10. once the project is bulild.
    </td>
    <td width="50%">
      <img src="https://user-images.githubusercontent.com/36288975/226189577-c61cc1eb-3990-4968-8aa6-aefffc766b70.png">
    </td>
  </tr>  
  <tr>
    <td width="50%">
      11. click on debug option.
    </td>
    <td width="50%">
      <img src="https://user-images.githubusercontent.com/36288975/226189625-37daa9a3-62e9-42b5-a5ce-2ac63345905b.png">
    </td>
  </tr>  
  
  <tr>
    <td width="50%">
      
  12.  Creating Proteus project and running the simulation.
  We are now at the last part of step by step guide on how to simulate STM32 project in Proteus.
13. Create a new Proteus project and place STM32F40xx i.e. the same MCU for which the project was created in STM32Cube IDE. 
14. After creation of the circuit as per requirement as shown below
    </td>
    <td width="50%">
      <img src="https://user-images.githubusercontent.com/36288975/233856847-32bea88a-565f-4e01-9c7e-4f7ed546ddf6.png">
    </td>
  </tr>  
  <tr>
    <td width="50%">
      15. Double click on the the MCU part to open settings. Next to the Program File option, give full path to the Hex file generated using STM32Cube IDE. Then set the external crystal frequency to 8M (i.e. 8 MHz). Click OK to save the changes.
https://engineeringxpert.com/wp-content/uploads/2022/04/26.png

16. click on debug and simulate using simulation as shown below 


    </td>
    <td width="50%">
      <img src="https://user-images.githubusercontent.com/36288975/233856904-99eb708a-c907-4595-9025-c9dbd89b8879.png">
    </td>
  </tr>  
  
</table>

### STM 32 CUBE PROGRAM :
```
Jeyabalan
212222240040
```
```C
#include "main.h"
#include "stdbool.h"
bool button_status;
void push_button();
int main(void)
{
  HAL_Init();
  SystemClock_Config();
  MX_GPIO_Init();
  while (1)
  {
   push_button();
  }
}
void push_button()
{
	 button_status=HAL_GPIO_ReadPin(GPIOC,GPIO_PIN_13);
	 if(button_status==0)
	 {
    HAL_GPIO_WritePin(GPIOA,GPIO_PIN_5,SET);
		  HAL_Delay(50);
		  HAL_GPIO_WritePin(GPIOA,GPIO_PIN_5,RESET);
		  HAL_Delay(50);
	}
	else
	{
		HAL_GPIO_WritePin(GPIOA,GPIO_PIN_5,RESET);
	}
}
```

### Output  :
![pmc exp22](https://github.com/jeyaqbalan7/EXPERIMENT--02-INTEFACING-A-DIGITAL-INPUT-TO-ARM-DEVELOPMENT-BOARD/assets/119393851/a2dc15cf-b5a9-40fb-aaae-99b179a838ea)


## Result :
Interfacing a digital Input (Pushbutton ) with ARM microcontroller based IOT development is executed and the results are verified.
