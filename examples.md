# Manual

## Contents

* [Examples](#examples)
	* [Upload Local Images](#upload-local-images)
	* [Upload Remote Images](#upload-remote-images)
	* [Upload to Your Album](#upload-to-your-album)
	* [Upload to Your Account](#upload-to-your-account)
	* [Add Title To Images](#add-title-to-images)
	* [Delete Images](#delete-images)
	* [Automatic Image Deletion](#automatic-image-deletion)
* [Configuration File](#configuration-file)
* [Trivia](#trivia)

## Examples

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
imgurbash2  https://myserver.org/fish.png  ~/tmp/lion.jpg
```


### Upload to Your Album

To upload the image named raven.png to your imgur album whose ID is `xaxarqs`:
```bash
imgurbash2 -l -a xaxarqs raven.png
```

**NOTE 1**:  Album ID can be determained by analyzing the album's URL.  For example,
`https://imgur.com/a/xaxarqs` means that the ablum ID is `xaxarqs`.  Your alblums should be
avaliable at `https://<your_username>.imgur.com/`

**NOTE 2**:  The `-l` or `--login` argument is required in order to authenticate and upload to
your album.

**NOTE 3**:  Please refer to the [Trivia section](#trivia) if you are getting weird errors when
executing the above command.


### Upload to Your Account

You can upload an image to your accout:
```bash
imgurbash2 -l parrot.png
```

Such images are uploaded to `https://<your_username>.imgur.com/all`.


### Add Title To Images

You can add a title to the image you'd like to upload:
```bash
imgurbash2 -t "My Title" bird.png
```

A title can be assigned to any image uploaded to your album:
```bash
imgurbash2 -l -a xaxarqs -t "Bird Is The Word" bird.png
```


### Delete Images

Assume you've uploaded an image and the application outputed the following:

```bash
imgurbash2 dog.png
http://i.imgur.com/HDVh123.png (Delete Hash = vgdTM62vQ08xaxa)
```

To delete the above uploaded image:
```bash
imgurbash2 -d vgdTM62vQ08xaxa
```

You can mass delete previously uploaded image:
```bash
imgurbash2 -d vgdTM62vQ08xaxa VZTheonfu2i300q
```


### Automatic Image Deletion

Uploaded image will automatically be deleted after 10 minutes:

```bash
imgurbash2 -D 10m shark.png
```

Here, the uploaded image will be deleted after 5 hours:

```bash
imgurbash2 -D 5h lobster.png
```

**NOTE**:  The deletion will be executed by backgrounded shell process,
which means it assumes your computer won't be halted/suspended
before the time has passed, and you still have external connection
in order to call imgur API.



## Configuration File

Configuration file is located at `$HOME/.config/imgurbash2/config`.  The 
following variables are kept within such file:

* `COPY_URL_TO_CLIP`:  Enable/Disable clipboard URL copying.
* `DISABLE_LOGGING`:  Enable/Disable logging.  Logs are kept at `$HOME/.config/imgurbash2/log`


## Trivia

If imgurbash2 is returning errors when executing `imgurbash2 -l ...`:

1. Ensure that your imgur account's email address has been verified.
2. If you get a 403 'forbidden' error message: it is recommended that your account's email address
   is changed to a mainstream email provider (such as Gmail).
