# Ray-Traced Reflections

A summarised guide on utilising ray-traced reflections to capture dynamic reflections which are sourced out of the camera view for an accurately simulated environment. Performance optimisations will be presented which includes roughness control, distance limiting, number of bounces, samples per pixel, and shadow control.

## Realistic Reflections
* Ray-traced reflections simulate accurate environment reflections that can support multiple bounces to create inter-reflection for reflective surfaces. 
  
* When compared with Screen Space Reflections (SSR), planar reflections, or even reflection probes, ray-traced reflections captures the entire scene dynamically and is not limited to static captures or objects within the current camera view to be visible in the reflection. These differences are easily noted in the comparison below:

    ![Screen Space Reflections](https://docs.unrealengine.com/Images/Engine/Rendering/RayTracing/RT_Reflections_Disabled.jpg)
    *Image 1: Scene rendered with Screen Space Reflections*

    ![Ray-Traced Reflections](https://docs.unrealengine.com/Images/Engine/Rendering/RayTracing/RT_Reflections_Enabled-1.jpg)
    *Image 2: Scene rendered with Ray-Traced Reflections*
  
* These can be enabled by **ticking** the **Type** box and setting the dropdown to **Ray Tracing** under the **Reflections** settings of the **Post Process Volume** in the *Details pane*.
  
* Due to the reflection simulation not being limited to what is within the camera view, the computational cost is exceptionally high depending on the number of reflections to compute. Key optimisations exist to find a balance between accuracy and performance.

## Optimisation
* There are a multitude of settings which help balance the quality versus performance of ray-traced reflections. The exact value of each setting will depend on the requirements and components of your scene. These settings are found under the **Ray Tracing Reflections** section of the **Post Process Volume** in the *Details pane*:

  * **Max Roughness**: Sets the maximum roughness value that Ray Traced Reflections will be visible before falling back to raster methods that are less expensive. Reflection contribution is smoothly faded when close to the roughness threshold and this parameter behaves similarly to SSR’s **Max Roughness** setting. Lower values fall back to other methods more quickly. Scene roughness can be viewed by selecting the **Roughness** option under the **Buffer Visualization** settings of the editor *View Mode*.

  * **Max Bounces**: Sets the maximum number of bounces that Ray Traced Reflections uses. More bounces create inter-reflection but comes at a higher cost. Set to **1** bounce by default.

  * **Samples Per Pixel**: Sets the number of samples to use per pixel for Ray Traced Reflections. Additional samples decrease performance while increasing quality and accuracy. Set to **1** sample per pixel by default.

  * **Shadows**: Sets how shadows should be reflected. Choose between:

    * **Hard Shadows** which has no soft shadows

    * **Area Shadows** to have soft shadowing like Ray Traced shadows

    * **Disable** to disable shadowing in Ray Traced Reflections