# Ray-Traced Ambient Occlusion

A summarised guide on utilising ray-traced ambient occlusion to accurately represent the physical handling of light in areas without direct exposure. As well as performance optimisations including intensity control, radius limiting and samples per pixel.

## Realistic Reflections
* Ray-traced ambient occlusion (RTAO) accurately shadows areas blocking ambient lighting better grounding objects in the environment, such as shadowing the corners and edges where walls meet or adding depth to the crevices and wrinkles in skin.

* When compared with Screen Space Ambient Occlusion (SSAO), RTAO grounds objects and adds depth to the scene to produce natural looking shadowing in indirectly lit areas. These differences are easily noted in the comparison below:
  
    ![Screen Space Ambient Occlusion](https://docs.unrealengine.com/Images/Engine/Rendering/RayTracing/RT_AO_Disabled.jpg)
    *Image 1: Scene rendered with Screen Space Ambient Occlusion*

    ![Ray-Traced Ambient Occlusion](https://docs.unrealengine.com/Images/Engine/Rendering/RayTracing/RT_AO_Enabled.jpg)
    *Image 2: Scene rendered with Ray-Traced Ambient Occlusion*

* RTAO can be enabled by **ticking** the **Samples Per Pixel** box and setting the value to **greater than 0** under the **Ray Tracing Ambient Occlusion** settings of the **Post Process Volume** in the *Details pane*.
  
* Key optimisations exist to find a balance between accuracy and performance.

## Optimisation
* There are a multitude of settings which help balance the quality versus performance of RTAO. The exact value of each setting will depend on the requirements and components of your scene. These settings are found under the **Ambient Occlusion** and **Ray Tracing Ambient Occlusion** sections of the **Post Process Volume** in the *Details pane*:

  * **Intensity**: Defines how much ambient occlusion affects non-direct lighting for RTAO. Lower values decrease the effect while higher values increase how strong the effect is.

  * **Radius**: Controls the distance in Unreal Units that ambient occlusion affects.

  * **Samples Per Pixel**: Sets the number of samples to use per pixel for RTAO. Additional samples decrease performance while increasing quality and accuracy. Set to **1** sample per pixel by default.