# thunar-folder-thumbnailer
Modified version of folder thumbnailer script for thunar from archlinux tumbler-extra-thumbnailers package

I could not find an official repo for this script so. I created mine. 

This modification will look for thumbnails additionaly in:

```sh
...
# Check is there some custom file thumbnail in $XDG_CACHE_HOME/.thumbnails/custom/
if [[ -n "$XDG_CACHE_HOME" ]]; then
    CUSTOM_DIR="$XDG_CACHE_HOME/thumbnails/custom"
else
    CUSTOM_DIR="$HOME/.cache/thumbnails/custom"
fi
...
```

## Usage
(Assuming you're on archlinux and allready have tumbler-extra-thumbnailers package installed)

Replace /usr/bin/folder-thumbnailer with the script in this repo.

Now you dont have to put folder.png or .folder.png inside of the directory to make a custom folder thumbnail in thunar, instead:
Run:

```sh
echo -n <input_directory> | md5sum | awk '{print $1}'
```

> [!IMPORTANT]  
>  <input_directory> must be absolute path, otherwise it wont work.
 
and than move your thumbnail picture in "$HOME/.cache/thumbnails/custom" and name it with generated by previous command hash.

Voila! Now you dont have to put annoing folder.png in the directory to get custom thumbnail. 
