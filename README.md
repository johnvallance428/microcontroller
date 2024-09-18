The code below is responsible for controlling the LED blinking functionality. Initially, there was an issue with line 7, where the original code referenced button2 bit2. This would correspond to pin p2.2 on the board. However, after testing, it was determined that P2.2 does not correspond to the correct pin needed to trigger the desired behavior. Specifically, it does not control the correct LED. To resolve this, we had to modify the code and change the reference from bit2  to bit3. This adjustment ensured that the pin used is P2.3, which correctly corresponds to the green LED. Now, when the button is pressed, the correct pin is triggered, and the green LED blinks as intended. This modification was crucial for ensuring that the hardware functions as expected and responds accurately to the button press.

include <msp430.h>
#define RED_LED BIT0 //P1.0
#define GREEN_LED BIT6 //P6.6
#define BUTTON1 BIT1 //push button P4.1
#define BUTTON2 BIT3 //push button P2.3



void main(void)
{
WDTCTL = WDTPW | WDTHOLD;
P1OUT &= ~BIT0;  //p1.0 red led
P6OUT &= ~BIT6; //p6.6 greenled
P1DIR |= BIT0;
P6DIR |= BIT6;


P4DIR &= ~BIT1;//clear P4.1(s1)
P4REN |= BIT1;//Enable pull up/down resistor
P4OUT |= BIT1;//Make resistor a pull up

P2DIR &= ~BIT3;//clear P2.3(s2)
P2REN |= BIT3;//Enable pull up/down resistor
P2OUT |= BIT3;//Make resistor a pull up



PM5CTL0 &= ~LOCKLPM5;                   // Disable the GPIO power-on default high-impedance mode
                                           // to activate previously configured port settings
int count = 0;
while(1){
        if((P4IN & BUTTON1) == 0x00){
        _delay_cycles(5000);
        if((P4IN & BUTTON1) == 0x00){
            P1OUT ^= RED_LED;
            } while((P4IN & BUTTON1) == 0x00);
        }

        else if((P2IN & BUTTON2) == 0x00){
         _delay_cycles(5000);
        if((P2IN & BUTTON2) == 0x00){
            P6OUT |= GREEN_LED;
            }
        while((P2IN & BUTTON2) == 0x00);}

*/
}
//return 0;
}





#include <msp430.h> 

void main(void)
{
	WDTCTL = WDTPW | WDTHOLD;	// stop watchdog timer
	
	int a  = 32;
	int b;
	unsigned int c = 0xFFFF;
	unsigned char d = 0x00;
	int e = 10;
	float f = 10.1;
	int g = 0;
	float h = 0.0;

	a += 1;
	b = 17/2;

	while(1);
	
}
