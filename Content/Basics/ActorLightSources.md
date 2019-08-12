# Actor Light Sources

Actors can be used to create dynamic lighting within a scene. This is generally seen with ceiling lights, fires, torches, etc.

## Fire Torch Example
* Within the *Content Browser*, select the **Add New** button and then the **Blueprint Class**. In the next screen, select the parent class to be an **Actor** class.
* Open the blueprint (ensure the full editor view is open).
* Within the *Viewport* pane, drag in the static mesh to be used (in this case, a fire torch). Ensure that the static mesh is a child of the **DefaultSceneRoot** component.
* Add the particle component which is to be the aesthetic light source of the Actor (in this case, a fire particle component). Ensure the particle component is a child of the **DefaultSceneRoot** component.
* Adjust the particle component to be positioned at the correct location within the static mesh (in this case, the holder area of the fire torch).
* In order to physically emit light into the level, the particle component requires a light source. Within the *Components* pane, select the **Add Component** button and then the **Point Light**. Ensure the point light component is a child of the **DefaultSceneRoot** component.
* Adjust the point light component to be positioned within the particle component. Sometimes placing the light component in an offset position to the particle component will yield a more rewarding lighting effect so be sure to test what works best for your actor and scene.
* In the *Details* pane of the **Point Light** component, adjust the **Light Attention** setting in the **Light** section to a realistic value (in this case, **500.0**).
* In the same section, adjust the **Light Color** setting to an appropriate color (in this case, an orange-based colour).
* Once the actor has been created in the blueprint editor, **Compile** and **Save** the blueprint.

## Light Flicker Effects
* Within the *Event Graph* pane, add a **Delay** block to the **Event BeginPlay** block. Source a **Random Float in Range** block into the **Delay** parameter using **Min** and **Max** values of **0.0** and **0.2** respectively. This now adds a random delay in the fire ignition of the torch.
* Add a **Set Intensity** block to the *Event Graph*. Source a *reference* to the **Point Light** component into the **Target** parameter. Source a **Random Float in Range** block into the **New Intensity** parameter using **Min** and **Max** values of **900.0** and **3000.0** respectively. This now adds a variable intensity for each torch instance.
* Connect the **Delay** block success pin to the trigger input of the **Set Intensity** block. This creates the sequence required for a light flicker.
* Connect the **Set Intensity** success pin to the trigger input of the **Delay** block. This creates the loop for infinite light flickering.
* Once the actor has been created in the blueprint editor, **Compile** and **Save** the blueprint.

## Using Actor Light Sources in a Level
* In the main editor window, drag the blueprint instances into the scene and position as necessary.
* Build all lighting for the level.