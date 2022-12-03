# Manual

## Contents

* [Examples](#examples)
	* [Upload Local Images](#upload-local-images)
	* [Upload Remote Images](#upload-remote-images)
	* [Upload Videos and Images](#upload-videos-and-images)
	* [Upload to Your Account](#upload-to-your-account)
	* [Upload to Your Album](#upload-to-your-album)
	* [Add Title To Images](#add-title-to-images)
	* [Delete Images](#delete-images)
	* [Automatic Image Deletion](#automatic-image-deletion)
* [Configuration File](#configuration-file)
* [Credentials File](#credentials-file)
* [Trivia](#trivia)

## Examples

The below examples are applicable for imgurbash2 v3.3+

### Upload Local Images

To upload the image named cow.png to imgur:
```bash
imgurbash2 cow.png
```

The above command will output something like this:
```bash
http://i.imgur.com/HDVh123.png (Delete Hash = wef2q3r)
```

The first link is the URL of the uploaded image. This URL is copied to you 
clipboard and hence you can use <kbd>CTRL</kbd>+<kbd>V</kbd> (or 
<kbd>⌘</kbd>+<kbd>V</kbd>) to paste it (provided that `xsel`, `xclip` or 
`wl-copy` is installed on Linux - no separate program is required for macOS).


### Upload Remote Images

It is also possible to upload remote images (HTTP/HTTPS) to imgur.  The following command
will upload a remote image fish.png and (local image) lion.png
```bash
imgurbash2  https://myserver.org/fish.png  ~/tmp/lion.jpg
```


### Upload Videos and Images

You can upload local/remote videos and images to imgur:
```bash
imgurbash2 cat.jpeg ~/Pictures/khajiit.mp4 http://mylameserver.lan/coins.mpeg
```

**NOTE: The below examples apply to both images and videos.**


### Upload to Your Account

You can upload an image to your accout:
```bash
imgurbash2 -l parrot.png
```

Such images are uploaded to `https://<your_username>.imgur.com/all`.  

**NOTE 1**:  The `-l` or `--login` argument is required in order to authenticate
and upload to your album.  If this is the first time running the 
`imgurbash2 -l ...` command, then you will be presented with instructions on how
to get such credentials.  Please refer to the [Credentials File](#credentials-file).

**NOTE 2**:  Please refer to the [Trivia section](#trivia) if you are getting weird errors when
executing the above command.


### Upload to Your Album

To upload the image named raven.png to your imgur album whose ID is `albumid`:
```bash
imgurbash2 -l -a albumid raven.png
```

**NOTE 1**:  Album ID can be determained by analyzing the album's URL.

To get your album ID:

1.  Go to `https://imgur.com/user/<your_username>/posts`
2.  Within the "all" section, [click on the album](https://imgur.com/LLzZqFc) where you want to upload the image.
3.  The album should be displayed and it should contain the album ID.  E.g. https://imgur.com/a/albumid, thus the album ID is "albumid".

**NOTE 2**:  The `-l` or `--login` argument is required in order to authenticate
and upload to your album.  If this is the first time running the 
`imgurbash2 -l ...` command, then you will be presented with instructions on how
to get such credentials.  Please refer to the [Credentials File](#credentials-file).

**NOTE 3**:  Please refer to the [Trivia section](#trivia) if you are getting weird errors when
executing the above command.


### Add Title To Images

You can add a title to the image you'd like to upload:
```bash
imgurbash2 -t "My Title" bird.png
```

A title can be assigned to any image uploaded to your album:
```bash
imgurbash2 -l -a albumid -t "Bird Is The Word" bird.png
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


## Credentials File

Credentials file holds your personal imgur application credentials.  It is
located at `$HOME/.config/imgurbash2/credentials.conf`.  

This file is only used when using `imgurbash2 --login ...`.  If the file does
not exist and you try to execute `imgurbash2 --login ...`, then you will 
provided with instructions on how to create credentials for this application,
after which the credentials file is created.


## Trivia

If imgurbash2 is returning errors when executing `imgurbash2 --login ...`:

1. Ensure that your imgur account's email address has been verified.
2. If you get a 403 'forbidden' error message: it is recommended that your account's email address
   is changed to a mainstream email provider (such as Gmail).
