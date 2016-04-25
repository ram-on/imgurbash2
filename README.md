# imgurbash2
imgurbash2 is a simple bash script that allows you to upload images to [imgur](https://imgur.com/).  Once an image is uploaded, the link is displayed on the terminal and copied to your clipboard (see below).

This script can delete previously uploaded images.

## Usage
### Upload Local Images

To upload the image named cow.png to imgur:
```bash
imgurbash2 cow.png
```
The above command will output something like this:
```bash
http://i.imgur.com/HDVh123.png    (Delete Hash = vgdTM62vQ08xaxa)
```
The first link is the URL of the uploaded image.  This URL is copied to you clipboard and hence you can use <kbd>CTRL</kbd>+<kbd>V</kbd> to paste it (provided that `xsel` or `xclip` is installed).

### Upload Remote Images

It is also possible to upload remote images (HTTP/HTTPS) to imgur:
```bash
# Upload the remote image fish.png and (local image) lion.png
imgurbash2  https://myserver.org/fish.png  ~/lion.png
```

### Delete images
```bash
imgurbash2 ~/tmp/test.png
http://i.imgur.com/HDVhl23.png    (Delete Hash = vgdTM62vQ08xaxa)
```

To delete the above uploaded image:
```bash
imgurbash2 -d vgdTM62vQ08xaxa
```

## Installation
### Linux / UN*X
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
| `xsel` or `xclip`  | Yes      | Copies URL (image) link to clipboard |

## License
[MIT License](https://raw.githubusercontent.com/ram-on/imgurbash2/master/LICENSE)
