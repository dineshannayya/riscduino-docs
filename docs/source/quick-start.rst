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

User project quick start guide
==============================

This section describes how to simulate and .gds generarion with the `Riscduino repository <https://github.com/dineshannayya/riscduino>`_ 

Prerequisites
-------------

* Docker

If you have followed the Getting Started Guide you should have all of these installed. To proceed make sure, that your environment variables are set correctly:

.. code-block:: bash

   git clone https://github.com/efabless/caravel-lite.git
   cd caravel-lite
   make install_mcw

.. code-block:: bash

   export OPENLANE_IMAGE_NAME=riscduino/openlane:<Check the mpw version on project mpw4/mpw5/latest>
   export OPENLANE_TAG=<Check the mpw version on project mpw4/mpw5/latest>
   export CARAVEL_ROOT=<Set the caravel lite root>
   export MCW_ROOT=$CARAVEL_ROOT/mgmt_core_wrapper



Building individual design
--------------------

To build your design go into ``openlane`` and run make with your design name as a target:

.. code-block:: bash

   cd openlane
   make <design>

This will run your design throught the OpenLANE workflow and if successfull produce a ``.gds`` file of your project. The subdirectory ``runs/<design>`` will be created in your designs folder, which contains the results of the run. The following result files in ``runs/<design>/`` are important:

* ``<design>/runs/<design>/reports/final_summary_report.csv``: Contains the results of the run including violations
* ``<design>/runs/<design>/results/magic/<design>.lef``
* ``<design>/runs/<design>/results/magic/<design>.gds``

The ``.gds`` and ``.lef`` files can also be found in the ``gds`` and ``lef`` directories on the top level of the repository.


