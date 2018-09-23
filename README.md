# imgurbash2
imgurbash2 is a simple bash script that allows you to upload images to
[imgur](https://imgur.com/). Once an image is uploaded, the link is displayed on the
terminal and copied to your clipboard (see below).

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

To upload the image named cow.png to imgur:
```bash
imgurbash2 cow.png fish.png
```

The above command will output something like this:
```bash
http://i.imgur.com/HDVh123.png (Delete Hash = mo02q3r)
http://i.imgur.com/QCfh256.png (Delete Hash = blub1qx)
```

The first link is the URL of the uploaded image. This URL is copied to you clipboard
and hence you can use <kbd>CTRL</kbd>+<kbd>V</kbd> to paste it (provided that `xsel`
or `xclip` is installed on Linux - no separate program is required for macOS).

### Upload image to your album

Upload the image named cow.png to your imgur album:
```bash
imgurbash2 -l -a abc134 cow.png
```

### Delete images
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

### Manual
More examaples and a detailed manual is available at https://github.com/ram-on/imgurbash2/blob/master/examples.md.


## Installation
### Linux / macOS / UN*X
```bash
curl -O https://raw.githubusercontent.com/ram-on/imgurbash2/master/imgurbash2
chmod u+x imgurbash2
```

### Arch Linux / Manjaro / Antergos
```bash
yaourt -S imgurbash2
```

## Dependencies
| Program            | Optional | Reason |
| ------------------ | -------- | ------------- |
| `curl`             | No       | Uploads images  |
| `xsel` or `xclip`  | Yes      | Copies URL (image) link to clipboard if using Linux - no separate program is required for macOS |


## License
[MIT License](https://raw.githubusercontent.com/ram-on/imgurbash2/master/LICENSE)
