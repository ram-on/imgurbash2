# imgurbash2
imgurbash2 is a simple script that allows you to upload images to [imgur](https://imgur.com/) using bash.  Once an image is uploaded, the link is displayed on the terminal and copied to your clipboard (see below).

## Usage
```
./imgurbash2 cow.png            # uploads cow.png to imgur
./imgurbash2 cow.png bee.jpg    # uploads cow.png and bee.jpg to imgur
```

## Installation
```
curl https://raw.githubusercontent.com/ram-on/imgurbash2/master/imgurbash2 > imgurbash2
chmod u+x imgurbash2
```

## Dependencies
| Program            | Optional | Reason |
| ------------------ | -------- | ------------- |
| `curl`             | No       | To upload images  |
| `xcel` or `xclip`  | Yes      | To copy URL (image) link to clipboard |

## License
MIT License
