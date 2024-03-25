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

Once you have SSH setup, it only takes a single command to copy files to your Paperspace Machine's Shared Drive. However, you need to modify it first. This command should be run in your local terminal (while not connected via SSH to your machine).

```
scp -i ~/.ssh/my-key.pem ~/path/to/local_file paperspace@machine-ip-address:~/.
```

To use this command, replace ```my-key``` with the name of the SSH key you created to connect to your machine (don’t forget the ```.pem```).

Next, replace ```~/path/to/local_file``` with the local file on your Paperspace Machine. Remember that ```~``` is short hand for your home directory, so if you wanted to upload a data set in your Documents folder you would type something like: ```~/Documents/my-data-set.csv```.

In our case, we want to copy over the content of a whole folder ```movie-digital-twin``` into the folder with the same name ```movie-digital-twin``` inside the Paperspace Machine's Shared Drive.

After that, replace ```machine-ip-address``` with the IP address listed for your Paperspace Machine's Shared Drive in the console.

Optionally, you can also replace the ```~/.``` with whatever path you would like to copy the data to on your machine. If you leave it as is, it is copied into your home directory on the machine. In our case we want to copy it directly to the folder ```movie-digital-twin``` on the Paperspace Shared Drive, hence ```/movie-digital-twin```.

**NOTE**: A more efficient copy protocol is **Remote Sync (rsync)**. It copies over only what has changed between the tow locations, thus preventing costly copying over of files that have not changed since the previous copying. This saves time and resources. See [How To Use Rsync to Sync Local and Remote Directories](https://www.digitalocean.com/community/tutorials/how-to-use-rsync-to-sync-local-and-remote-directories). 

Consider using the macOS Graphical User Interface for RSync: [RsyncOSX](https://github.com/rsyncOSX/RsyncOSX). See also [Rsync Server](http://bonhardcomputing.com/rsync-server/) and [Rsync Server in the Apple Store](https://apps.apple.com/id/app/rsync-server-basic-edition/id1255146085), which may be dated.

## In addition, Copy results from your machine back to your local machine

See [Copy results from your machine back to your local machine](https://docs.digitalocean.com/products/paperspace/machines/how-to/transfer-data/).

Copying files back to your local machine is nearly the same as before. However, you have to flip the local and remote paths.

```
scp -i ~/.ssh/my-key.pem ubuntu@machine-ip-address:~/results.ckpt .
```

You still need to update the ```my-key.pem``` as well as the ```machine-ip-address``` with your own. This time you specify the remote file you would like to copy for example, ```~/results.ckpt``` and then tell scp where to send it for example, ```.``` (```.``` being the current directory).

Again, using **rsync** is a more efficient protocol.

An example of wanting to copy files from the Paperspace Machine or Shared Drive back to your workstation could be to collect the rendered movie, created by the Adobe After Effect Render Engine.