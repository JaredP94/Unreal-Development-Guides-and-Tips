### Materials II: Master Materials and Material Functions

A summarised guide on configuring a master material as well as creating and making use of material functions.

1. **Creating Master Materials**
   * Within the *Content browser* create a new material and open it in the *Material viewer* window.
   * **Parameterise** the options which are intended to be used by instances. This is done by adding a **VectorParameter**, assigning it a **Parameter Name**, and assigning a **Group** under the **General** section of the *Details* pane.
   * Thereafter, connect the **VectorParameter** node to the material parameter which is expected to change with instances (i.e base colour).

2. **Adding Textures to Master Materials**
   * As previously mentioned, asset textures can be changed by material instances at run time.
   * Select the desired texture within the *Content browser*.
   * Within the *Material viewer* window of the master material, hold the **T key** and click on an empty space to create a **Texture Sample** node. 
   * **Right click** the texture sample and select **Convert to Parameter** to have the texture converted to a **texture object**. This now allows the texture to be modified in instances.
   * Assign the texture object a **Parameter Name** and **Group**.

3. **Creating Material Functions**
   * Material functions are a way of sharing shader code between multiple materials.
   * Within the *Content browser*, **right click** and select **Material Function** from the **Materials & Textures** option.
   
4. **Basic Material Function Example**
   * In this example, the goal is to configure the material function to implement basic texture tiling which can be shared between materials.
   * Open the material function within its viewer to edit the function.
   * Within the **Material Expression Function Output** section of the *Details* pane, enter an **Output Name** and **Description**. This defines the function name and a brief description of what it does.
   * Add a **TextureCoordinate** node as well as a **Function Input** node. Within the function input, define an **Input Name**, **Description** and **Input Type**. The objective of this is to multiply the number of tiles.
   * Add a **Multiply** node and connect the inputs to the **TextureCoordinate** and **Function Input** nodes.
   * Connect the result of the **Multiply** node to the **Output TitleOut** node.
   * Finally, select **Apply**.
   * Adjusting the scalar function input will result in varying previewed output.
   * This function can now be added to multiple materials and connected to the **Input UVs** of **texture parameters** to enable the tiling.