As far as I know, The Microprocessor running Linux OS will boot up in the below order.

Primary Bootloader(BootROM code)  -> Secondary Bootloader(UEFI/u-boot) -> Linux Kernel -> User Login

How does the primary bootloader initialize, execute and hand over control to the secondary bootloader?

My Answer:
After thinking it over for a bit, I answered. 

Once the Processor is powered on, It will start its tasks in the below order.

1. POR(Power On Reset)
First, The processor will start resetting itself. Resetting the registers, flags and memory. This is done to make sure the device is in a known state. Mostly, The known state means typically zero. During this POR, The Program Counter will change its address to Reset vector. This Reset vector is nothing but the starting address of the BootROM code. This BootROM code is stored in a non-volatile storage.

2. Initial Setup
As soon as the POR completes, The processor starts to execute the BootROM code sequentially. Here is where the Primary Bootloader comes into action. The Boot ROM initially setup the following things.
-> Configuring the clock settings
-> Setting up basic memory mapping
-> Initializing basic system peripherals

3. Self-Testing
After the Initial setup, The Processor will self-test itself. The self-test includes checking of Registers, Flags, Memory and peripherals. These tests change from one chip manufacturer to another.

4. Identify Boot Source
Then the Processor will start to search for the source where the Secondary Bootloader is stored(Flash devices like SD card, NAND Flashes or  network interfaces). This identification has a sequence and priority for each. For example, It will be like below.
NAND(First) -> SD card(Second) -> Network interface(Third).
These sequences and priority can be varied using some hardware techniques(like switches and shorting the dedicated pins).

5. Load Secondary Bootloader
Once it identifies the source, Primary Bootloader will start to copy Secondary Bootloader from source to RAM. 

6. Transfer Control
After the secondary Bootloader is loaded into memory, The Primary Bootloader will hand over the control to Secondary Bootloader. This will be done by executing an assembly language Instruction. When this assembly language Instruction is executed, The Program Counter will be set to the starting address of secondary bootloader code in RAM.

7. Secondary Bootloader Execution
Now, Secondary Bootloader will take over the control. Then, It will perform the following tasks.
-> Performing further hardware initialization
-> Loading the operating system
-> Starting the OS by jumping to its entry point

In this way, BootROM initializes the microprocessor, identifies a boot source, loads the secondary bootloader, and then transfers control to it. This process ensures a smooth transition from the initial power-on state to executing user applications like setting the stage for proper operation.


https://www.synacktiv.com/en/publications/i-hack-u-boot
Summary:
The article guides firmware extraction from U-Boot devices via serial, SD card, USB, and TFTP.
It covers file system operations, including backdoor insertion and sensitive file extraction.
Depthcharge toolkit aids security research and jailbreaking of U-Boot-based platforms.
The article discusses the I2C protocol for chip communication and U-Boot shell unlocking.
Tips are provided for bypassing U-Boot protections, including bootargs modification and console changes.
Autoboot control is explained using bootdelay, bootstopkey, and bootstopkeysha256 options.

Note: The reference links, available at the end of the article, provides further reading.
             It is a very long article, kindly bookmark it and explore at your own pace.

