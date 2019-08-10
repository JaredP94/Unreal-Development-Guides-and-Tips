### Lighting, Shadowing, and Post Processing

A summarised guide on how these components can dramatically affect performance, along with where to look to control their impact on your scene. These components generally overlap with each other and more often than not are responsible for the most performance degradation as their over-use is very appealing.

1. **Lighting**
   * It is important to be knowledgeable about the different light types in ue4 and what each type does. Furthermore, it is useful to understand the process of building lighting.
   * There are three lighting mobility types within ue4:
     * **Static** - no properties can be changed at runtime **[cheap]**.
     * **Stationary** - can change its colour and brightness at runtime but cannot move, rotate or change influence size **[moderate]**.
     * **Movable** - capable of changing all properties at runtime **[expensive]**.
   * The mobility type of a light can be set within the **Mobility** setting under the **Transform** section of the light in the *Details pane*.
   * When building scene lighting, ue4 offers four quality modes:
     * **Preview** - gets the point across, but at least it is fast **[preview]**.
     * **Medium** - looks better, takes a bit longer to calculate **[better preview]**.
     * **High** -  looks good, takes some time **[pre-shipping]**.
     * **Production** - looks great, takes a long time **[shipping]**.

2. **Shadowing**
   * Since there is no perfect method for shadowing, ue4 offers a variety of shadowing methods to cater for various cases such as large objects in the scene versus small surface detail.