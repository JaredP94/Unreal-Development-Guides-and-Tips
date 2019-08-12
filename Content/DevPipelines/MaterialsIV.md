# Materials IV: Vertex Animation Materials

A summarised guide on vertex animation concepts, performance considerations and use cases along with an example of creating a vertex animation material.

## Vertex Animations
   * These are used to cheaply convey subtle movement for complex objects (i.e foliage, water, cloth, etc).
   * The animations are rendered by the GPU as vertices are continuously being slightly offset within a given mesh.
   * The downside to this is that physics interactions are not entirely accurate since the CPU calculates the interaction without knowledge of the offsets which are occurring.
   * Thus vertex animation should be used a secondary line of animation in cases such as added perceived realism within level scenery where interactivity is not required.

## Vertex Animation Foliage Configuration
   * Consider the case where a tree needs to be animated using vertex animation. Two materials are used within the tree mesh, namely a material for the trunk and a material for the foliage component. The latter will then use vertex animation whilst the former will not.
   * Create a new material which will be used for the vertex animation. Ensure the material is prefixed with **M_VT** to indicate it is a vertex animation material.
   * Open the material viewer for the newly created material.
   * Set the **Blend Mode** parameter to **Masked** within the **Material** section under the *Details* pane. This is because a masked texture will be used to give the leaves their appearance.
   * Set the **Two Sided** parameter to **Enabled** within the same section. This ensures the tree foliage appears correctly at any angle.
   * Add a **Texture Sample** node with the masked foliage material and connect its output to the **Base Color** of the vertex material. Furthermore, connect the **Alpha** of the node to the **Opacity Mask** of the vertex material.
   * Add a **Texture Sample** node with the normal foliage material and connect its output to the **Normal** of the vertex material.
   * Add a **Decimal** node and connect its output to the **Roughness** of the vertex material. Set a value of **0.5** to get the leaves a more realistic appearance.
   * Add a **Simple Grass Wind** node and connect its output to the **World Position Offset** of the vertex material.
   * Add two **Decimal** nodes. Connect the output of the first to the **Wind Intensity** and **Wind Weight** inputs of the **Simple Grass Wind** and set its value to **0.5**. Connect the output of the second to the **Additional WPO** input of the **Simple Grass Wind**.
   * Replace the foliage material of the tree with the created vertex animation material to yield the animated effect.