# Path Tracer Benchmarking

A summarised guide on understanding and using the Path Tracer tool for creating realistic environments. This includes the intention and benefits of the tool, along with how to use it and additional configurations when using the tool.

## Purpose and Benefits
* UE4 provides a companion tool to the Ray Tracer that includes a full Path Tracer. This tool is useful to generate reference images called a **Ground Truth**. The Path Tracer is similar to other offline renderers in how it is used, like [V-Ray](https://www.chaosgroup.com/) and [Arnold](https://www.arnoldrenderer.com/). It works by casting many rays into the scene to gather information about light and color to shade a given pixel. 

* Where ray tracing is great for real-time graphics, path tracing techniques are better for generating an unbiased target result because it's not limited by the number of samples it can use, making it good for comparing against real-time ray tracing features.

* A scene comparison using the Ray-Tracer and Path Tracer is shown below (note that not all materials and lighting effects are fully supported in the comparison):

    ![Ray Traced](https://docs.unrealengine.com/Images/Engine/Rendering/RayTracing/PathTracer/RayTracer.jpg)
    *Image 1: Scene rendered using Ray Tracer*

    ![Path Tracer](https://docs.unrealengine.com/Images/Engine/Rendering/RayTracing/PathTracer/PathTracer.jpg)
    *Image 2: Scene rendered using Path Tracer*

* For artists and programmers, the unbiased nature of the Path Tracer’s ground truth image makes it invaluable to have built right into the engine for comparison. It also removes the need for additional third-party software or plugins to generate these comparison results. For artists, it means being able to fine-tune materials and lighting setups more quickly. For programmers, it improves workflow and iteration times when tuning and validating the look of their real-time algorithms for techniques like Denoising.

## Configuration and Usage
* To make use of the Path Tracer, ensure that ray-tracing has been enabled within the project. Thereafter, **enable** the Path Tracer by selecting the **Path Tracing** option from the **View Modes** dropdown menu as shown below:

    ![Enable Path Tracer](https://docs.unrealengine.com/Images/Engine/Rendering/RayTracing/PathTracer/PathTracerViewMode.jpg)  
    *Image 3: Path Tracing option under View Modes dropdown*

* The Path Tracer uses a progressive accumulation method whereby it's continuously adding samples while the camera is not moving. It also uses adaptive sampling to trace additional rays for the pixels that produce a higher amount of noise, as shown in the image below. The pixels start to fill in with final shading color after a few moments depending on the complexity of the scene and the materials being sampled.

    ![Path Tracer Noise](https://docs.unrealengine.com/Images/Engine/Rendering/RayTracing/PathTracer/PathTracerConvergence.jpg)  
    *Image 4: Visible noise due to adaptive sampling*

* The noise can be mitigated by setting the **Max Bounces**, that rays should travel, and **Samples Per Pixel**, for convergence, settings under the **PathTracing** section of the *Post Process Volume* settings.

## Notes
* Additional properties and adjustable settings can be found under the console variables related to:  
  ```
  r.PathTracing.*
  ```

* The current implementation of the Path Tracer is missing features or workflows that would make it a production-ready replacement for final pixel renders. Instead, it’s current implementation is best suited for comparison reference.

* The Path Tracer enables future research and development to be considered for content creation workflows such as progressive light builds, cinematic rendering, and even for non-rendering applications such as audio simulation in virtual reality (VR), physics collision and hit detection, and artificial intelligence (AI).