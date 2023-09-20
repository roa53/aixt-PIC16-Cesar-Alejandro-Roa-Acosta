
# Guía rapida PSoC4
Esta implementación de Aixt para PSoC 4 da soporte a la tarjeta   CY8CKIT14540XX

# Identificación tarjeta CY8CKIT14540XX	

## Vista
*Parte superior*
![](https://iotexpert.com/wp-content/uploads/2016/02/145front-e.png)
*Parte inferior*
![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ4ZfGdAnE2c-UQa2_0utN_ya3bh9NYv5eqZQ&usqp=CAU)

## Hoja de datos
[CY8CKIT14540XX](https://www.infineon.com/dgdl/Infineon-CY8CKIT-145-40XX_PSoC_4000S_Prototyping_Kit_Guide-UserManual-v01_00-EN.pdf?fileId=8ac78c8c7d0d8da4017d0efccdd91344)



# Configuración general

Se integran las funciones básicas del microcontrolados para generar una estructura hardware general, asi;

- 3 pwms
- 9 leds
- 1 pulsador
- 2 puertos de comunicación
- 3 entradas digitales
- 3 salidas digitales

## Puertos y nombramientos
A continuación se muestran los puertos que se usan y sus debidos nombramientos para la programación: 

Puerto | nombre |Tipo    |
--  |-       |-       |
2.5 |led1    |salida
2.0 |led4    |salida
2.1 |led5    |salida
2.2 |led6    |salida
2.3 |led7    |salida
2.4 |led8    |salida
3.4 |led9    |salida
3.5 |led10   |salida
3.6 |led11   |salida
0.7 |sw2     |entrada
2.7 |di0     |entrada
0.4 |di1     |entrada
1.7 |di2     |entrada
4.0 |do0     |salida
0.5 |do1     |salida
3.7 |do2     |salida
1.2 |out_pwm0|salida
2.6 |out_pwm1|salida
1.0 |out_pwm2|salida
3.0 |\uart:rx\ |salida
3.1 |\uart:tx\ |salida

## Retardos
```go
import time {
	sleep_ms,
	sleep_us,
}

sleep_us(1)     // sleep for 1 microsecond
sleep_ms(500)   // sleep for 500 milliseconds
```
## Leds
se enciende con un uno

## pines emulados
Use el module `machine` y el submodulo `{ pin }`.
```go
import machine { pin }

pin_high(led1)         // turn ON the led1 pin 
pin_low(led4)          // turn OFF the led4 pin 
pin_write(led5, 1)     // write 1 on led5 pin
pin_read(led6)         // read led6 pin
```




## PWM
Se nombran 4 PWMS; out_pwm0, out_pwm1, out_pwm2 y out_pwm3.



Use the `machine` module and the `{ pwm }` submodule.
```go
import machine { pwm }

out_pwm1_duty(100)       // set the duty cycle for PWM 1
out_pwm2_duty(60)       // set the duty cycle for PWM 2
out_pwm3_duty(40)       // set the duty cycle for PWM 3
```


## UART
```go
import machine { uart }

uart1(115200)

uart1_put(`x`)
y := uart1_get()

uart1_write('Hello...')
msg := uart1_read()
```
## sensores capacitores
Se tienen -- sensores de tipo botón  y -- sensores tipo slider
Estos capsenses estan asociados a los leds 9, 10 y 11.

### `input()` function
The input strings to be captured by the `input()` function having a fixed size of 30 characters.