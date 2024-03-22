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



MORE ...

