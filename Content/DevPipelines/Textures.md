### Textures

A summarised guide on optimal settings and best practices used in the creation of textures.

1. **Naming Convention**
   * Using an appropriate naming convention is useful in grouping/parsing assets within a project.
   * Prefix texture assets with a **T_** (i.e **T_Car_Texture_00**).
   * Append texture assets with the suffix that corresponds to the category of the texture (i.e **T_Car_Texture_00_N** corresponds to the *Texture Normal*).

2. **Texture Creation**
   * Texture axes should always be a **power of 2** (i.e **2, 4, 8, 16, 32, 64, 128, 256, 512, 1024, 2048, 4096, 8192**). This is required due to the manner in which the textures are loaded into memory as well as to adhere to Unreal's optimisation techniques that include *mip mapping* and *texture streaming*.
   * Textures are not required to be square, but rather to adhere to the power rule (i.e **512 x 64**, **8192 x 1024**, etc).
   * Following this process allows for LODs to become functional on the texture as a correctly created texture will feature a number of *MIP maps* which facilitates the scaling requirement for LODs.

3. **Handling Alpha Information**
   * There are two ways of storing alpha information in a texture - **Embedded** and **Separate**.
   * Making use of the **Separate** alpha is ideal as it will be compressed when imported into Unreal versus the **Embedded** alpha which will be imported in an uncompressed manner.
   * Making use of the **Separate** alpha also allows for size control which is independent to the **Base** color size.
   * Should you wish to retain the high resolution of the alpha information then the **Embedded** alpha is more useful. Note that this will have **double** the cost of the **Separate** alpha.

4. **RGB Mask Packing**
   * This is a method used to reduce the number of textures and amount of memory used throughout the project. It is generally used within VFX and character model applications. The method involves packing multiple masks together into the **R**, **G**, **B**, and **A** channels of a single image which is then exported.
   * When using this method, only black and white information will be accessible from the texture, so some form of color parameter multiplication will be required to obtain the respective color information.
   * Uncheck the **sRGB** parameter under the **Texture** section of the *Details* pane. This then supports the channel extraction.
   * When using the texture on a material, set the **Sampler Type** to **Masks** under the **Material Expression Texture Base** section of the *Details* pane. This is required as disabling **sRGB** on the texture will disable **gamma correction** on the texture. Mask textures do not require gamma correction as they simply inform the renderer of whether a pixel should be visible or not.

5. **Texture Formats**
   * Unreal supports a range of Texture file formats:
     * PNG (Embedded Alpha support)
     * PSD (Embedded Alpha support)
     * TGA (Embedded Alpha support)
     * BMP
     * FLOAT
     * PCX
     * IPG
     * EXR
     * DDS (Cubemap Texture)
     * HDR (Cubemap Texture - Exception to the *Power of 2* rule)

6. **MIP Mapping**
   * This is a key feature in facilitating good performance within a project. It can be thought of as LODs for textures.
   * MIP map generation occurs when a texture is imported into Unreal. In most cases, no interaction is required unless for a very specific use case. Such a case is where shimmering or aliasing is noticed on an object. This can be adjusted by selecting one of the **Sharpen** configurations from the **Mip Gen Settings** option under the **Level Of Detail** section in the *Details* pane of the texture.
   * This is used to apply a resolution of the texture which is better suited to the render size of the object, rather than incurred the memory cost of rendering the full resolution texture where the full detail cannot be told apart from the scaled down variant.

7. **Importing Textures**
   * There are two ways of importing textures into Unreal, namely the **Drag and Drop** and **Import** methods.
   * The **Drag and Drop** method simply requires a texture to be dragged into the *Content Browser* from a *Windows Explorer Window*. The import is automatically handled.
   * The **Import** method requires the **Import** button in the *Content Browser* to be selected. This opens a *Windows Explorer Window* to navigate to and select the required texture.
   * Unreal will assess the file name of the texture to decide the appropriate type of texture being imported (refer to this [Naming Convention Guide](https://github.com/Allar/ue4-style-guide#anc)).

8. **Texture Groups**
   * These groups serve to manage how textures are used and displayed within a project. Each group determines the size at which the texture will be drawn within the project, how the texture is minified or magnified and what type of filtering is applied to the texture.
   * Thus it is imperative that correct group assignment of each texture is performed.
   * Group assignment is done by changing the **Texture Group** property of the **Level Of Detail** section in the *Details* pane of the texture.
   * Such an example of a defined texture group configuration:  
        ```cpp
        TEXTUREGROUP_World=(MinLODSize=1,MaxLODSize=8192,LODBias=1,MinMagFilter=aniso,MipFilter=point)
        ```

9. **Texture Compression**
    * Texture compression can be adjusted at any time in the editor.
    * Open the target texture from the *Content Browser*.
    * Select the desired **Compression Settings** type under the **Compression** section in the *Details* pane of the texture.
    * Refer to this [Texture Compression Document](https://docs.unrealengine.com/en-us/Editor/Content/Types/Textures/TextureCompressionSettings) for information on each type of texture compression.
    * Certain types of compression will require the **Compress Without Alpha** property to be set. Consult the above document to determine the required configuraton.