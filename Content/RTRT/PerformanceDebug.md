# Performance Analysis and Debugging

A summarised guide on using performance analysis and debugging tools within RTRT environments. These include GPU statistics, ray-tracing resource usage, ray-tracing debug view modes, evaluating denoiser quality and on-the-go ray-tracing management.

## GPU Profiling
* The live GPU profiler provides real-time per-frame stats for the major rendering categories. To use the live GPU profiler, press the **Backtick key** to open the console and then input the following command:
  
  ```
  stat GPU
  ```

  The live GPU profiler can also be accessed from **Stat sub-menu** in the **Viewport Options** dropdown. Ray-tracing features will appear within the profiler as shown below:
  
  ![GPU Profiler](https://docs.unrealengine.com/Images/Engine/Rendering/RayTracing/GPUStats1.jpg)
  *Image 1: GPU Profiler containing Ray-Tracing features*

## Ray-Tracing Resource Profiling
* The Ray-Tracing resource usage profiler shows relevant statistics. To use the Ray-Tracing resource profiler, press the **Backtick key** to open the console and then input the following command:
  
  ```
  Stat D3D12RayTracing
  ```

  Ray-Tracing resource consumption statistics will appear within the profiler as shown below:
  
  ![Ray-Tracing Profiler](https://docs.unrealengine.com/Images/Engine/Rendering/RayTracing/StatD3D12RayTracing.jpg)
  *Image 2: Ray-Tracing resource profiler showing relevant statistics*

## Debug View Modes
* A number of ray-tracing debug view modes can be found in the **Ray Tracing Debug** option under the **View Mode** dropdown. This location and list of debug modes is shown below:

  ![Ray-Tracing Debug View Modes](https://docs.unrealengine.com/Images/Engine/Rendering/RayTracing/RT_DebugOptions.png)
  *Image 3: Ray-Tracing Debug View Modes*

## Denoiser Quality Evaluation
* Quality evaluation of the denoiser for various ray-tracing effects can be performed in the following ways:

  * Disable **Temporal Anti-Aliasing** and **Depth of Field**: Both of these are running in linear color space in Unreal Engine's renderer. They do some HDR color weighting tricks to avoid aliasing between shadows and highlights.

  * Compare the **Denoised single sample per pixel** with an **Undenoised single sample per pixel**: The result will look incorrect due to the energy difference and that the denoiser is darkening the shadows too much. However, a single sample per pixel will look brighter due to the tonemapper's non-linear operation. For a better comparison, the **Denoised single sample per pixel** should be tested against an **Undenoised multiple samples per pixel**. An example of the comparison is shown below:

    ![Denoised Single Sample Per Pixel](https://docs.unrealengine.com/Images/Engine/Rendering/RayTracing/RT_Denoiser_SingleSample.jpg)
    *Image 4: Rendered scene with Denoised Single Sample per Pixel*

    ![Undenoised Multiple Samples per Pixel](https://docs.unrealengine.com/Images/Engine/Rendering/RayTracing/RT_Denoiser_MultiSamples.jpg)
    *Image 5: Rendered scene with Undenoised Multiple Samples per Pixel*

    The denoised single sample per pixel will not be perfect due to information loss. However, when compared to undenoised multiple samples per pixel, the results are consistent. Also, keep in mind that the Denoiser supports up to **four samples per pixel**, which improves the quality and more closely matches the undenoised multiple samples per pixel result.

## Ray-Tracing Management
* All ray-tracing effects can be enabled and disabled on the go through the use of console commands. Press the **Backtick key** to open the console and then input the following command:
  
    ```
    r.raytracing.ForceAllRayTracingEffects [DesiredState]
    ```

    where a **DesiredState** value of **0** and **1** will disable and enable all ray-tracing effects respectively.

## Material Management
* Complex Materials can affect performance of ray-tracing features. To test performance impact, press the **Backtick key** to open the console and then input the following command:
  
    ```
    r.RayTracing.EnableMaterials
    ```

* Use the **Cast Ray Traced Shadows** checkbox to set whether this material casts ray-traced shadows. This is useful for controlling specific elements of your materials assigned to geometry that should or should not cast a ray-traced shadow.

* Use the **Ray Tracing Quality Switch Replace Node** to replace entire parts of your material logic to lower the cost of features like RTGI, RT Reflections, and RT Translucency with less complex logic. This is a global change that affects all ray-tracing effects. 
  
    Below is an example where the **Normal** logic path renders as seen in the scene. The **Ray Tracing** path uses less complex logic for effects in Ray-Tracing, such as RTGI and Reflections where textures, normals, and roughness can be come an expensive added cost.

    ![Ray Tracing Quality Switch Replace Node Example](https://docs.unrealengine.com/Images/Engine/Rendering/RayTracing/RT_MaterialQualitySwitch.png)
    *Image 6: Ray Tracing Quality Switch Replace Node Example*

## Geometry Considerations
* Geometry with small holes or lots of little details can impact performance, such as foliage and fences. 

* Indoor environments are slower to render than outdoors ones. For example, when light enters from outside, areas that are directly lit is faster than points that are indirectly lit. Also, you have to consider that more ray-tracing features are being used, such as reflections and translucency