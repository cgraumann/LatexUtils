LatexMacUtils
=============

Some Latex utilities that ease my life which I want to share

Clean LaTeX Junk Workflow (MAC ONLY)
-------------------------

This is an easy Apple Automator service which deletes all the junk files created by Latex from a folder.

### Installation

Download the `.workflow` file and copy it into the following folder on your mac:

```
~/Library/Services
```

with `~` being your home folder. To move to this folder, click in Finder on "Go to folder" and insert the above line.

### Usage

Just right-click on the folder containing your Latex junk files and choose `Services -> Clean LaTeX Junk`.
Voilá :)

### Contribute

This workflow is really easy. It just whitelists some common extensions.
Feel free to edit it in the Automator app!
If you are missing any extensions, please send me a pull request to improve.

Note: I deactivated recursive folder filtering for performance purposes.
If you have junk files scattered over subfolders, consider to turn it on.

Clean LaTeX Junk Shellscript (MAC/LINUX)
----------------------------

You can also use a bash/shell script to remove those junk files. This has the advantage, that you can use it in your standard LaTeX editor (e.g. TexStudio) as your last build phase - resulting in always clean folders :-)

### Installation

1. Download the `cleanlatexjunk.sh` file and copy it to a folder of your choice.
2. Open Terminal and navigate to that folder.
3. Add execution rights to the file: `chmod +x cleanlatexjunk.sh`

### Usage in Terminal

Remove all junk files in *\<latexfolder>*:

```
./cleanlatexjunk.sh <latexfolder>
```

This will prompt you with a security check, which you have to acknowledge by entering `Y`, since the script will delete all files with standard latex junk extensions, regardless of their name. That could also delete other files, so be careful!

To remove only files related to a tex-file, use:

```
./cleanlatexjunk.sh -p <filename.tex> <latexfolder>
```

To avoid the security check, use the option `-f`.

### Usage in TexStudio

How to install this script as a build phase in TexStudio:

1. Open *Preferences/Build* in TexStudio
2. Select *Advanced options* at the bottom
3. Add a new user command with the name `cleanjunk`
4. As the command, enter:

	```
	"/PATH/TO/SCRIPT/cleanlatexjunk.sh" -fp ?me ?a) 
	```
	and change */PATH/TO/SCRIPT/* accordingly
5. In the meta-command for *Build & View* add 
```
 | txs:///compile | txs:///compile | txs:///cleanjunk
``` at the end

***Please note:*** The files I called "junk" in fact are necessary for the LaTeX build process. To allow the TOC and all other references to work properly, you need to perform at least one compile run with these files present. To account for this, the suggested command in step 5 above includes two additional compile runs before deletion of the files.

Now every build & view execution should result in a clean workspace :-)