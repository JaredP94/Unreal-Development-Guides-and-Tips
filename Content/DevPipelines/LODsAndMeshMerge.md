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
   * This tool facilitates the ability to merge background objects together in order to reduce their **draw call** and **material count**. This is done by merging the static meshes and materials into a singular mesh and material respectively, thus reducing the memory consumption and rendering cost. The result is almost indistinguishable as the triangle count remains unchanged (in most cases), preserving the visual fidelity.
   * Within the UE4 editor, select all the static meshes from the **World Outliner** pane which are to be merged. Then access the merge tool by navigating to **Window -> Developer Tools -> Merge Actors**.
   * A window will then appear which allows for the selected meshes to be confirmed along with a range of settings for the resultant merged mesh.
   * Noteworthy **Mesh Settings**:
     * Enabling the **Pivot Point at Zero** setting sets the pivot point of the merged mesh to **[0, 0, 0]**. Hence when dragging the merged mesh into the world and setting its **transform** to **[0, 0, 0]**, it will be placed in the exact location of the meshes before they were merged.
     * Setting the **LODSelection Type** option to **Use specific LOD level** allows for a specific LOD level to be used. It is advisable to select the **base LOD level (0)** which preserves the highest quality of the merged mesh. Further LODs can then be generated on the merged mesh thereafter if required.
   * Noteworthy **Material Settings**:
     * Enabling the **Merge Materials** setting allows for all mesh materials to be combined into a singular material. This option is enabled by default when setting the **LODSelection Type** option to **Use all LOD levels**.
     * Adjusting the **Texture Size** setting determines the resulting texture size of the merged materials, which yields a performance gain. It is advisable to not reduce the size to below **1024 x 1024** unless the result is a very small mesh or very far away.
     * Ensure the **Blend Mode** option is configured to the type of materials which are being used in the meshes (i.e masked material).
   * Noteworthy **Landscape Culling** settings:
     * Enabling the **Use Landscape Culling** setting allows for any triangles which intersect with the landscape to be culled, which yields a performance gain.
   * Enabling the **Replace Source Actors** setting will result in any selected actors being replaced by the mesh that results from the merge.
   * Once the merge has completed, the selected meshes can be deleted and the merged mesh can be dragged into the scene. It should position itself in the same position after the mesh **transform** has been reset.

3. **Hierarchical Level of Detail Tool**
   * This tool blends the idea of LODs and the mesh merge tool. When an HLOD is applied, at a certain viewing distance, groups of meshes will be merged with  results containing a few materials rather than all the original materials. Furthermore, an automatic LOD will be applied based on the distance of the mesh.
   * To enable the HLOD tool, enable the **Enable Hierarchical LOD** option under the **LODSystem** section of the *World Settings* pane. Properties under the **Hierarchical LODSetup** setting should automatically be generated.
   * Open the HLOD tool by navigating to **Window -> Hierarchical LOD Outliner**.
   * Select the **Generate Clusters** button to create clusters to encapsulate groups of meshes within the scene. These will be generated with a default **Desired Bound Radius** which can be modified under the **Cluster Generation settings** section of the **HLOD Level**. Alter the value to encapsulate more/fewer meshes within a single mesh.
   * Another way in which the volume radius can be adjusted is to select a mesh which should be included and drag it into the target grouping volume. This will result in the target volume automatically resizing itself to contain the selected mesh. This is useful when dealing with sizeable meshes which are not contained within any generated grouping volumes.
   * These groups meshes will not be rendered until a certain LOD distance is reached, thus leaving the original meshes unchanged until that distance is reached.
   * Once the groupings are finalised, select the **Generate Proxy Meshes** button to begin the merge operation. This essentially runs a similar process to the **Merge Actor Tool** but with most of it automatically handled. Note that this can be quite a time consuming process depending on the meshes and materials involved.
   * Once complete, the outcome can be easily verified by selecting individual meshes at close range (as before) and then moving the camera significantly further away from the meshes and attempting to select the same mesh. At a distance, the merged group of meshes becomes selected as the group of meshes has been replaced by the cluster mesh.