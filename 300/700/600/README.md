# 600 - Package After Effects Project for Rendering

Based on "Share or Reuse After Effects Project Files" at https://youtu.be/dfC9gmsP9RY?t=103

In After Effects, from the ```File``` menu go down to ```Dependencies > Collect Files ...```.

In the ```Collect Files``` dialogue choose for Collect Source Files the **For All Comps** (unless you want to collect for a currently selected composition only).

Optionally choose to check the **Reduce Project** checkbox, which will collect only files that are used within the compositions (ignoring any unused files), which is recommended.

Optionally choose to check the **Reveal collected project in Finder when finished** for ease of finding the collected files afterwards. Recommended.

Lastly, click the button **Collect...**.

Now you are asked to navigate to which folder you want to save the collected files. 

Choose a local directory to save the collected files to, for example a folder named ```movie-digital-twin```.

Click the button **Save**.

Once the process has completed succesfully, you will notice in the ```movie-digital-twin``` folder there to be three (new) items:

- A folder called (Footage)
- An After Effects project file called the name of the composition that was collected (in case of all compositions, the name of the main composition, e.g. ```digital-twin.aep```)
- A text file with the same name as the above project file + ```Report.txt```

These files are now ready for rendering.

Next, we'll use Secure Copy Protocol (SCP) to copy the saved collected files over from our workstation (here: macos) to our Paperspace Machine.

See also [How to Transfer Data to Paperspace](https://docs.digitalocean.com/products/paperspace/machines/how-to/transfer-data/).

Here we aim to save the collected files on the Shared Drive at Paperspace in the previously created folder "movie-digital-twin".

Secure Copy the collected file from your editing workstation (either Mac or Windows) to the Shared Drive at Paperspace, choose the movie-digital-twin folder.

Lookup the IP address and path of the Shared Drive as well as the connection credentials (username and password) from the web console's tab "Drives" at https://console.paperspace.com/teu1osqtk/drives

In order to copy files from your local laptop or desktop to your machine, you need to have [SSH setup](https://docs.digitalocean.com/products/paperspace/accounts-and-teams/add-ssh-keys/) correctly on your local machine.

![Screenshot 2024-03-26 at 14 16 19](https://github.com/vanHeemstraSystems/nexrender/assets/1499433/205d90e3-f1cf-4c47-80b5-fee0cd7268d1)

We find the file id_rsa.pub here.

Now take a copy of the **content** of above rsa_id.pub file from your local computer and add it in below [ssh-keys page](https://console.paperspace.com/account/settings/ssh-keys), after clicking "**ADD NEW SSH KEY**":

![Screenshot 2024-03-26 at 14 34 52](https://github.com/vanHeemstraSystems/nexrender/assets/1499433/6a1b7cfa-2365-4a37-bea1-0136eefbd792)

Next, assign a previoulsy created Public IP address (here: 184.105.188.243) on Paperspace to your Machine:

![Screenshot 2024-03-26 at 14 39 14](https://github.com/vanHeemstraSystems/nexrender/assets/1499433/8841d80e-2233-4a3d-b473-a737cedf530e)

![Screenshot 2024-03-26 at 14 39 54](https://github.com/vanHeemstraSystems/nexrender/assets/1499433/b076e981-fd25-45a5-b1b5-90b722affe58)

Once you have SSH setup, it only takes a single command to copy files to your Paperspace Machine's Shared Drive. However, you need to modify it first. This command should be run in your local terminal (while not connected via SSH to your machine).

```
scp -i ~/.ssh/my-key.pem ~/path/to/local_file paperspace@machine-ip-address:~/.
```

To use this command, replace ```my-key``` with the name of the SSH key you created to connect to your machine (don’t forget the ```.pem```).

Next, replace ```~/path/to/local_file``` with the local file on your local computer (e.g. ~/demo-file.txt). Remember that ```~``` is short hand for your home directory, so if you wanted to upload a data set in your Documents folder you would type something like: ```~/Documents/my-data-set.csv```.

In our case, we want to copy over the content of a whole folder ```movie-digital-twin``` into the folder with the same name ```movie-digital-twin``` inside the Paperspace Machine's Shared Drive.

After that, replace ```machine-ip-address``` with the (Public) IP address listed for your Paperspace Machine in the console.

Optionally, you can also replace the ```~/.``` with whatever path you would like to copy the data to on your Paperspace Machine. If you leave it as is, it is copied into your home directory on the machine. In our case we want to copy it directly to the folder ```movie-digital-twin``` on the Paperspace Shared Drive, hence ```/movie-digital-twin```.

Hence, our command becomes (where 184.105.188.243 is our Pubic IP address of our Machine):

```
scp -i ~/.ssh/id_rsa.pub ~/demo-file.txt paperspace@184.105.188.243:~/.
```

**NOTE**: If you receive following warning: "ssh: connect to host 184.105.188.243 port 22: Network is unreachable" this could be due to the Firewall on the Paperspace Machine (Windows). Advise is proved at [My Adventures with Paperspace | Day 1: Connection Issues](https://kaushikmoudgalya.medium.com/my-adventures-with-paperspace-day-1-connection-issues-ff7c390b1a48).

In short: 

- **Step 1**: Head over to the Control Panel of the Paperspace Machine and open up “System and Security”.


... open the firewall for port 22 (ssh) on the Paperspace Machine.



**NOTE**: A more efficient copy protocol is **Remote Sync (rsync)**. It copies over only what has changed between the two locations, thus preventing costly copying over of files that have not changed since the previous copying. This saves time and resources. See the excellent tutorial about rsync called [How To Use Rsync to Sync Local and Remote Directories](https://www.digitalocean.com/community/tutorials/how-to-use-rsync-to-sync-local-and-remote-directories). And [rsync | The most powerful backup tool you're not using](https://www.youtube.com/watch?v=_D7sTx93gZ4).

Consider using the macOS Graphical User Interface for RSync: [RsyncOSX](https://github.com/rsyncOSX/RsyncOSX). Or look for [Truck - The RSync Client for Mac](http://bonhardcomputing.com/truck/). See also [Rsync Server](http://bonhardcomputing.com/rsync-server/) and [Rsync Server in the Apple Store](https://apps.apple.com/id/app/rsync-server-basic-edition/id1255146085), which may be dated. Or even [Acrosync for Mac](https://acrosync.com/mac.html). For rsync automation on macOS, read [rsync + Automator = free and easy backups for your Mac](https://www.practicallyefficient.com/2011/03/18/rsync-automator.html). In addition, automate the automation of rsync with [Trypa](https://apps.apple.com/us/app/trypa/id1666429734).

Until we get the connection working, we can simply drag files from our local computer onto the Paperspace App to copy them to the Paperspace Machine.

For example, we have created a sample Adobe After Effects project (called ```movie-hello-world```) and collected the files from within the File > .. > Collect Files menu in After Effects. Our composition is called **main**. There is only a solid layed in blue gradient and a text layer with the text "Hello World !". So no images or other files.

```
hello-world.aep
hello-worldReport.txt
```

By dragging them onto the Paperspace App and moving them to the shared drive (z:), they are now inside the ```hello-world``` folder:

![hello-world-collected-files-on-shared-drive](https://github.com/vanHeemstraSystems/nexrender/assets/1499433/e0723c44-21a6-492d-8a1a-12170d6c959a)

Here depicted inside the browser, but dragged across with the Paperspace App.

We will be using the nexrender-cli-win64 executable to start e render process for the hello-world project.

**Note**: on MacOS you might need to change the permissions for downloaded file ```nexrender-cli-macos```, so it would be considered as an executable. You can do it by running: ```$ chmod 755 nexrender-cli-macos```

A job is a single working unit in the nexrender ecosystem. It is a json document, that describes what should be done, and how it should be done. Minimal job description always should contain a pointer onto Adobe After Effects project, which is needed to be rendered, and a composition that will be used to render.

The pointer is the ```src``` (string) field containing a URI pointing towards specified file, followed by ```composition``` (string) field, containing the name of the composition that needs to be rendered.

**After Effects 2023 (and newer)**

Please not that for After Effects 2023, it's vital to set up an Output Module, even if you want to rely on the default output module. After Effects 2023 rendering binary (aerender) in a lot of cases will not render a composition unless it has a configured output module. Additionally, AE2023 now allows rendering directly to mp4, so consider setting up a custom value for outputExt as well:

```
{
    "template": {
        "src": "file:///z:/hello-world/hello-world.aep",
        "composition": "main",
        "outputModule": "H.264 - Match Render Settings - 15 Mbps",
        "outputExt": "mp4",
        "settingsTemplate": "Best Settings"
    }
}
```
myjob.json

![nexrender-myjob-json-hello-world-mp4](https://github.com/vanHeemstraSystems/nexrender/assets/1499433/9d7cdd74-5eb9-46cd-80e2-37946f22cd0c)

Submitting this data to the binary will result in start of the rendering process:

![nexrender-cli-win64-render-myjob-json](https://github.com/vanHeemstraSystems/nexrender/assets/1499433/268b5a99-ea24-4bf8-9844-5fea211723e8)

```
$ nexrender-cli-win64 --file C:\Users\paperspace\nexrender\myjob.json
```

**Note**: its recommended to run ```nexrender-cli-win64 -h``` at least once, to read all useful information about available options.

More info: [@nexrender/cli](https://github.com/inlife/nexrender/blob/master/packages/nexrender-cli)

![nexrender-cli-win64-render-myjob-json-002](https://github.com/vanHeemstraSystems/nexrender/assets/1499433/7029ed8f-c270-4d89-95cd-cabfef210e7a)

**WARNING**: nexrender is changing the default aerender log path to the project folder. This is done to streamline the log management and enable efficient log cleanup.

If you want to keep the older behavior and mute this message, please set the environment variable NEXRENDER_ENABLE_AELOG_LEGACY_TEMP_FOLDER to true.

If you want to switch to the new behavior, please set the environment variable NEXRENDER_ENABLE_AELOG_PROJECT_FOLDER to true.

Right now, the older behavior is still the default, but this will change in the next minor release. Estimated date of change to the new behavior: 2023-06-01.

Hence, we like to set the environment variable **NEXRENDER_ENABLE_AELOG_PROJECT_FOLDER** to **true**.

![nexrender-cli-win64-render-myjob-json-003](https://github.com/vanHeemstraSystems/nexrender/assets/1499433/887f48f8-5edb-461c-9038-c06efe3cdcf8)

Hooray, we have rendered a movie (in ~151.06 seconds)!

The rendered movie (*.mp4) can be found at: ...

## In addition, Copy results from your Paperspace machine back to your local machine

See [Copy results from your Paperspace machine back to your local machine](https://docs.digitalocean.com/products/paperspace/machines/how-to/transfer-data/).

Copying files back to your local machine is nearly the same as before. However, you have to flip the local and remote paths.

```
scp -i ~/.ssh/my-key.pem ubuntu@machine-ip-address:~/results.ckpt .
```

You still need to update the ```my-key.pem``` as well as the ```machine-ip-address``` with your own. This time you specify the remote file you would like to copy for example, ```~/results.ckpt``` and then tell scp where to send it for example, ```.``` (```.``` being the current directory).

Again, using **rsync** is a more efficient protocol.

An example of wanting to copy files from the Paperspace Machine or Shared Drive back to your workstation could be to collect the rendered movie, created by the Adobe After Effect Render Engine.
