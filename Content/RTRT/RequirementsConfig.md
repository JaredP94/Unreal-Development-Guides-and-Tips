# Requirements and Configuration

A summarised guide on the hardware and software requirements for using ray-tracing within your projects. As well as ue4 configuration to enable the features to be accessed and utilised as expected.

## Hardware Requirements
* A ray-tracing supported GPU is required to make use of the RTRT features in ue4.
* At the current time of writing, these GPUs are only offered by NVIDIA which include the following:
    
    | **Turing Architecture** | **Volta Architecture** | **Pascal Architecture** |
    |-------------------------|------------------------|-------------------------|
    |Titan RTX                |Titan V                 |Titan XP                 |
    |RTX 2080 Ti              |                        |Titan X                  |
    |RTX 2080                 |                        |GTX 1080 Ti              |
    |RTX 2070                 |                        |GTX 1080                 |
    |RTX 2070                 |                        |GTX 1070 Ti              |
    |GTX 1660 Ti              |                        |GTX 1070                 |
    |GTX 1660                 |                        |GTX 1060 (6GB edition)   |
* It should be noted that not all supported GPUs are capable of supporting the full set of RTRT features:
    
    | **RTX Products**        | **Non-RTX Products** |
    |-------------------------|------------------------|
    |High ray count           |Low ray count           |
    |Complex RTRT effects     |Basic RTRT effects      |
    |Multiple RTRT effects    |                        |

## Software Requirements
* A Windows operating system is required as the RTRT features make use of DirectX Raytracing (DXR). Additionally, a minimum build version of 1809 is required.
* Unreal Engine version 4.22 or later is required to access the RTRT features.
* These RTRT features then need to be enabled within the *Project Settings*:
  * Set the **Default RHI** setting to **DirectX 12** in the **Platforms->Windows** section.
  * Enable the **Ray Tracing** setting in the **Engine->Rendering** section.
  * If the **Support Compute Skincache** setting is not enabled, a dialogue will appear prompting confirmation for the setting to be enabled - click **Yes**.
  * Restart ue4 to effect the configured settings.
