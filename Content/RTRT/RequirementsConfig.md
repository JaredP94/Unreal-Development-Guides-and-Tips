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

## Engine Changelog
* This section summarises any general ray-tracing improvements/modifications as new engine versions are made available.
  
* **UE 4.22**: 
  
  **Added ray tracing low level support.**
  * Implemented a low level layer on top of UE DirectX 12 that provides support for DXR and allows creating and using ray tracing shaders (ray generation shaders, hit shaders, etc) to add ray tracing effects.
  
  **Added high level ray tracing features.**
  * Rect area lights
  
  * Soft shadows
  
  * Reflections
  
  * Reflected shadows
  
  * Ambient occlusion
  
  * RTGI (ray traced global illumination)
  
  * Translucency
  
  * Clearcoat
  
  * IBL
  
  * Sky
  
  * Geometry types
  
  * Texture LOD
  
  * Denoiser
  
  * Path tracer

* **UE 4.23**:
  
  Ray Tracing support has received many optimizations and stability improvements in addition to several important new features, including performance and stability enhancements, additional geometry and material support, and multi-bounce reflection fallback.

* **UE 4.24**:
  
  Stability and performance improvements, including support for static meshes that use vertex animation.