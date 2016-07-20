# PixiAnimate Extension

Creates a custom FLA document which support publishing to [PixiJS](http://pixijs.com) natively in Adobe Animate CC (formerly Flash CC 2015).

## Examples

See [examples](https://github.com/jiborobot/pixi-animate-examples) for sample FLA document to test features of PixiAnimate.


## Dependencies

The following dependencies are required in order to publishing FLA document created with this Plugin.

* Adobe Flash CC 2015+ or Adobe Animate CC
* Mac OS X (Window not currently supported)
* [Node & NPM](http://nodejs.org)
* [Electron](http://electron.atom.io/) `npm install -g electron-prebuilt`

## Installation

If you are trying to install with Adobe Animate CC 2015, you **cannot** install the ZXP with Adobe Extension Manager CC (this not longer is supported in CC 2015). There are two ways to install:

* [Enable syncing](https://www.adobeexchange.com/resources/19) in your Adobe CC desktop application (**recommended**); or
* Use the [Manage Extension utility](http://blogs.adobe.com/animate/installing-zxp-extensions-using-the-manage-extensions-utility/) to manually install.

## Building

To get setup, please follow the instructions outlined from [Adobe's documentation](https://helpx.adobe.com/flash/using/enabling-support-custom-platforms.html#Building%20a%20Flash%20custom%20platform%20support%20plug-in). This will enable you to build the project itself and see the plugin exposed from Adobe Animate CC.  

- Some project / file names may be changed due to not wanting to produce a plugin named "SamplePlugin".
- The certificate password is: `password`

### CEP Debug Mode

To setup your platform for development, you must enable debugging in your Adobe preferences for CEP. **_VERY Important to reboot your machine after making this change_** or it will not take effect.

#### Windows

Go to Registry, `regedit` > `HKEY_CURRENT_USER/Software/Adobe/CSXS.6`, then add a new entry `PlayerDebugMode` of type `"string"` with the value of `"1"`.

#### OS X
Add the entry `PlayerDebugMode` of type `"string"` with value set to `1` in the plist file `/Users/<username>/Library/Preferences/com.adobe.CSXS.6.plist`

### Commands

To build and install to Animate CC directly, run the script. This will copy the plugin and then install in the CEP extension's folder (`/Library/Application Support/Adobe/CEP/extensions/com.jibo.PixiAnimate/`)

```bash
gulp --install
```

To build the extension in debug mode and allow for remote debugging, run this command. Navigate to http://localhost:8008 to get the DevTools for the Publish Settings dialog.

```bash
gulp --debug --install
```

To rebuild the C++ code on the current platform, use the `--plugin` flag. This will build the plugin for both debug and release.

```bash
gulp --debug --install --plugin
```

Or to ONLY build the plugin without building the rest of the extension.

```bash
gulp plugin
```
