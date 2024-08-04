# STM32_Timer_LED_Control

A simple STM32 project to toggle an LED on board the STM32 nucleo board using Timer 10 of the STM32 NucleoF401RE.

## Blocking Mode:
The commented code in the main loop shows blinking an LED in blocking mode. The timer prescaler is set to 8000-1 and the auto reload counter is set to default 65535.

## Non Blocking Mode:
1) For this mode the timer prescaler is set to 8000-1 to generate a clock signal at 10KHZ. 
2) The auto reload counter register value is set to 10,000-1 so that we can generate a LED blink every 1 second. 
3) The interrupt is triggered on the rollover value (set in the auto reload register which is 10,000-1)
4) The interrupt callback function is a generic callback for all the timers so we need to specify what timer we are looking at and based on that, we toggle the GPIO pin for the LED.
5) From the Interrupt Vector Table we find the Tim10 global interrupt that triggers on the rollover value set in the auto reload register.



