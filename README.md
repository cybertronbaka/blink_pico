# CMake
`CMakeLists.txt` sample has been provided in this repository.

To build a cmake just do the following:
1. Remove `build` folder
2. Create `build` folder
3. `cd build`
4. `cmake ..`
5. `make`

# To Run the code in the pico
1. `cd build`
2. `dmesg | tail` to figure out where the pico USB Mass Storage device sits at
3. `mkdir /mnt/pico/` ( Ignore if already dir already exists)
4. `mount /dev/sdX1 /mnt/pico/` to mount to `/mnt/pico/`
5. `cp blink.uf2 /mnt/pico` to copy the uf2 file into the Pico. Pico should automatically start the work.
6. `umount /mnt/pico/` to safely unmount it.

# To show logs(printf) texts in your console
1. In CMakeLists.txt, add the following: (Enable only 1 at a time. (Only one of [usb, uart] can be `1` at a time)). UART is basically just using `tx rx`:<br/>
```
pico_enable_stdio_usb(${PROJECT_NAME} 1)
pico_enable_stdio_uart(${PROJECT_NAME} 0)
```
2. cmake and make again after clearing build folder ( Need to automate this)
3. Use putty or minicom to communicate with the pico serially.
Note: buadrate is 115200 and usually the Serial Device sits at /dev/ttyACM0

# TODO:
Figure out how to build for debug from terminal.

# Resources:
1. Good Setup guide if you are to use C/C++ [Youtube(Digi-Key)](https://www.youtube.com/watch?v=B5rQSoOmR5w)
2. Setup guid in PDF [Getting-Started](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf)
3. Pinout diagram [diagram](https://datasheets.raspberrypi.com/pico/Pico-R3-A4-Pinout.pdf)
4. Documentation of `pico-sdk` [pico-sdk/doxygen](https://raspberrypi.github.io/pico-sdk-doxygen/)
5. PuTTY setup [instr](https://www.ssh.com/academy/ssh/putty/linux)