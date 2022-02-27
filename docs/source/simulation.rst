.. raw:: html
   <!---
   # SPDX-FileCopyrightText: 2021 Dinesh Annayya (dinesha@opencores.org)
   #
   # Licensed under the Apache License, Version 2.0 (the "License");
   # you may not use this file except in compliance with the License.
   # You may obtain a copy of the License at
   #
   #      http://www.apache.org/licenses/LICENSE-2.0
   #
   # Unless required by applicable law or agreed to in writing, software
   # distributed under the License is distributed on an "AS IS" BASIS,
   # WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   # See the License for the specific language governing permissions and
   # limitations under the License.
   #
   # SPDX-License-Identifier: Apache-2.0
   -->


Simulation
===========

This section provides basic description of how to simulate the Riscduino SoC.

Basic Usage command :  make verify-<test directory name>

Dut Test case
-------------
Below test-case run faster as it uses only user_project_wrapper and wishbone to control the test case

* make verify-user_basic   
* make verify-user_uart    
* make verify-user_risc_boot
* make verify-user_spi
* make verify-user_i2cm
* make verify-user_uart_master

Core RISC-V Regression
----------------------
Below test is validate the RISC v compliance

* make verify-riscv_regress

  This test has has following sub tests:
     riscv_isa
     riscv_compliance
     isr_sample
     coremark
     dhrystone21
     hello

Caravel+ user_project_wrapper Test case
---------------------------------------
Below Test run take more time as it's full chip run with caravel + user_project_wrapper

* make verify-wb_port
* make verify-risc_boot
* make verify-uart_master

If you want to dump, then you can add DUMP=ON swicth

Test Case Details
-----------------
Below test-case run faster as it uses only user_project_wrapper and wishbone to control the test case

1. user_basic
   AIM: To Validate the Test the different clock selection option for wishbone , risc core, usb and validate device signature

2. user_uart
   AIM: Test to validation uart rx to tx loop back. 
   TEST SEQUENCE: 40 random char are sent from TB to DUT and RISCV core does the hardware loop back,i.e UART-RX to UART-TX

3. uart_risc_boot
   AIM: Test the RISC CORE boot
   TEST SEQUENCE: 
       1. Make sure that core hex file loaded into spi memory
       2. Though wishbone sequence wake-up the core.
       3. core boots from spi
       4. core write 6 Pimux register with some signature
       5. After some delay, testbench validation these signature through wishbone

4. user_spi
    AIM: Test SPI DDR,QUAD,DUAL,SINGLE mode.
    BACKGROUND:  
        SINGLE - This is single pin tx/rx transaction and seperate pin for Tx (spi_sdo[0]) and Rx (spi_sdi[0]) pin, data valid for one spi clock
        DUAL   - This uses two pin for tx/rx transaction, Tx: spi_sdo[1:0] & Rx: spi_sdi[1:0], data valid for one spi clock
        QUAD   - This uses four pins for tx/rx transaction, Tx: spi_sdo[3:0] & Rx : spi_sdi[3:0], Data valid for one spi clock
        DDR    - This uses four pins for tx/rx transaction, Tx: spi_sdo[3:0] & Rx : spi_sdi[3:0], Data valid for half spi clock

    TEST SEQUENCE:
         Test SPI SRAM Memory through Indirect Access
         Test SPI SRAM memory through Direct Access
         TEST SPI FLASH Memory in DDR Mode
         TEST SPI FLASH Memory in QUAD Mode
         TEST SPI FLASH Memory in DUAL Mode
         TEST SPI FLASH Memory in SINGLE Mode
                   
5. user_i2cm
    AIM:  Test the I2C Interface
    TEST SEQUENCE:
          I2C Write and Read access

6. user_uart_master
    AIM: Test the uart master port
    TEST SEQUENCE:
          Configure the uart master baudrate through la_in pins
          From TB uart master send the Write command to wake the device
          Write some general purpose register with uart master and read back and validate

7. riscv_regress
     test is validate the RISC v compliance and this have below sub tests

     riscv_isa
     riscv_compliance
     isr_sample
     coremark
     dhrystone21
     hello

Below Test run take more time as it's full chip run with caravel + user_project_wrapper
1. wb_port
    AIM: Test user_project_wrapper through caravel wishbone interface
    TEST SEQUENCE:
         Boot through caravel riscv core
         Write some general purpose register user project wrapper and read back and validate

2. risc_boot
    AIM: Boot the User RISC core through caravel core
    TEST SEQUENCE:
         Boot through caravel riscv core
         Wake-up the user riscv core
         User risc core write some general porpose register with signtaure
         Read back through caravel riscv core and validate the signature
       
3. uart_master
    AIM: Test the uart master port from caravel core
    TEST SEQUENCE:
          Configure the uart master baudrate through la_in pins using caravel core
          From TB uart master send the Write command to wake the device



