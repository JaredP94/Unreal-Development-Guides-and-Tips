### Textures

A summarised guide on optimal settings and best practices used in the creation of textures.

1. **Naming Convention**
   * Using an appropriate naming convention is useful in grouping/parsing assets within a project.
   * Prefix texture assets with a **T_** (i.e **T_Car_Texture_00**).
   * Append texture assets with the suffix that corresponds to the category of the texture (i.e **T_Car_Texture_00_N** corresponds to the *Texture Normal*).

2. **Texture Creation**
   * Texture axes should always be a **power of 2** (i.e **2, 4, 8, 16, 32, 64, 128, 256, 512, 1024, 2048, 4096, 8192**). This is required due to the manner in which the textures are loaded into memory as well as to adhere to Unreal's optimisation techniques that include *mip mapping* and *texture streaming*.
   * Textures are not required to be square, but rather to adhere to the power rule (i.e **512 x 64**, **8192 x 1024**, etc).
   * Following this process allows for LODs to become functional on the texture as a correctly created texture will feature a number of *mip maps* which facilitates the scaling requirement for LODs.

3. **Handling Alpha Information**