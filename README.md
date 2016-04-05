# imgurbash2
imgurbash2 is a simple script that allows you to upload images to [imgur](https://imgur.com/) using bash.  Once an image is uploaded, the link is displayed on the terminal and copied to your clipboard (see below).

## Usage
```
# upload cow.png to imgur
imgurbash2 cow.png

# upload cow.png and bee.jpg to imgur
imgurbash2 cow.png bee.jpg

# upload the remote image fish.png and lion.png to imgur
imgurbash2 https://myserver.org/fish.png lion.png
```

## Installation
### Linux / UN*X
```
curl https://raw.githubusercontent.com/ram-on/imgurbash2/master/imgurbash2 > imgurbash2
chmod u+x imgurbash2
```

### Arch Linux / Manjaro / Antergos
```
yaourt -S imgurbash2
```

## Dependencies
| Program            | Optional | Reason |
| ------------------ | -------- | ------------- |
| `curl`             | No       | Uploads images  |
| `xsel` or `xclip`  | Yes      | Copies URL (image) link to clipboard |

## License
[MIT License](https://raw.githubusercontent.com/ram-on/imgurbash2/master/LICENSE)
