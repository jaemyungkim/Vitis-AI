Setting up a Versal Accelerator Card
=====================================

The Xilinx |reg| DPUs for VCK5000-PROD card is a High Performance CNN processing engine **DPUCVDX8H**. The detailed combination of VCK5000-PROD card and DPU IP is given in the following table:

=== ================ =====================
No. Accelerator Card DPU IP
=== ================ =====================
1   VCK5000-PROD     DPUCVDX8H_4pe_miscdwc
2   VCK5000-PROD     DPUCVDX8H_6pe_dwc
3   VCK5000-PROD     DPUCVDX8H_6pe_misc
4   VCK5000-PROD     DPUCVDX8H_8pe_normal
=== ================ =====================

You can choose one of them according to your preferences.

VCK5000-PROD Card Setup
--------------------------

Some scripts are provided to automatically finish the VCK5000-PROD card setup process. You could refer to these to understand the required steps.

.. note:: You should use this script in host environment, namely out of the Docker container. After the script is executed successfully, manually reboot the host server once. For cloud DPU, Vitis AI 3.0 applies 2022.2 Tools/Platform/XRT/XRM.

.. code-block::

   source ./install.sh

The command will detect the Operating System you are using, then download and install the appropriate packages.

The following installation steps were performed in this script.

1. Install XRT.
2. Install XRM. The `Xilinx Resource Manager (XRM) <https://github.com/Xilinx/XRM/>`__ manages and controls FPGA resources on a machine. It is used on runtime.
3. Install the VCK5000-PROD Card Target Platform.
4. Install DPU V4E xclbin for VCK5000-PROD.

.. note:: This version requires the use of a VCK5000-PROD card. VCK5000-ES1 card is no longer updated since Vitis AI 2.0. If you want to use it, refer to `Vitis AI 1.4.1 <https://github.com/Xilinx/Vitis-AI/tree/v1.4.1>`__.

Docker Container Environment Variable Setup
----------------------------------------------

Once you have downloaded Vitis AI, entered Vitis AI directory, and then started Docker, in the docker container, execute the following steps.

You can use the following command to set environment variables. The xclbin file must be in the ``/opt/xilinx/overlaybins`` directory. There are four xclbins to choose from depending on the parameters you use.

- For 4PE 350 Hz, you can select DPU IP using the following command:

   .. code-block::
   
      source /workspace/board_setup/vck5000/setup.sh DPUCVDX8H_4pe_miscdwc

- For 6PE 350 Hz with DWC, you can select DPU IP using the following command:

   .. code-block::
   
      source /workspace/board_setup/vck5000/setup.sh DPUCVDX8H_6pe_dwc

- For 6PE 350 Hz with MISC, you can select DPU IP using the following command:

   .. code-block::
   
      source /workspace/board_setup/vck5000/setup.sh DPUCVDX8H_6PE_misc

- For 8PE 350 Hz, you can select DPU IP using the following command:

   .. code-block::
   
      source /workspace/board_setup/vck5000/setup.sh DPUCVDX8H_8pe_normal


.. |trade|  unicode:: U+02122 .. TRADEMARK SIGN
   :ltrim:
.. |reg|    unicode:: U+000AE .. REGISTERED TRADEMARK SIGN
   :ltrim:
