# Materials I: Basics

A summarised guide on the concepts and uses of physical based rendering, material domains, material instances and master materials along with best practices for materials.

## Physical Based Rendering (PBR)
   * PBR utilises simplified calculations which aim to describe light interaction with different physical surfaces.
   * PBR is  helpful in unifying the art production pipeline as there is no longer a requirement for unique materials which are dependent on the type of light the surface is exposed to.

## Material Domain
   * This determines how the material attributes will be evaluated.
   * **Material Domain** ([additional details](https://docs.unrealengine.com/en-us/Resources/ContentExamples/MaterialProperties/1_5)) attribute defines the usage of a material and is is configurable as:
     * Surface (default - used for any kind of geometry)
     * Deferred Decals (used by Decal Actor)
     * Light Function (applied to lights at LightFunctions)
     * PostProcess (used as Blendable Material in PostProcessing chain)
     * User Interface (used for UMG or Slate UI)
   * **Blend Mode** ([additional details](https://docs.unrealengine.com/en-us/Resources/ContentExamples/MaterialProperties/1_1)) attribute defines the foundation of a material and is configurable as:
     * Masked (surface which requires selective visibility)
     * Opaque (surface through which light neither passes nor penetrates)
     * Translucent (surface which requires some form of transparency)
     * Additive (add material pixels to background pixels)
     * Modulate (multiplies value of material against background pixels)
   * **Shading Model** ([additional details](https://docs.unrealengine.com/en-US/Engine/Rendering/Materials/MaterialProperties/LightingModels)) attribute controls light reflection of a material and is configurable as:
     * Unlit (only outputs Emmissive for colour)
     * Default Lit (uses direct and indirect lighting as well as specularity for reflections)
     * Subsurface (light penetrates surface and then diffuses throughout it)
     * Preintegrated Skin (similar to Subsurface but with low performance cost skin rendering on human characters)
     * Clear Coat (simulate multilayer materials that have a thing translucent layer of the surface)
     * Subsurface Profile (similar to Subsurface and Preintegrated Skin but with higher performance cost skin rendering)
     * Two Sided Foliage (gives foliage more natural and uniform look when being lit)

## Materials
   * These provide a way for Unreal to manipulate and display textures on an object.
   * Materials are built using the **Material Editor** and consist of HLSL (High Language Shader Language) code blocks to manage tinting, blending, etc.
   * Materials have to be compiled before they can be displayed or used in-game. Saving the material will automatically compile it.
   * Once compiled, the material is considered to be static and cannot change during runtime.

## Material Instances
   * These are special materials which allow for value and texture changes at runtime. A recompilation is not required when changing the instance attributes.
   * Material instances can be accessed and modified within timelines and blueprints to generate impressive visual effects.
   * There is a discrete performance improvement in using material instances over materials but this is only really noticed at scale.

## Master Materials
   * These provide the base functionality which a material instance is able to use and modify at runtime such as base colour, roughness, textures, etc.
   * Instance editable attributes can be identified through the **Param** keyword on the master material attributes.

## Master Materials Best Practices
   * Use multiple master materials so that each target component has its own master material (i.e unique master materials for environmental objects, characters, weapons, etc).
   * Do not attempt to use a single master material for all objects. It will likely be unable to offer the broad customisation required, possibly incur performance costs and limits the options available to the artist.

## Master Materials Concepts
   * There are a number of steps involved in the creation of a master material that will ensure it is performant and compatible on any target platform.
   * **Material Functions** facilitate the sharing and reuse of parts of the **Material Graph**.
   * **RGB Mask Packing** stores various **Textures** in the **R**, **G** and **B** channels of a **Texture**. Pay careful attention to which textures are assigned to each channel for future use.
   * **Static Switches** allows for binary control of entire code paths in a material. This can be used for selectively applying high resolution textures to certain objects but not others.
   * **Feature Level Switches** facilitates the creation of a single material which is cross-platform. This takes in multiple versions of the same material to build a cross-platform material.