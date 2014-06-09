LatexMacUtils
=============

Some Latex utilities for Mac which I want to share

Clean LaTeX Junk Workflow
-------------------------

This is an easy Apple Automator service which deletes all the junk files created by Latex from a folder.

### Installation:

Download the `.workflow` file and copy it into the following folder on your mac:

```
~/Library/Services
```

with `~` being your home folder. To move to this folder, click in Finder on "Go to folder" and insert the above line.

### Usage:

Just right-click on the folder containing your Latex junk files and choose `Services -> Clean LaTeX Junk`.
Voilá :)

### Contribute:

This workflow is really easy. It just whitelists some common extensions.
Feel free to edit it in the Automator app!
If you are missing any extensions, please send me a pull request to improve.

Note: I deactivated recursive folder filtering for performance purposes.
If you have junk files scattered over subfolders, consider to turn it on.