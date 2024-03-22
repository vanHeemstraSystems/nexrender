# 600 - Package After Effects Project for Rendering

Based on "Share or Reuse After Effects Project Files" at https://youtu.be/dfC9gmsP9RY?t=103

In After Effects, from the ```File``` menu go down to ```Dependencies > Collect Files ...```.

In the ```Collect Files``` dialogue choose for Collect Source Files the **For All Comps** (unless you want to collect for a currently selected composition only).

Optionally choose to check the **Reduce Project** checkbox, which will collect only files that are used within the compositions (ignoring any unused files), which is recommended.

Optionally choose to check the **Reveal collected project in Finder when finished** for ease of finding the collected files afterwards. Recommended.

Lastly, click the button **Collect...**.

Now you are asked to navigate to which folder you want to save the collected files. Here we aim to save the collected files on the Shared Drive at Paperspace in the previously created folder "```movie-digital-twin```".

With the Shared Drive at Paperspace opened as a mapped network drive on your editing workstation (either Mac or Windows), choose the ```movie-digital-twin``` folder.

Click the button **Save**.

Once the process has completed succesfully, you will notice in the ```movie-digital-twin``` folder there to be three (new) items:

- A folder called (Footage)
- An After Effects project file called the name of the composition that was collected (in case of all compositions, the name of the main composition, e.g. ```digital-twin.aep```)
- A text file with the same name as the above project file + ```Report.txt```

These files are now ready for rendering.