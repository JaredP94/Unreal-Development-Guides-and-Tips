# Requirements and Configuration

A summarised guide on the engine requirements for using Chaos physics within your projects. As well as project configuration to enable the required subset of Chaos features.

## Software Requirements
* Unreal Engine version 4.23 or later is required to access the Chaos Physics features.

* Engine versions 4.23 through 4.25 require source builds, and have produced varied results when trying to use Chaos since it has been in beta. For the sake of feature completeness and reliability of feature access, I will not delve into those versions (if you need to use one of these versions, see the *Setting up Chaos Destruction* section of the [documentation](https://docs.unrealengine.com/en-US/Engine/Chaos/ChaosDestruction/ChaosDestructionOverview/index.html))

* Engine version 4.26 is the first to offer Chaos in a production-ready state and is included in the launcher version. At the time of writing, 4.26p1 is available for download through the Epic Games Launcher. **NOTE: This has been reverted in the main binary version of 4.26, however, a separate _4.26-Chaos_ binary has been made available via the launcher**

* If porting an existing project, note that NVIDIA PhysX has been deprecated in 4.26 and Chaos is now the default physics engine.

## Project Configuration

* A collection of different plugins are required based on the physics feature required within a project. These are detailed below and will be updated as more use-cases are added:
  
  * **Physics Destruction:**

    * Chaos Editor

    * Chaos Solver

    * Chaos Niagara

    * Planar Cut

    * Editable Mesh

    * Geometry

    * Geometry Cache

    * Field System

* Restart the editor once the plugin configuration is complete.
  

## Engine Changelog
* This section summarises any general Chaos Physics improvements/modifications as new engine versions are made available.
  
* **UE 4.26p1**: 
  
  * First production-ready release
