.. include:: ../../../substitutions.rst

.. _sln_voice_low_power_ffd_deploying_linux_mac:

******************************************
Deploying the Firmware with Linux or macOS
******************************************

This document explains how to deploy the software using `CMake` and `Make`.

Building the Host Applications
==============================

This application requires a host application to create the flash data partition. Run the following
commands in the root folder to build the host application using your native toolchain:

.. note::

  Permissions may be required to install the host applications.

.. code-block:: console

  cmake -B build_host
  cd build_host
  make install

The host applications will be installed at ``/opt/xmos/bin``, and may be moved if desired. You may
wish to add this directory to your ``PATH`` variable.

Building the Firmware
=====================

Run the following commands in the root folder to build the firmware:

.. code-block:: console

    cmake -B build -DCMAKE_TOOLCHAIN_FILE=xmos_cmake_toolchain/xs3a.cmake
    cd build
    make example_low_power_ffd

Running the Firmware
====================

Before running the firmware, the filesystem and `command` model must be flashed to the data partition.

Within the root of the build folder, run:

.. code-block:: console

    make flash_app_example_low_power_ffd

After this command completes, the application will be running.

After flashing the data partition, the application can be run without reflashing. If changes are
made to the data partition components, the application must be reflashed.

From the build folder run:

.. code-block:: console

    make run_example_low_power_ffd

Debugging the Firmware
======================

To debug with xgdb, from the build folder run:

.. code-block:: console

    make debug_example_low_power_ffd

|newpage|
