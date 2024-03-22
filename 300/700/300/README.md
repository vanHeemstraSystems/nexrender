# 300 - Step 3 – Launch Nexrender Worker

Visit the [GitHub Releases](https://github.com/inlife/nexrender/releases) page of Nexrender.

Choose a binary for your platform (Windows or macOS) for the Nexrender worker. It should match the platform of your Paperspace Machine (here: Windows).

Download the Nexrender Worker (here: nexrender-worker-win64.exe) to your Paperspace machine.

![nexrender-downloads-win64](https://github.com/vanHeemstraSystems/nexrender/assets/1499433/9d4e864c-5b1b-452d-835d-2dab15df9f01)

Move the downloaded Nexrender Worker to the ```Program Files``` folder, into a (newly created) subfolder called ```Nexrender``` for ease of use:

![nexrender-executables-win64](https://github.com/vanHeemstraSystems/nexrender/assets/1499433/05bd4cd2-e53f-4d1a-a589-2f4b9904f441)

From the [Documentation](https://github.com/inlife/nexrender?tab=readme-ov-file#nexrender-worker):

**nexrender-worker**

**Description:**

A CLI application which is responsible mainly for actual job processing and rendering, communication with the nexrender-server, and serves mainly as a consumer in the nexrender network model.

**Supported platforms:**
Windows, macOS

**Requirements:**
Installed licensed/trial version of Adobe After Effects

Example:

```
$ nexrender-worker \
        --host=https://my.server.com:3050 \
        --secret=myapisecret
```

**Note**: its recommended to run nexrender-worker -h at least once, to read all useful information about available options.

More info: [@nexrender/worker](https://github.com/inlife/nexrender/blob/master/packages/nexrender-worker)

Make sure to install Adobe After Effects Engine on your Paperspace Machine before continuing, as the Nexrender Worker needs it as a reference.

Log in to [Adobe](https://commerce.adobe.com/store) with your Adobe Account and download [Adobe After Effects](![nexrender-executables-win64](https://github.com/vanHeemstraSystems/nexrender/assets/1499433/05bd4cd2-e53f-4d1a-a589-2f4b9904f441)) to your Paperspace Machine and install it as a Render Engine. **NOTE**: Make sure to download and install the same Adobe After Effects version as the version you are editing with! You don't need an additional license, as this will be used for rendering only.

**[Installing a render-only instance of Adobe After Effects CC](https://helpx.adobe.com/nl/after-effects/using/setup-installation.html)**

In addition to the full version of Adobe After Effects, you can also install additional copies on additional computers to use as After Effects render engines to assist with network rendering. 

Before you start:

If you have installed Creative Cloud applications on two computers, sign out of one of them by opening any of the applications and choosing Sign Out from the Help menu.

You can sign back into Creative Cloud on this computer after the render-only instances of After Effects are installed.

To install a render-only instance of After Effects CC, do the following:

1. Go to the product page to download and install After Effects CC.
2. When the installation is complete, start After Effects.
3. Choose Sign Out from the Help menu.
4. Quit After Effects.
5. Create and place the ae_render_only_node.txt file as described in this [blog post](https://blogs.adobe.com/aftereffects/2012/06/codecs-and-the-render-engine-in-after-effects-cs6.html).

RUN AERENDER IN NON-ROYALTY BEARING MODE

After Effects CS5.5 had to be serialized on render-only machines due to licensing issues. In After Effects CS6 and later, you can now run aerender or use Watch Folder in a non-royalty bearing mode, so serialization not required.

To ensure that After Effects is running in non-royalty bearing mode, place a blank file named **ae_render_only_node.txt** into the following location:

Install After Effects on the render-only machine.

Mac locations:

/Users/<username>/Documents/

/Users/Shared/Adobe/

Windows locations:

C:\Users\<username>\Documents

C:\Users\Public\Documents\Adobe

![ae_render_only_node_txt_001](https://github.com/vanHeemstraSystems/nexrender/assets/1499433/ebb6ae1c-20ba-4460-825a-a6233761e7b2)

![ae_render_only_node_txt_002](https://github.com/vanHeemstraSystems/nexrender/assets/1499433/25582c86-7b73-4948-844b-51103b4d317b)

Limitations of the trial version

The trial version of After Effects includes all of the codecs that are included with the full version of After Effects. This means that you can import and export to all of the supported file formats using the trial version. 

The trial version of After Effects also includes the Keylight plug-in, mocha-AE, mocha shape, Cycore (CC) effects, and Color Finesse. 

If your installation of After Effects is missing some third-party components, contact your system administrator to ensure that all licensed components have been installed correctly.
