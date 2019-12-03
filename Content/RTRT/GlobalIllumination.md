# Ray-Traced Global Illumination

A summarised guide on utilising ray-traced global illumination to add real-time light interaction within the scene. As well as performance optimisations including max bounce control and samples per pixel.

## Real-time interaction
* Ray-traced global illumination (RTGI) facililates real-time interactive bounce lighting to areas not directly lit by a given light source. This provides real-time shadow casting and dynamic material interaction for a truly realistic scene.

* When compared with a Sky Light, RTGI prevents the harshly contrasted light within scenes and facilitates a truly dynamic lighting system. These differences are easily noted in the comparison below:
  
    ![Sky Light Only](https://docs.unrealengine.com/Images/Engine/Rendering/RayTracing/RT_GI_Disabled.jpg)
    *Image 1: Scene rendered with Sky Light only*

    ![Ray-Traced Global Illumination](https://docs.unrealengine.com/Images/Engine/Rendering/RayTracing/RT_GI_Enabled.jpg)
    *Image 2: Scene rendered with Ray-Traced Global Illumination*

* RTGI can be enabled by **ticking** the **Enabled** under the **Ray Tracing Global Illumination** settings of the **Post Process Volume** in the *Details pane*.
  
* Key optimisations exist to find a balance between accuracy and performance as RTGI is extremely expensive as the number of bounces increase within a scene.

## Optimisation
* There are a multitude of settings which help balance the quality versus performance of RTGI. The exact value of each setting will depend on the requirements and components of your scene. These settings are found under the **Ray Tracing Global Illumination** section of the **Post Process Volume** in the *Details pane*:

  * **Max Bounces**: Sets the maximum number of bounces of light that will be used by RTGI. Increased number of bounces translates to a more realistic scene but yield becomes exponentially more expensive. Set to **1** bounce by default.

  * **Samples Per Pixel**: Sets the number of samples to use per pixel for RTGI. Additional samples decrease performance while increasing quality and accuracy. Set to **1** sample per pixel by default.