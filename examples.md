# Examples

## Upload Images

### Upload Local Images

To upload the image named cow.png to imgur:
```bash
imgurbash2 cow.png
```
The above command will output something like this:
```bash
http://i.imgur.com/HDVh123.png (Delete Hash = wef2q3r)

```
The first link is the URL of the uploaded image. This URL is copied to you clipboard
and hence you can use <kbd>CTRL</kbd>+<kbd>V</kbd> to paste it (provided that `xsel`
or `xclip` is installed on Linux - no separate program is required for macOS).


### Upload Remote Images

It is also possible to upload remote images (HTTP/HTTPS) to imgur.  The following command
will upload a remote image fish.png and (local image) lion.png
```bash
imgurbash2  https://myserver.org/fish.png  ~/lion.png
```


### Upload to Album

To upload the image named cow.png to imgur album:
```bash
imgurbash2 -l true -a abc134 raven.png
```

The image will be uploaded to your album whose ID is `abc134`.




## Delete images
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

**NOTE**:  The deletion will be executed by backgrounded shell process,
which means it assumes your computer won't be halted/suspended
before the time has passed, and you still have external connection
in order to call imgur api.
