# Importing and Exporting

A summarised guide on the processes related to importing and exporting static, skeletal and 3D meshes, re-importing assets, auto re-import and full scene import from DCC applications as well as exporting assets from Unreal.

## Exporting Static Meshes
* These should be exported using the **FBX** format.

* Within the export configuration window, tick the **Smoothing Groups**, **Triangulate** and **Preserve Edge Orientation** options under the **Geometry** section. 

* It is generally recommended to disable all other configuration properties so it is clear which properties of the mesh will be imported.

## Exporting Skeletal Meshes
* These should be exported using the **FBX** format.

* Within the export configuration window, tick the **Smoothing Groups**, **Triangulate** and **Preserve Edge Orientation** options under the **Geometry** section. This prepares the static mesh component of the skeletal mesh.

* Proceed to tick the **Animation** option under the **Animation** section and **Deformations** and **Skins** options under the **Deformations** section.

* It is generally recommended to disable all other configuration properties so it is clear which properties of the mesh will be imported.

## 3D Mesh Import
* These can be imported in the same way as [Texture Imports](/Content/DevPipelines/Textures.md#importing-textures). Unreal attempts to automatically configure the import settings but some generally require some tweaking depending on the asset type.

* When importing **Static Meshes**, the following import parameters require attention:
   
   * Auto Generate Collision (**Enable**)
   
   * Generate Light Map UVs (**Enable** but **may want to disable** depending on the UVs that have been added from the DCC application)
   
   * Transform Vertex to Absolute (**Enable**)
   
   * Import Materials (**Disable** unless materials are exported within the mesh)
   
   * Import Textures (**Disable** unless textures are exported within the mesh)

* When importing **Skeletal Meshes**, the following import parameters require attention:
   
   * Skeletal Mesh (**Enable**)
   
   * Import Animations (**Enable**)
   
   * Import Materials (**Disable** unless materials are exported within the mesh)
   
   * Import Textures (**Disable** unless textures are exported within the mesh)

## Re-Importing Assets
* This is useful for ensuring Unreal is using the latest version of a modified asset.

* This can be achieved in a variety of methods:
   
   * **Right click** within the *Content browser* the asset and select **Reimport**
   
   * Within the *asset viewer* window select the **Reimport** button from the *toolbar*
   
   * **Drag & Drop** the asset from a *file browser* window into the *Content browser*

## Auto Re-Importing
* This feature works by constantly monitoring defined directories for any changes. When a change occurs, the modified asset is automatically re-imported into Unreal.

* To configure this functionality, define **Directories to Monitor** under the **Auto Reimport** section of **Loading & Saving** tab within the **Editor Preferences**.

* It may prove beneficial to enable the **Monitor Content Directories** parameter within the same section.

## Full Scene Import
* Entire levels can be imported from DCC applications into Unreal.

* This supports a single import which can include all of the following:
   
   * Static meshes
   
   * Skeletal meshes
   
   * Animations
   
   * Materials (limited import support)
   
   * Textures
   
   * Rigid mesh
   
   * Morph targets
   
   * Cameras (without any animation)
   
   * Lights

* This can be done by selecting the **Import Into Level...** option under the **Actors** section within the **File** menu.

## Exporting Assets from Unreal
* Any importable assets can also be exported from Unreal.

* When exporting **Textures**, **Static Meshes** and **Skeletal Meshes** out of a project for use in other applications, simply **Right Click** on the asset and select **Export...** from the **Asset Actions** options.

* When exporting **any kind of asset** out of a project and into another, simply **Right Click** out of a project and into another, on the asset and select **Migrate...** from the **Asset Actions** options.