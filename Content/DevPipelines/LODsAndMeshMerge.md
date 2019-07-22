### Levels of Detail (LODs) and Static Mesh Merging

A summarised guide on more advanced LOD concepts and practices, benefits and use of the merge actor tool as well as the benefits of using Hierarchical Level of Detail (HLOD) for distance scaling.

1. **UE4 Automatic LOD Creation Tools**
   * As mentioned in the [Static meshes](StaticMeshes.md) section, LODs can be created for meshes before they are imported into UE4. However, should you opt not to create the LODs or the application not support LODs, UE4 offers a range of tools to facilitate automatic LOD creation.
   * Within the static mesh viewer, when selecting an **LOD Group** under the **LOD Settings** section of the *Details pane*, the **BaseEngine.ini** file is parsed to determine the number of LODs required along with other LOD settings which can be configured in the *Details pane*.
   * Configuring the **Reduction Settings** within the **LOD[number] (i.e LOD1)** section of the *Details pane* determines what graphical fidelity is prioritised as each LOD is generated (i.e Preserve silhouettes, triangles, textures, etc.).
   * Selecting an option from the **LOD Group** will automatically load predefined **reduction settings**, which provide an ideal LOD reduction for the type of static mesh, and generate the ideal number of LODs for that type.
   * To manually customise the generated LODs, simply reduce the **Number of LODs** setting to **1** and select **Apply Changes**. Thereafter, increase the **Number of LODs** to the desired amount and select **Apply changes**. This generates LODs without any reduction and only differ based on the screen size of the mesh.
   * To manually adjust the screen size at which each LOD is used, **Un-tick** the **Auto Compute LOD Distances** box under the **LOD Settings** section. The target screen sizes can then be manually entered.
   * To force a specific LOD to always be rendered on a mesh, simply enter the **LOD number** in the **Forced LOD Mode** field under the **Rendering** section of the *Details pane* after the target mesh has been selected.
   * Maintaining a minimum level of detail is achievable through enabling the **Override Min LOD** option and entering a **Min LOD** value under the **Rendering** section of the *Details pane* after the target mesh has been selected. This ensures that no further reduction occurs once the minimum specified LOD is loaded.

2. **Merge Actor Tool**