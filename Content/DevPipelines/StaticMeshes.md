### Static Meshes

A summarised guide on the components of static meshes and the best practices to be used when creating performance optimised static meshes.

1. **System Units**
   * Consistent use of a specific unit is required to ensure no scaling issues occur.
   * Unreal utilises **centimeters** as its unit of measurement. Thus **1 Unreal unit = 1 Centimeter**.
   * Ensure that the DCC (i.e 3ds Max) system / scene scale is set to centimeters.

2. **Triangle Counts**
   * The number of triangle counts in a static mesh is inversely proportional to the project performance. Thus optimising the triangle count is essential.
   * Do not waste a large number of triangles in modelling small details (i.e nuts and bolts) as the user will not notice the superior level of detail for such small objects.
   * Always display your triangle count as you model the mesh. This can be done in the DCC software as well as the static mesh viewer in Unreal.

3. **Material IDs**
   * These are used to identify which polygon faces get specific materials assigned to them.
   * The performance drawback relates to the number of material IDs as each ID associated to a material will cause the object to be rendered again (i.e 5 material IDs prompt the object to be rendered 5 times before the complete object is ready for rendering).
   * Small props should generally only have a single material ID where as a character may have 2 or 3.

4. **Pivot Points**
   * This is the point of reference for the object to be placed in the level with reference to the target location.
   * Ensure that the pivot point always matches the origin of the object. This prevents awkward placement within the level as a location offset will not need to be considered.
   * Furthermore, an offset pivot point will cause location offset when rotating or scaling the object in Unreal.

5. **Lightmaps**
   * These are used to store complex light and shadow information inside a texture. This is due to textures being cheap and efficient at storing this type of data. Hence the performance cost is low.

6. **Lightmap UVs**
   * These are maps which contain the lighting information for each face of the object.
   * Each face must be laid out in a **0 to 1 UV Space**.
   * Each face must also be unique. Thus no face is allowed to overlap on the map. Should an overlap occur, incorrect lighting will occur on certain faces.
   * Lightmap UV information should be stored in the **second** map channel.
   * Lightmap resolution can be adjusted, if required, by changing the **Light Map Resolution** parameter under the **Static Mesh Settings** section in the *Details* pane of the static mesh.

7. **Collision Meshes**
   * These are responsible for managing collision detection of static meshes, facilitating collision driven events (i.e car impact).
   * Collision meshes should follow the naming convention **UCX_[FullNameOfMesh]_[CollisionNumber]**.
   * There are two ways of using collision meshes inside Unreal. The first involves creating the collision mesh in the DCC application and importing it along with the static mesh geometry. The second involves adding a collision mesh of choice from the *Collision* option in the toolbar of static mesh viewer.
   * When using the former method, ensure that **Auto Generate Collision**, **Import Materials** and **Import Textures** are unchecked when importing.
   * When attempting to add a collision mesh for an organic static mesh (i.e rubble), it is difficult to generate an optimised solution. Unreal caters for this by offering **Convex Decomposition** which offers a fairly accurate optimised collision generation. This can created by setting the desired **Accuracy** and **Max Hull Verts** parameters in the *Convex Decomposition* pane in the static mesh viewer. Thereafter select **Apply** to generate the collision mesh.

8. **Limiting Overdraw**
   * This effect is generally encountered when dealing with static meshes that include transparency or opacity (i.e foliage). This results in the GPU evaluating areas which don't contain any useful information and thus will not be drawn.
   * This can be partially mitigated by adding vertices to clip some of the static mesh so that transparent areas are limited.
   * Unreal offers a number of tools to identify and limit the effects of overdraw. 
   * The first is **Shader Complexity Mode**. Within the editor, overdraw effects can be visualised by selecting **Lit** then selecting **Shader Complexity** from the **Optimization Viewmodes** list.

9. **Level of Detail (LOD)**
    * LODs are lower triangle versions of the same mesh.
    * These are important as they help lower the rendering cost of distant objects.
    * They can be created by hand or programmatically.
    * Typical LOD reduction scales are **75 %**, **35 %** and finally **12 %**.
    * LODs can be created within the DCC application and imported into Unreal with the rest of the static mesh geometry. When importing, ensure that the **Import Mesh LODs** parameter is checked.
    * LODs can be created within Unreal by selecting an appropriate **LOD Group** under the **LOD Settings** section in the *Details* pane of the static mesh viewer. Unreal then generates a set of LODs which matches the **Number of LODs** parameter in the same section.