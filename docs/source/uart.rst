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

Description
===========

This section provides basic description of the uart core. UART (Universal Asynchronous Receiver/Transmitter) IP Core is designed for use in serial communication, supporting the RS-232. The UART IP Core has many characteristics similar to those of the NS16450 UART.

Block Diagram
--------------
.. figure:: _static/uart_blockdiagram.png
    :name: Uart block diagram
    :width: 100%
    :align: center

     Uart block diagram

Key features
------------
    * Open sourced under Apache-2.0 License (see LICENSE file) - unrestricted commercial use allowed.
    * Full Duplex
    * Independent Tx-Rx Transaction Queue
    * Error Detection: Frame Error, Parity Error
    * Programmable Baud Rate Generator

License
-------

The Riscduino is an open-source design, licensed under the terms of Apache 2.0.

Repository
----------

The complete chip design may be obtained from the git repository located at GitHub `Riscdino database <https://github.com/dineshannayya/riscduino/>`

Process
-------

The Riscduino chip is tagetted to part of efabless MPW Shuttle and in SkyWater 0.13um CMOS technology, with process specifications and data at GitHub `google/skywater-pdk repository <https://github.com/google/skywater-pdk>`_.
