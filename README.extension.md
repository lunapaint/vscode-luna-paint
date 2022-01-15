_Luna Paint_ is a VS Code extension that lets you edit raster images from within the editor, just open an image from the explorer and start editing like any other file.

> ⚠ This is a preview release:
> - Some features you expect from an image editor may be missing or limited.
> - Hot exit state may break when the extension updates as the data format gets refined.
> - Images below may show older versions of the UI.
> - If you hit any problems or want to request a feature, please [create an issue on the repo](https://github.com/lunapaint/vscode-luna-paint).

![](https://raw.githubusercontent.com/lunapaint/vscode-luna-paint/master/images/readme/demo.png)



## Features

- **VS Code native**: Luna Paint was built from the ground up for VS Code.
- **Performance**: The editor is built on WebGL to achieve a smooth editing experience.
- **Layers and blend modes**: Compose an image using multiple layers, combining them with blend modes.
- **Powerful tools**: A growing range of tools are available to modify images.
- **Formats supported**: .bmp, .ico, .jpg, .png, .webp.
- **Import from clipboard**: Quickly edit the image in the clipboard via ctrl/cmd+'.
- **Hot exit**: Support for [hot exit](https://code.visualstudio.com/docs/editor/codebasics#_hot-exit) is available for small images, just like in text files.
- **Remote support**: Edit images remotely in a [GitHub Codespace](https://github.com/features/codespaces) or via the [Remote WSL](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl), [SSH](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh) and [Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) extensions.
- **Web support**: The extension works in [vscode.dev](http://vscode.dev/) and [github](http://github.dev/).



## Getting started

Luna Paint features a walkthrough experience to learn how to use the extension. Access it via VS Code's Get Started page which you can access via the Help menu:

![](https://raw.githubusercontent.com/lunapaint/vscode-luna-paint/master/images/readme/walkthrough.png)



## Tools

There are a growing range of tools available in Luna paint which can be accessed in the Tools window in the top left of the image editor.

![](https://raw.githubusercontent.com/lunapaint/vscode-luna-paint/master/images/readme/tools-overview.png)



## Image and layer commands

Luna Paint contributes many commands that are accessible via the command palette or the Menu button in the top left corner of the editor. Try searching the command palette for `luna image` or `luna layer`.

![](https://raw.githubusercontent.com/lunapaint/vscode-luna-paint/master/images/readme/image-commands.png)

This is also a great way to learn the default keybindings.



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



## Open source licenses

The following open source libraries are shipped as part of Luna Paint:

| Project | License | Reason
|---------|---------|--------
| [pako]  | [MIT][pako_MIT] and [Zlib][pako_Zlib] | Used to decompress png datastreams



[pako]: https://www.npmjs.com/package/pako
[pako_MIT]: https://github.com/nodeca/pako/blob/master/LICENSE
[pako_Zlib]: https://github.com/nodeca/pako/blob/master/lib/zlib/README