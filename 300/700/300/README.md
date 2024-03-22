# 300 - Step 3 – Launch Nexrender Worker

Visit the [GitHub Releases](https://github.com/inlife/nexrender/releases) page of Nexrender.

Choose a binary for your platform (Windows or macOS) for the Nexrender worker. It should match the platform of your Paperspace Machine (here: Windows).

Download the Nexrender Worker (here: nexrender-worker-win64.exe) to your Paperspace machine.

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




MORE ...

