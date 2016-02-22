/*
 * File:   timer.c
 * Authors:
 *
 * Created on December 30, 2014, 8:07 PM
 */

#include <xc.h>
#include "timer.h"

#define ON

void delayUs(unsigned int delay){

    //TODO: Create a delay for "delay" micro seconds using timer 2
    TMR2 = 0;
    PR2 = delay*10-1; //need 10 Mhz oscillator for 1 second
    T2CONbits.TON = 1;
    IFS0bits.T2IF = 0;
    while(IFS0bits.T2IF == 0);
    T2CONbits.TON = 0;
    
}

void initTimer2(){
    TMR2 = 0;
    T2CONbits.TCKPS = 0;
    T2CONbits.TCS = 0;
    IFS0bits.T2IF = 0;
}
