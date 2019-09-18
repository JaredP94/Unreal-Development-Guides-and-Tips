# Materials III: Material Instances

A summarised guide on parent (master) materials and their children, creating and using material instances and overriding parent material functionality.

## Parent - Child Relationship
* This relationship mimics that of a parent (master) material and a child (instance) of that material.

* The child can inherit any of the properties of the parent, but not combine them (i.e parent with red and blue produces child with red or blue).

## Creating Material Instances
* There are two methods of creating a material instance within unreal.

* The first involves **right clicking** on the target master material and select **Create Material Instance** within the *Content browser* pane.

* The second involves **right clicking** within the *Content browser* pane and selecting **Material Instance** from the **Materials & Textures** group. Thereafter, open the material instance and select the parent material from the **Parent** parameter under the **General** section of the *Details* pane.

## Using Material Instances
* The material instances do not make use of any inherited parameters by default.

* These can be enabled and configured within the **Parameter Groups** section of the *Details* pane within the material viewer.

## Overriding Parent Material Functionality
* Certain functionalities of the parent material can be overridden by the material instance.

* The overridable parameters can be found in the **Material Property Overrides** group under the **General** section of the *Details* pane.

* These are use-case specific, where the **Two Sided** property, for example, is helpful in ensuring that the material is always rendered even when facing away.