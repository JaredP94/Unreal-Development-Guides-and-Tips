# Volumes

A summarised guide on what volumes are and how to make use of Lightmass volumes as well as Cull Distance volumes.

## Brief Intro to Volumes
   * Volumes are specific actors which can be played into a scene to determine a range of interaction factors ranging including controlling the player movement area, affecting how sound will reverberate and affecting lighting or visibility.
   * Ue4 offers a wide range of volumes which can be located within the *Modes pane* (full range of volume types can be found [here](https://docs.unrealengine.com/en-US/Engine/Actors/Volumes/index.html)).
   * Lightmass and Cull Distance volumes are a highly featured volume within ue4 and thus their usage should be optimal where possible.


## Using Lightmass Volumes
   * These volumes have two main purposes within ue4:
     * They determine the bounds of the lightmass simulation (i.e the biggest and smallest areas to be calculated within the simulation). Without this, a large amount of calculation time could be wasted on areas which may not contain any light within the scene. The lightmass volume thus ensures only player-visible areas are added to the light calculation.
     * They provide dynamic objects (i.e. characters) with information about the static lit environment. This is done through lightmass importance to identify areas of interest to determine what lighting surrounds the dynamic objects.
   * Always ensure that the volume within the scene covers all playable areas.
   * The **Lightmass Character Indirect Detail Volume** increases the number of samples which are placed within the lightmass volumes. This is generally used in a scene such an elevator where the character is going to traverse an area with an insufficient amount of samples. The number of samples within this volume can be controlled through the **Static Lighting Level Scale** setting under the **Lightmass** section of the *Details pane*. Be wary of the memory cost induced by a larger number of samples.

## Using Cull Distance Volumes
   * This is an optimisation tool which allows for objects above a specified size and distance from the camera to stop being rendered.
   * Both the size and distance properties must be met for the cull to occur. These are the **Size** and **Distance** properties within a cull distance element under the **Cull Distance Volume** settings in the *Details pane*.
   * A number of size and distance combinations can be created to cater for different groups of objects being rendered.
   * Ensure that the **Allow Cull Distance** setting is enabled under the **LOD** section of the *Details pane* for the target objects.
   * The ideal application of this volume should be that of a safety net, whereby each target object should already have its own **Desired Max Draw Distance** setting defined and the volume simply caters for objects which may not have stopped rendering as desired.