# Ray-Traced Reflections

A summarised guide on utilising ray-traced reflections to capture dynamic reflections which are sourced out of the camera view for an accurately simulated environment. As well as performance optimisations including roughness control, distance limiting, number of bounces, samples per pixel, reflection shadows and the reflection denoiser.

## Realistic Reflections
* Ray-traced reflections simulate accurate environment reflections that can support multiple bounces to create inter-reflection for reflective surfaces. 
  
* When compared with Screen Space Reflections (SSR), planar reflections, or even reflection probes, ray-traced reflections captures the entire scene dynamically and is not limited to static captures or objects within the current camera view to be visible in the reflection.
  
* These can be enabled by **ticking** the **Type** box and setting the dropdown to **Ray Tracing** under the **Reflections** settings of the **Post Process Volume** in the *Details pane*.
  
* Due to the reflection simulation not being limited to what is within the camera view, the computational cost is exceptionally high depending on the number of reflections to compute. Key optimisations exist to find a balance between accuracy and performance.

## Optimisations
* 