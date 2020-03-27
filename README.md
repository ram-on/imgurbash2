# imgurbash2
imgurbash2 is a simple bash script that allows you to upload images to
[imgur](https://imgur.com/). Once an image is uploaded, the link is displayed on the
terminal and copied to your clipboard (see below or refer to the [manual](https://github.com/ram-on/imgurbash2/blob/master/examples.md)).

Tested on Linux, macOS and FreeBSD.

## Features
* Upload remote HTTP/HTTPS images to imgur.
* Upload multiple images at one go.
* Upload images to your album and to your account.
* Delete previously uploaded images.
* Automatically images deletion.
* Copy uploaded images' URLs to clipboard.

## Usage
### Upload Images

Upload the images named cow.png and fish.jpg to imgur:
```bash
imgurbash2 cow.png https://myserver.io/fish.jpg
```

The above command will output something like this:
```bash
http://i.imgur.com/HDVh123.png (Delete Hash = mo02q3r)
http://i.imgur.com/QCfh256.png (Delete Hash = blub1qx)
```

The outputted links are the URLs of the uploaded images. Such URLs are copied to
your clipboard if the right programs are installed.

### Upload To Your Album

Upload the image named cow.png to your imgur album:
```bash
imgurbash2 -l -a abc134 cow.png
```

### Delete Images
```bash
imgurbash2 ~/tmp/test.png
http://i.imgur.com/HDVh123.png (Delete Hash = vgdTM62vQ08xaxa)
```

To delete the above uploaded image:
```bash
imgurbash2 -d vgdTM62vQ08xaxa
```

### Automatically Image Deletion
```bash
imgurbash2 -D 5m ~/tmp/test.png
```

Uploaded image will automatically be deleted after 5 minutes.


## Manual
More examaples and a detailed manual is available at https://github.com/ram-on/imgurbash2/blob/master/examples.md.
Details about the configuration file are also explained.


## Installation
### Linux / macOS / UN*X
```bash
curl -O https://raw.githubusercontent.com/ram-on/imgurbash2/master/imgurbash2
chmod u+x imgurbash2
```

### Arch Linux / Manjaro / Antergos
```bash
yay -S imgurbash2
```

## Dependencies
| Program                      | Optional | Reason |
| ---------------------------- | -------- | ------------- |
| `bash` 4.0+                  | No       | To run this script.  Given that macOS ships with an old Bash version, it is recommended that the latest Bash is installed via `brew install bash`  |
| `curl`                       | No       | Uploads images  |
| `xsel`, `xclip` or `wl-copy` | Yes      | Copies URL (image) link to clipboard if using Linux - no separate program is required for macOS |


## License
[MIT License](https://raw.githubusercontent.com/ram-on/imgurbash2/master/LICENSE)
