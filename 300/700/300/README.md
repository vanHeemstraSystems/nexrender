# 300 - Step 3 – Launch Nexrender Server and Worker

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

![nexrender-worker_help_001](https://github.com/vanHeemstraSystems/nexrender/assets/1499433/72bd7d66-8de0-4c5b-88b9-4835bd31e80c)

![nexrender-worker_help_002](https://github.com/vanHeemstraSystems/nexrender/assets/1499433/f5c07071-d305-46d1-845e-4b43ab09a3d4)

![nexrender-worker_help_003](https://github.com/vanHeemstraSystems/nexrender/assets/1499433/4b8a3134-9292-4679-8626-5e639edcbc4a)

Make sure to install Adobe After Effects Engine on your Paperspace Machine before continuing, as the Nexrender Worker needs it as a reference.

Log in to [Adobe](https://commerce.adobe.com/store) with your Adobe Account and download [Adobe After Effects](![nexrender-executables-win64](https://github.com/vanHeemstraSystems/nexrender/assets/1499433/05bd4cd2-e53f-4d1a-a589-2f4b9904f441)) to your Paperspace Machine and install it as a Render Engine. **NOTE**: Make sure to download and install the same Adobe After Effects version as the version you are editing with! You don't need an additional license, as this will be used for rendering only.

**NOTE**: If you get a warning that JavaScript is disabled in your Webbrowser (on Windows) and therefor the installation of Adobe After Effects is halted, reduce the level of Security from your Windows settings (from High to Medium), to be set to High again after a successful installation of After Effects. Changing JavaScript enabling in the browser won't help. See [CC Installer: JavaScript is disabled. Please enable JavaScript and try to sign in again.](https://community.adobe.com/t5/download-install-discussions/cc-installer-javascript-is-disabled-please-enable-javascript-and-try-to-sign-in-again/td-p/10674497).

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

Back to nexrender-worker.

From a command line on the Paperspace machine execute the following command to start the nexrender worker:

```
cd C:\Program Files\Nexrender
nexrender-worker-win64 \
        --host=https://my.server.com:3050 \
        --secret=myapisecret
```

Where **my.server.com** should be replaced by the **hostname** or **IP address** of the Paperspace machine (here: psgsjni6wn1p or 10.12.107.2), see https://console.paperspace.com/teu1osqtk/machines/psgsjni6wn1p/details .

![nexrender-worker_inside_program_files](https://github.com/vanHeemstraSystems/nexrender/assets/1499433/2e99d653-82ac-4e23-9753-c8aecbc14ef4)

Follow the advice given above; please run nexrender with Administrator Privileges only ONE TIME, to install the patch.

Right-click on C:\program Files\Nexrender\nexrender-worker-win64.exe and choose "Run as Administrator".

![nexrender-worker_inside_program_files_patch](https://github.com/vanHeemstraSystems/nexrender/assets/1499433/15a26895-8c04-417f-b775-3be360c8c40e)

Choose "Yes" in above prompt.

You may see an error: "FetchError: request to https://10.12.107.2:3050/api/v1/jobs/pickup failed, reason: connect ECONNREFUSED 10.12.107.2:3050"

Don't worry, this is because we have not yet started the Nexrender Server (which listens to port 3050 by default).

Forward to nexrender-server.

**NOTE**: We are running nexrender server on the same Paperspace machine as the nexrender-worker(s). This is not required, but limiting ourselves to one Paperspace machine saves in costs.

**nexrender-server**

Description:

A CLI application which is responsible for job management, worker node cooperation, communications with the nexrender-worker instances, serves mainly as a producer in the nexrender network model.

Technically speaking, its a very tiny HTTP server with minimal REST API support.

Optional support for external databases can be added (like Redis, MongoDB, MySQL, etc.), with some of them already in place. Please check modules for more info.

Supported platforms:<br/>
Windows, macOS, Linux

Requirements:<br/>
None

Example:<br/>

```
$ nexrender-server \
        --port=3050 \
        --secret=myapisecret
```

More info: [@nexrender/server](https://github.com/inlife/nexrender/blob/master/packages/nexrender-server)

Let's start the nexrender-server first with help:

```
cd C:\Program Files\Nexrender
nexrender-server-win64 -h
```

![nexrender-server_help_001](https://github.com/vanHeemstraSystems/nexrender/assets/1499433/707e8448-e5bc-418e-be6b-e120949187e6)

Now start the nexrender server with the chosen port and api secret configuration that matches the nexrender worker(s):

```
cd C:\Program Files\Nexrender
nexrender-server-win64 --port=3050 --secret=myapisecret
```

If not already started, restart the nexrender worker as follows (**note**: since we are running server and worker on the same machine, we can use the IP address 0.0.0.0 simply). For simplicity we use http instead of http**s**:

```
cd C:\Program Files\Nexrender
nexrender-worker-win64 --host=http://0.0.0.0:3050 --secret=myapikey
```

![nexrender-server_0000_3050_001](https://github.com/vanHeemstraSystems/nexrender/assets/1499433/480ad210-7717-45e2-8dd3-742146e7529e)

![nexrender-worker_0000_3050_001](https://github.com/vanHeemstraSystems/nexrender/assets/1499433/33979890-9c5a-4ceb-bb96-e3d16e4c1b86)

Nice!

Now if we fire an API call to our nexrender server, instructing a render job, the nexrender worker will take it from there.
