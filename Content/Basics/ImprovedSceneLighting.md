# Improved Scene Lighting

Currently, your scene lighting may be quite harsh with overexposure and lack of light in shadow cast areas. These factors can be mitigated as follows:

## Cast Shadows
* Since the directional light in the scene does not make use of bounced light (Ray Tracing will not be used in this instance), an artificial bounced light is required by using the *Sky Light*.

* Add a **Sky Light** from the *Modes* panel.

* Set the **Location** to **[0, 0, 400]** to hover the sky light above the level origin.

* This will result in artificial bounced light in cast shadow areas.

* Note that the default parameters are recommended and any adjustment should occur within the scene light sources rather than the sky light itself.

## Automatic Light Exposure
* Moving the camera around the scene will result in automatic light exposure which may increase the difficulty of correctly balancing the scene lighting. A *Post Process Volume* allows for control of all light in the scene through a single controller.

* Add a **Post Process Volume** from the *Modes* panel.

* Set the **Location** to **[0, 0, 0]** to place the post process volume at the level origin.

* Under the **Lens** section of the *Details* pane for the post process volume, enable the **Min Brightness** and **Max Brightness** options with respective values of **1.0** each. This enforces the standard light exposure within the volume constraints.

* Under the **Post Process Volume Settings** section, enable the **Infinite Extent (Unbound)** option. This enforces the standard light exposure across the entire level bounds.

## Realistic Sky Effects
* The scene is lacking a realistic looking sky.

* Add a **BP_Sky_Sphere** from the *Modes* panel.

* Set the **Location** to **[0, 0, 0]** to place the post process volume at the level origin.

* The sky sphere offers optimal effects when linked to a directional light, as with atmospheric fog.

* Under the **Default** section of the *Details* pane for the sky sphere, select the dropdown for the **Directional Light Actor** setting and select the directional light in the level.

## Environmental Light Tweaking
* Environmental lighting can be customised to a range of settings to meet the requirements of the level design. This is such an example:

* Under the **Light** section of the *Details* pane for the directional light, set the **Intensity** setting to a value of **1.0 lux** for a dusk-like effect.

* Rotate the directional light to be at an appropriate angle for a dusk-like setting. Note that the sun spot does not update, and the sky sphere needs to be disabled temporarily to see the expected changes. Thereafter, re-enable the sky sphere and select the **Refresh Material** setting under the *Details* pane.

* To enable sun rays from the sun spot, enable the **Light Shaft Occlusion** and **Light Shaft Bloom** settings under the **Light Shafts** section of the *Details* pane. To reduce the glaring effect, set the **Sun Brightness** setting to a value of **1.0** under the **Default** section in the *Details* pane of the sky sphere.

* To add some lighting dynamism to scene, set the values of the **Bloom Scale** and **Bloom Threshold** settings to **0.55** and **0.15** respectively under the **Light Shafts** section in the *Details* pane of the directional light.