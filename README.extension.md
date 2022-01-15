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

Luna Paint features a walkthrough experience to learn how to use the extension. Access it via VS Code's Get Started page or the `Luna > Help: Open Documentation` command:

![](https://raw.githubusercontent.com/lunapaint/vscode-luna-paint/master/images/readme/walkthrough.png)



## Tools

There are a growing range of tools available in Luna paint which can be accessed in the Tools window in the top left of the image editor.

![](https://raw.githubusercontent.com/lunapaint/vscode-luna-paint/master/images/readme/tools-overview.png)



## Image and layer commands

Luna Paint contributes many commands that are accessible via the command palette or the Menu button in the top left corner of the editor. Try searching the command palette for `luna image` or `luna layer`.

![](https://raw.githubusercontent.com/lunapaint/vscode-luna-paint/master/images/readme/image-commands.png)

This is also a great way to learn the default keybindings.



## Resources

- [Customization](https://github.com/lunapaint/vscode-luna-paint/wiki/Customization)
- [Limitations](https://github.com/lunapaint/vscode-luna-paint/wiki/Limitations)



## Open source licenses

The following open source libraries are shipped as part of Luna Paint:

| Project | License | Reason
|---------|---------|--------
| [pako]  | [MIT][pako_MIT] and [Zlib][pako_Zlib] | Used to decompress png datastreams



[pako]: https://www.npmjs.com/package/pako
[pako_MIT]: https://github.com/nodeca/pako/blob/master/LICENSE
[pako_Zlib]: https://github.com/nodeca/pako/blob/master/lib/zlib/README