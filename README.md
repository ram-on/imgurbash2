# imgurbash2
imgurbash2 is a simple bash script that allows you to upload images to
[imgur](https://imgur.com/). Once an image is uploaded, the link is displayed on the
terminal and copied to your clipboard (see below).

Tested on Linux and macOS.

## Features
* Upload remote HTTP/HTTPS images to imgur.
* Upload multiple images at one go.
* Upload images to specific album.
* Authenticate imgur user.
* Delete previously uploaded images.
* Automatically delete uploaded images.
* Copy uploaded images' URLs to clipboard.

## Usage
### Upload Local Images

To upload the image named cow.png to imgur:
```bash
imgurbash2 cow.png
```
The above command will output something like this:
```bash
[cow.png] uploaded: http://i.imgur.com/HDVh123.png deletehash=[wef2q3r] (https://imgur.com/delete/wef2q3r)

```
The first link is the URL of the uploaded image. This URL is copied to you clipboard
and hence you can use <kbd>CTRL</kbd>+<kbd>V</kbd> to paste it (provided that `xsel`
or `xclip` is installed on Linux - no separate program is required for macOS).

### Upload image to your album

To upload the image named cow.png to imgur album:
```bash
imgurbash2 -a abc134 cow.png
```
Image will be uploaded to album whose id is `abc134`. Note you most likely
want to enable authentication in config file (or via `--login true` option).

### Upload Remote Images

It is also possible to upload remote images (HTTP/HTTPS) to imgur:
```bash
# Upload the remote image fish.png and (local image) lion.png
imgurbash2  https://myserver.org/fish.png  ~/lion.png
```

### Delete images
```bash
imgurbash2 ~/tmp/test.png
[~/tmp/test.png] uploaded: http://i.imgur.com/HDVh123.png deletehash=[vgdTM62vQ08xaxa] (https://imgur.com/delete/vgdTM62vQ08xaxa)
```

To delete the above uploaded image:
```bash
imgurbash2 -d vgdTM62vQ08xaxa
```

### Automatically delete images after specified delay
```bash
imgurbash2 -D 5m ~/tmp/test.png
```

Uploaded image will automatically be deleted after 5 minutes.

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
| `jq`               | No       | Parses api json response  |
| `xsel` or `xclip`  | Yes      | Copies URL (image) link to clipboard if using
Linux - no separate program is required for macOS |

## License
[MIT License](https://raw.githubusercontent.com/ram-on/imgurbash2/master/LICENSE)
