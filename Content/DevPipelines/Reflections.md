# Reflections

A summarised guide on extracting the best performance from reflections. This includes understanding and making use of reflection actor types, screen space, sphere, box and planar reflections, and yielding higher quality reflections.

## Screen Space Reflections (SSR)
   * These are much more efficient than Planar Reflections when it comes to rendering, but are also much less reliable:
     * Sphere Reflection Capture **[cheap]**
     * Box Reflection Capture **[moderate]**
   * Each reflection is controlled by the particular actor which is placed into the scene.
   * The intended reflection can be applied by simply dragging the type of reflection actor into the scene.
   * Within the **Reflection Capture** section of the *Details pane*:
     * The **Influence Radius** setting is responsible for controlling the area of the reflection.
     * Selecting the **Update Captures** button will update the cubemap of the reflection.
     * The **Reflection Source Type** option determines whether the reflection is based on its surroundings (**Captured Scene**) or using a cubemap from a different scene (**Captured Scene**).
   * Sphere reflection capture is best used with encapsulating groups whereby a single sphere will encapsulate the entire area where reflections are required and subsequent smaller spheres are placed in areas of interest. Use enough to get the desired effect, but don't overuse as this will eventually ruin the scene and become expensive. 
   * Box reflection capture is best suited for areas such as corridors as they can produce artefacts.
   * The **reflections view mode** is helpful in determining the correct layout of reflection capture actors.

## Planar Reflections
  * These can give more accurate looking reflections than screen space reflections provide but come with a higher rendering cost. This is due to planar reflections actually rendering the level again from the direction of the reflection. The cost is thus proportional to the rendering cost of the scene which requires the reflections.
  * These need to be enabled within the *Project Settings* by selecting the **Support global clip plane for Planar Reflections** setting within the **Rendering** section and restarting the editor.
  * Within the **Planar Reflection** section of the *Details pane*:
    * Enabling the **Render Scene Two-Sided** setting will reduce any noted artefacts at reflection edges. Note: ensure that the water plane is added to the **Hidden Actors** as it will not block the reflection.

## Improving SSR
  * Although SSRs are more efficient, they do not cater for dynamic objects within the scene. This can be catered for with SSR post process effects.
  * These include three Settings:
    * Intensity - enable/fade/disable the SSR feature by percentage (avoid numbers between 0 and 1 for consistency).
    * Quality - [0=lowest quality] while [100=maximum quality] (50 is the default to provide better performance).
    * Max Roughness - used to determine what roughness is to be used for fading the SSR (0.8 works well, smaller can run faster).
  * Ensure the dynamic object is always contained within the SSR container.

## Higher Quality Reflections
  * There are a few options available to increase the quality of scene reflections.
  * Due to being a real-time engine, reflection capture resolution is generally reduced. This can be increased by increasing the **Reflection Capture Resolution** setting under the **Rendering** section in *Project Settings*.
  * Within the scene skylight settings, increase the **Cubemap Resolution** settings in the *Details pane*.
  * Within the static mesh editor, enable the **Use High Precision Tangent Basis** under the **LOD** section in the *Details pane* for higher accuracy normals on the meshes.
  * Improved mesh rendering interpolation can be obtained by setting the **GBuffer Format** setting in the **Rendering** section in *Project Settings* to **High Precision Normals**.
  * Furthermore, higher mesh tessellation will translate to improved rendering interpolation of the reflected meshes.