#include<reg51.h>
sbit rs=P3^0;
sbit rw=P3^1;
sbit en=P3^2;
void lcdcmd(unsigned char);
void lcddata(unsigned char);
void delay();
void main()
{
P2=0x00;
while(1)
{
//command passing
lcdcmd(0x38);
delay();
lcdcmd(0x80);
delay();
//data displaying
lcddata('L');
delay();
lcddata('U');
delay();
lcddata('B');
delay();    
lcddata('N');
delay();
lcddata('A');
delay();
}
}
void lcdcmd(unsigned char val)
{
P2=val;
rs=0;
rw=0;
en=1;
delay();
en=0;
}
void lcddata(unsigned char val)
{
P2=val;
rs=1;
rw=0;
en=1;
delay();
en=0;
}
void delay()
{
unsigned int i;
for(i=0;i<5000;i++);
}
