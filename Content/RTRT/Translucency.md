# Ray-Traced Translucency

A summarised guide on utilising ray-traced translucency to accurately represent the physical handling of light and reflections on transparent materials. As well as performance optimisations including roughness control, refraction ray limiting, samples per pixel, reflection shadows and refraction control.

## Realistic Translucency
* Ray-traced translucency provides a physically realistic representation of reflection, absorption, and refraction properties for transparent surfaces within a scene. These differences are easily noted in the comparison below:
  
    ![Raster Translucency](https://docs.unrealengine.com/Images/Engine/Rendering/RayTracing/RT_Translucency_Disabled.jpg)
    *Image 1: Scene rendered with Raster Translucency*

    ![Ray-Traced Translucency](https://docs.unrealengine.com/Images/Engine/Rendering/RayTracing/RT_Translucency_Enabled.jpg)
    *Image 2: Scene rendered with Ray-Traced Translucency*

* This can be enabled by **ticking** the **Type** box and setting the dropdown to **Ray Tracing** under the **Translucency** settings of the **Post Process Volume** in the *Details pane*.
  
* The performance trade-off is less than that of ray-traced reflections but it is still important to manage the performance cost. Key optimisations exist to find a balance between accuracy and performance.

## Index of Refraction
* With ray-traced translucency, Index of Refraction (IOR) is controlled with the Material's **Specular** value clamped between **0** and **1**. This is how IOR is determined with a real-world material as well. An example of variable IOR is shown below:

    ![IOR Specular 0.0](https://docs.unrealengine.com/Images/Engine/Rendering/RayTracing/RT_Refraction_0.jpg)
    *Image 3: Scene rendered with IOR Specular value of 0.0*

    ![IOR SPecular 0.5](https://docs.unrealengine.com/Images/Engine/Rendering/RayTracing/RT_Refraction_1.jpg)
    *Image 4: Scene rendered with IOR Specular value of 0.5*

* Within the *Post Process Volume* **Translucency** and **Ray Tracing Translucency** sections, use the following guidelines to control IOR with a ray-traced translucent material:
  
  * **Enable** the **Type** box and select the **Ray Tracing** dropdown option.
  
  * **Enable** the **Refraction** option.

  *  Set the **Max Refraction Rays** to a high enough bumber of bounces to see the other side of the material. For example, a single bounce would not be enough to see objects behind it, but several bounces may be.

## Optimisation
* There are a multitude of settings which help balance the quality versus performance of ray-traced translucency. The exact value of each setting will depend on the requirements and components of your scene. These settings are found under the **Ray Tracing Translucency** section of the **Post Process Volume** in the *Details pane*:

  * **Max Roughness**: Sets the maximum roughness value that ray-traced translucency will be visible before falling back to raster methods which are less expensive. Translucency contribution is smoothly faded when close to the roughness threshold and this parameter behaves similarly to SSR’s **Max Roughness** setting. Lower values fall back to other methods more quickly.

  * **Max Refraction Rays**: Sets the maximum number of refraction rays that ray-traced translucency uses. Additional samples decrease performance while increasing quality and accuracy. Set to **3** refraction rays by default.

  * **Samples Per Pixel**: Sets the number of samples to use per pixel for ray-traced translucency. Additional samples decrease performance while increasing quality and accuracy. Set to **1** sample per pixel by default.

  * **Shadows**: Sets how shadows should be reflected. Choose between:

    * **Hard Shadows** which has no soft shadows

    * **Area Shadows** to have soft shadowing like ray-traced shadows

    * **Disable** to disable shadowing in ray-traced translucency
  
  * **Refraction**: Sets whether refraction should be enabled or not for ray-traced translucency. If disabled, rays will not scatter and only travel in the same direction as before the intersection event.