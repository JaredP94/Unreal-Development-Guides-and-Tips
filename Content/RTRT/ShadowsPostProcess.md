# Ray-Traced Shadows and Post Process Volume

A summarised guide on creating ray-traced shadows and how to tweak their softness for realistic content. As well as the use of the post process volume and the respective ray tracing and path tracing features it can offer and control.

## Ray-Traced Shadows
* These simulate soft area lighting effects for objects in the environment. This means that based on the light’s source size or source angle, an object’s shadow will have sharper shadows near the contact surface than farther away where it softens and widens.

* Shadows can be cast by any light source. This is activated by **Enabling** the **Cast Raytraced Shadow** property under the **Light** section in the *Details pane*. Each type of light source then needs to be configured in the following ways:
  * **Directional Light**: modify the **Source Angle** property.
  * **Point** and **Spot Lights**: modify the **Source Radius** property.
  * **Rect Light**: modify the **Barn Door Angle** and **Barn Door Length** to shape and soften the shadow softness.

* Each configured property will control the softness observed in cast shadows. A higher value translates to a softer shadow.

## Post Process Volume
* This is used in the scene to control ray tracing and path tracing features and properties. Volumes can be added to different areas for interiors and exteriors to facilitate the customisable features and desired quality level. They allow the control of **Ray Traced Reflections**, **Translucency**, **Global Illumination**, **Ambient Occlusion**, and the **Path Tracer**.

* The image below highlights all the available ray tracing and path tracing properties which can be customised within the volume:

  ![Post Process Volume Settings](https://docs.unrealengine.com/Images/Engine/Rendering/RayTracing/PPV_Settings.jpg)

* The post process volume can be placed into the scene by dragging it in from the *Modes pane*.

* In order to have the ray traced properties affect the entire scene, **enable** the **Infinite Extent (Unbound)** property under the **Post Process Volume Settings** section in the *Details pane*.