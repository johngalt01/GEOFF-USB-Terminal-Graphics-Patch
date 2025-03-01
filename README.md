# GEOFF-USB-Terminal-Graphics-Patch
This is a Patch for the GEOFF USB terminal to allow erasing of elements without having to clear the screen completely.
This is a Graphics Patch for the Geoff USB Terminal.

the loading screen will display the modifed message:

"Graphics Patch 2022 John Galt"

This indicates additional Graphics Escape codes as shown below.

the original code of the Geoff as altered here :

// draw graphics

void cmd_Draw(void) {

//    if(Display24Lines) {

//        arg[2] = (arg[2]/3)*2;

//        arg[4] = (arg[4]/3)*2;

//    }

    if(arg[0] == 1) DrawLine(arg[1], arg[2], arg[3], arg[4], 1);
    
    if(arg[0] == 2) DrawBox(arg[1], arg[2], arg[3], arg[4], 0, 1);
    
    if(arg[0] == 3) DrawBox(arg[1], arg[2], arg[3], arg[4], 1, 1);
    
    if(arg[0] == 4) DrawCircle(arg[1], arg[2], arg[3], 0, 1, vga ? 1.14 : 1.0);
    
    if(arg[0] == 5) DrawCircle(arg[1], arg[2], arg[3], 1, 1, vga ? 1.14 : 1.0);
    
    if(arg[0] == 6) DrawLine(arg[1], arg[2], arg[3], arg[4], 0);
    
    if(arg[0] == 7) DrawBox(arg[1], arg[2], arg[3], arg[4], 0, 0);
    
    if(arg[0] == 8) DrawBox(arg[1], arg[2], arg[3], arg[4], 1, 0);
    
    if(arg[0] == 9) DrawCircle(arg[1], arg[2], arg[3], 0, 0, vga ? 1.14 : 1.0);
    
    if(arg[0] == 10) DrawCircle(arg[1], arg[2], arg[3], 1, 0, vga ? 1.14 : 1.0);
    
    if(arg[0] == 11) plot(arg[1], arg[2], 1);
    
    if(arg[0] == 12) plot(arg[1], arg[2], 0);
    
}


This patch allows you to ERASE elements on the screen without having to clear the screen.
the original GEOFF terminal graphics could only draw to the screen not delete.


The basic original escape codes are:

Draw a line ESC [Z1;<x1>;<y1>;<x2>;<y2>Z

Draw a box ESC [Z2;<x1>;<y1>;<x2>;<y2>Z

Draw a filled box ESC [Z3;<x1>;<y1>;<x2>;<y2>Z

Draw a circle ESC [Z4;<x1>;<y1>;<r>Z

Draw a filled circle ESC [Z5;<x1>;<y1>;<r>Z

Extended escape codes to erase the above: (Graphics Patch 2022 John Galt)

Erase a line ESC [Z6;<x1>;<y1>;<x2>;<y2>Z

Erase a box ESC [Z7;<x1>;<y1>;<x2>;<y2>Z

Erase a filled box ESC [Z8;<x1>;<y1>;<x2>;<y2>Z

Erase a circle ESC [Z9;<x1>;<y1>;<r>Z

Erase a filled circle ESC [Z10;<x1>;<y1>;<r>Z

Additional added escape code: (Graphics Patch 2022 John Galt) 

Draw a Pixel ESC [Z11;<x1>;<y1>Z

Erase a Pixel ESC [Z12;<x1>;<y1>Z

originally you could do the same as drawing a one pixel line and deleteing a one pixel line
but it was felt to add a escape code just for one pixel draw and erase.
