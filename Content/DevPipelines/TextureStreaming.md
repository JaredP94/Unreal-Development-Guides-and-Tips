# Texture Streaming

A summarised guide on the concepts of texture streaming, increasing the texture streaming pool size and disabling texture streaming.

## Texture Streaming
   * This denotes the detail of the textures which are to be viewed.
   * Texture streaming is responsible for handling the transition between different mipmaps as the camera distance is changed.
   * As the camera moves closer to the texture, the texture streaming pool will become more full due to the larger mipmaps being streamed.
   
## Increasing Texture Streaming Pool Size
   * Warnings may arise when attempting to render extremely high detail textures within the scene. This is typically common in ArchViz projects.
   * This can be mitigated by increasing the texture streaming pool size in two ways.
   * The first method entails using the *Console*, which can be opened with the **tilde** key, with the command:
        ```cpp
        r.Streaming.PoolSize = [DesiredSizeInMB]
        ```
    * The second method entails editing the **DefaultEngine.ini** file which is a more permanent solution if the issue is reoccurring. Within the file locate the **[/Script/Engine.RendererSettings]** section and add the line:
        ```cpp
        r.Streaming.PoolSize = [DesiredSizeInMB]
        ```

## Disabling Texture Streaming
   * This is useful when the highest resolution texture is desired at any given camera distance. 
   * This will severely impact performance if applied to all project textures.
   * Applicable cases generally include UI elements and text containing textures which the user is required to read with clarity.
   * Within the texture viewer window, **enable** the **Never Stream** parameter under the **Texture** section of the *Details* pane.