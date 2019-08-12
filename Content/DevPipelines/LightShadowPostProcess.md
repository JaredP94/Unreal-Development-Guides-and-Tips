### Lighting, Shadowing, and Post Processing

A summarised guide on how these components can dramatically affect performance, along with where to look to control their impact on your scene. These components generally overlap with each other and more often than not are responsible for the most performance degradation as their over-use is very appealing.

1. **Lighting**
   * It is important to be knowledgeable about the different light types in ue4 and what each type does. Furthermore, it is useful to understand the process of building lighting.
   * There are three lighting mobility types within ue4:
     * **Static** - no properties can be changed at runtime **[cheap]**.
     * **Stationary** - can change its colour and brightness at runtime but cannot move, rotate or change influence size **[moderate]**.
     * **Movable** - capable of changing all properties at runtime **[expensive]**.
   * The mobility type of a light can be set within the **Mobility** setting under the **Transform** section of the light in the *Details pane*.
   * When building scene lighting, ue4 offers four quality modes:
     * **Preview** - gets the point across, but is at least fast **[preview]**.
     * **Medium** - looks better, takes a bit longer to calculate **[better preview]**.
     * **High** -  looks good, takes some time **[pre-shipping]**.
     * **Production** - looks great, takes a long time **[shipping]**.

2. **Shadowing [WIP]**
   * Since there is no perfect method for shadowing, ue4 offers a variety of shadowing methods to cater for various cases such as large objects in the scene versus small surface detail.
   * Ue4 offers two main shadow types:
     * **Static**:
       * Static light type
       * Inexpensive
       * No scene interaction
     * **Dynamic**:
       * Stationary and Movable
       * Expensive
       * Full scene interaction
   * Ue4 also offers some exotic shadow types:
     * **Cascaded** - divides the view frustum into a series of distance-based shadow cascades, each of which with steadily lower resolution as you move farther from the camera. Beyond the range of the **Dynamic Shadow Distance** property, the system blends back into static baked shadows.
     * **Distance Field** - enables you to shadow at farther distances than traditional Cascaded Shadow Maps (CSM) with a directional light.
     * **Contact** - a great way to improve the visual depth and fidelity of your scene because they provide a more accurate approximation of shadowing, allowing you to add a contoured shadow that might not be achieved with other shadowing algorithms.

1. **Post Process**
   * This is an area which eats up a large amount of performance. Post process effects are created by placing a **post process volume** in the scene (locatable within the *Modes pane*).
   * Enabling the **Unbound** setting under the **Post Process Volume Settings** section within the *Details pane* of the volume allows for this volume to manage all post process effects within the scene and ensures they are visible throughout the world.
   * Since the post process volume offers such a vast range of effects, the best approach is to pay close attention to the scene **frames per second (fps)** as each setting is enabled. Attempt to achieve the ideal aesthetic with a minimal number of post process effects to maximise the scene performance.