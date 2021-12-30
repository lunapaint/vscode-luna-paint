_Luna Paint_ is a VS Code extension that lets you edit raster images from within the editor, just open an image from the explorer and start editing like any other file.

> ⚠ This is a preview release:
> - Some features you expect from an image editor may be missing or limited.
> - Hot exit state may break when the extension updates as the data format gets refined.
> - Images below may show older versions of the UI.
> - If you hit any problems or want to request a feature, please [create an issue on the repo](https://github.com/lunapaint/vscode-luna-paint).

![](https://raw.githubusercontent.com/lunapaint/vscode-luna-paint/master/images/readme/demo.png)

## Features

- **Performance**: The editor is built on WebGL to achieve a smooth editing experience.
- **Layers and blend modes**: Compose an image using multiple layers, combining them with blend modes.
- **Powerful tools**: A growing range of tools are available to modify images.
- **Formats supported**: .bmp, .ico, .jpg, .png, .webp.
- **Import from clipboard**: Quickly edit the image in the clipboard via ctrl/cmd+'.
- **Hot exit**: Support for [hot exit](https://code.visualstudio.com/docs/editor/codebasics#_hot-exit) is available for small images, just like in text files.
- **Remote support**: Edit images remotely in a [GitHub Codespace](https://github.com/features/codespaces) or via the [Remote WSL](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl), [SSH](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh) and [Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) extensions.
- **Web support**: The extension works in [vscode.dev](http://vscode.dev/) and [github](http://github.dev/).

## Tools

The Tools window in the top left of the editor allows switching the active tool.

- The window can be hidden by hitting the `X` icon and toggled via Luna's _Menu_, the command palette or `F5`.

### Pencil

The Pencil tool is used to draw individual pixels.

- Use left or right click to draw freehand using the _primary_ or _secondary color_ respectively.
- Shift+click draws a line from the last drawn point, holding shift will show the angle of the line and which pixels will be drawn to.
- Set the _Blend Mode_ option to be used with the pencil, or select _replace_ to replace the color without blending.

![](https://raw.githubusercontent.com/lunapaint/vscode-luna-paint/master/images/readme/pencil.gif)

### Eraser

The Eraser tool is used to set pixels to fully transparent.

- Set the brush size to clear more than a single pixel.

![](https://raw.githubusercontent.com/lunapaint/vscode-luna-paint/master/images/readme/eraser.gif)

### Fill

The Fill tool will flood fill an area with similar colors to the pixel it was triggered on.

- Set the _Flood Mode_ option to _global_ in order to replace pixels across the entire image, regardless of whether they are adjacent.
- Tolerance can be set to determine how different a pixel needs to be to fill, compared to the pixel that is clicked.

![](https://raw.githubusercontent.com/lunapaint/vscode-luna-paint/master/images/readme/fill.gif)

### Color Picker

The Color Picker tool (aka eye dropper) allows sampling a layer's individual pixels for their color.

- Change the _Sampling_ option to average the colors over a range of pixels.

![](https://raw.githubusercontent.com/lunapaint/vscode-luna-paint/master/images/readme/color-picker.gif)

### Selection, Move Selection and Move Pixels

The Selection, Move Selection and Move Pixels tools allow selecting a portion of the image/layer, modifying that selection and moving the selected pixels.

- Ctrl/cmd+a can be used to select the entire image.
- Ctrl/cmd+shift+x to crop the image to the selection.
- Dragging the handles will resize the selection or scale the pixels.
- The Move Pixels tool supports scaling the selection and expanding the canvas to the selection.

![](https://raw.githubusercontent.com/lunapaint/vscode-luna-paint/master/images/readme/selection.gif)

### Crop

The Crop tool (<kbd>c</kbd>) enables cropping an image in a single action, as opposed to creating a selection and then cropping that.

![](https://raw.githubusercontent.com/lunapaint/vscode-luna-paint/master/images/readme/crop.gif)

### Rectangle

The Rectangle tool can be used to draw a rectangle and then manipulate it within the canvas.

- Supported options include blend mode, style (fill, outline or both) and outline size.
- Hold shift to drawing a square.
- Options can be independently configured, even after drawing the rectangle.
- The rectangle dimensions and top left coordinates are shown in the status bar.

![](https://raw.githubusercontent.com/lunapaint/vscode-luna-paint/master/images/readme/rectangle.gif)

### Line

The Line tool can be used to draw straight lines.

- The blend mode option is supported.
- Hold shift to draw the line to the nearest 15°.

![](https://raw.githubusercontent.com/lunapaint/vscode-luna-paint/master/images/readme/line.gif)

### Zoom

The Zoom tool allows zooming in and out with left and right click respectively.

- Ctrl+wheel can also be used to zoom, regardless of what the active tool is.

![](https://raw.githubusercontent.com/lunapaint/vscode-luna-paint/master/images/readme/zoom.gif)



## Palette

The Palette window lets you select the primary and secondary colors, with some basic colors available for quick access.

- In most tools, left click uses the _primary color_ and right click uses the _secondary color_.
- Transparent colors display over a checkered background.
- Pressing `x` will swap _primary_ and _secondary colors_.
- Sliders are available to change channels quickly, the mouse wheel can be used while hovering the slider to increment/decrement by 1.
- The window can be hidden by hitting the `X` icon and toggled via Luna's _Menu_, the command palette or `F8`.

![](https://raw.githubusercontent.com/lunapaint/vscode-luna-paint/master/images/readme/palette-window.png)



## Layers

The Layers window shows a preview of the image's layers and lets you modify their properties or change the active layer.

- The controls at the bottom of the window manipulate the current layer.
- The blend mode of a layer changes the way it blends with the layer(s) below.
- Layers can be hidden by clicking the checkbox.
- The window can be hidden by hitting the `X` icon and toggled via Luna's _Menu_, the command palette or `F7`.

![](https://raw.githubusercontent.com/lunapaint/vscode-luna-paint/master/images/readme/layers-window.png)

There are many commands that run on either the _Layer_ or _Image_ (all layers), these are accessible via Luna's _Menu_ or the command palette:

![](https://raw.githubusercontent.com/lunapaint/vscode-luna-paint/master/images/readme/layer-commands.png)
![](https://raw.githubusercontent.com/lunapaint/vscode-luna-paint/master/images/readme/image-commands.png)



## History

The History window allows viewing and navigating through changes made to the image, it's a more visual representation of VS Code's regular undo/redo stack.

- Clicking an item in the history window will undo/redo to that point.
- The window can be hidden by hitting the `X` icon and toggled via Luna's _Menu_, the command palette or `F6`.

![](https://raw.githubusercontent.com/lunapaint/vscode-luna-paint/master/images/readme/history-window.png)



## Minimap

The Minimap window shows the image with all layers blended together on an opaque background, it can be used to navigate around the image as well as to view a preview of the overall image without zooming out.

- Move the viewport by clicking and dragging within the minimap.
- Mouse wheel will zoom the viewport in and out.
- By default stretch mode is enabled which will fill the minimap with the image, this can be turned off to view small images at actual size which is especially useful when working with pixel art as you can be zoomed fine tuning the image while still seeing a 100% view of it.
- The viewport rectangle can be toggled off.

![](https://raw.githubusercontent.com/lunapaint/vscode-luna-paint/master/images/readme/minimap-window.png)



## Customization

### Default image size

The image size when creating a new image can be defined in the `luna.defaultImageSize` settings. You may want to set this to the size of your monitor setup for example to quickly paste in screenshots.

### Auto Save

Many people use auto save and it's enabled by default in GitHub Codespaces. Using it with Luna Piant has some consequences when working on larger images though as saves can be expensive (hopefully not forever, see Limitations). You may want to disable auto save if you edit larger images with this extension until a solution is worked out:

```json
"files.autoSave": "off"
```

### Free up memory of backgrounded tabs

Disabling `luna.retainContextWhenHidden` will dispose of editor contexts, slowing down tab restoring while freeing up memory. This is enabled by default because files where hot exit are disabled will lose changes when switching tabs. The recommendation for now is to set this to false if you work exclusively in small images.

### Avoiding conflicts in keybindings

To avoid conflicts between Luna Paint's keybindings and user defined keybindings, it's recommended to use the `when` clause `luna:focused && activeCustomEditorId == 'luna.editor'` or the inverse. For example:

```jsonc
// Only enable this keybinding when Luna Paint is not focused, such that it doesn't conflict with
// the default crop to selection keybinding.
{
  "key": "ctrl+shift+x",
  "command": "workbench.action.terminal.kill",
  "when": "!luna:focused && activeCustomEditorId != 'luna.editor'"
}

// Only enable this keybinding when Luna Paint is focused
{
  "key": "e",
  "command": "luna.image.expandCanvasToSelection",
  "when": "luna:focused && activeCustomEditorId == 'luna.editor'"
}
```



## Limitations

### Loading and Saving Files

The loading and saving of `png`, `jpg` and `bmp` images is currently handled by Electron/Chromium, as such the options for tweaking/optimizing how the images get encoded is limited. This also means that while the editor does support layers, saving an image that supports layer is not currently possible. More options for file formats and encoding options is planned for the future.

### Layers causing rendering issues

On some machines (eg. my macbook), rendering messes up when there are more than 2 layers.

### VS Code Custom Editors

Luna Paint is built on VS Code's custom editor's API. Below are some of the limitations in the API.

- The tab may lock up when doing busy work (filling, resizing, saving, updating minimap, etc.), the editor was built to support workers in order to keep the UI thread responsive, but it needed to be turned off until [microsoft/vscode#87282](https://github.com/microsoft/vscode/issues/87282) is done.
- Large images can take a while to load, this is because of the slow transfer speed and lack of ArrayBuffer support of postMessage, see [microsoft/vscode#79257](https://github.com/microsoft/vscode/issues/79257).
- Hot exit is only enabled by default for relatively small images, this is largely due to the slow transfer speed and lack of workers mentioned above.
- Hot exit will prevent closing with an error about dirty custom editors if you make a change and switch away from the tab. `"retainContextWhenHidden": true` works around this, the proper fix is [microsoft/vscode#113507](https://github.com/microsoft/vscode/issues/113507).
- Auto save has problems with custom editors and large files [microsoft/vscode#115404](https://github.com/microsoft/vscode/issues/115404).