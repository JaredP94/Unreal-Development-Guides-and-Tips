# Level Creation

Some core elements are generally required when creating a new level. These include:

1. **Level population**
   * A new level is created without any assets.
   * Be sure to add some meshes so that something is rendered in the level.

2. **Level lighting**
   * Levels are physics based, thus a light source is required to view anything in the level.
   * Adding a **Directional Light** from the *Lights* section of the *Modes* panel will render your level.
   * Set the **Location** of the directional light to **0, 0, 100** to have the light hover above the level origin.

3. **Quick tiling**
   * When tiling your level with meshes, the process can be sped up for drafting sake.
   * Increase the snap size to something relative to the ground tile.
   * Duplicate and place new tiles using **Alt + Left Click** and drag to the required location.
   * Select a number of tiles to duplicate multiple tiles at a time.

4. **Player start location**
   * Starting the game will result in the character spawning in the corner of the map and possibly infinitely falling if no tiles are present at that location.
   * Add a **Player Start** from the *Modes* panel.
   * Change the **Location** of the player start to **0, 0, 100** to have the spawn point at the level origin.

5. **Sky lighting**
   * Meshes are currently being rendered, but the sky is still filled with darkness.
   * Add an **Atmospheric Fog** from the *Modes* panel to illuminate the sky.
   * Set the **Location** of the atmospheric fog to **0, 0, 300** to have the fog source hover above the level origin.

6. **Sun lighting**
   * Currently, the sun is seen to be lying on the horizon in the distance.
   * The sun can be controlled by attached it to the directional light in the level.
   * Select the **Directional Light** from the *World Outliner*.
   * Search for **Fog** in the *Details Panel Search* bar.
   * Check the box for **Atmosphere / Fog Sun Light**.
   * The fog colour show now change to the sky light colour.
   * The sun spot can now be rotated to cast shadows in the level.

7. **Reflection capture**
   * A realistic reflection profile needs to be present within the level.
   * Add a **Sphere Reflection Capture** from the *Modes* panel.
   * Set the **Location** to **0, 0, 500** to hover the reflection capture above the level origin.
   * Select the **Build** dropdown then select **Build Reflection Captures**.

8. **Mesh addition**
   * The level is now ready for meshes to be added and the level design to be realised.
   * Be sure to make use of *Filters* in the content browser to easily identify all available meshes within the project.