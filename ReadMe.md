This project is from the "Baremetal" section of the Fastbit Embedded Brain 
Academy course found on Udemy and youtube.

This implementation uses a different board than the course.
Board Used: STM32F411VE Discovery board.

Mostly, this means the stm32_startup.c file is different, because the vector 
table for the F411 is different.

To run this you'll need
Make
OpenOCD
GNU Project Debugger (GDB)

The steps to run this are as follows. 
1. plug in board
2. Open terminal to folder containing the files
3. write to the terminal
```
    make
    make load
```    
4. open another terminal
5. write to the new terminal
```
    arm-none-eabi-gdb.exe
    target remote localhost:3333
    monitor reset init
    monitor flash write_image erase final.elf
```
6. Now you can choose to run any of the following
```
    monitor reset
    monitor reset halt
```
7. You can resume or halt the board by using
```
    monitor resume
    monitor halt
```

The writer.ccp is just a script I used to generate a lot of the stm32_startup.c
file.


I use bear to create compile_commands.json. I use this with my nvim setup. call this from top folder
'''
bear -- make
'''

Notes
I had to switch to using my own target cfg file because the one MX provided wasn't working.


