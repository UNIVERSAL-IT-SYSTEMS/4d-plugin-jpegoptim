# 4d-plugin-jpegoptim
Reduce size of JPG.

Based on [jpegoptim 1.4.3](https://github.com/tjko/jpegoptim).

Note: You can also change the compression of JPEG with [CONVERT PICTURE](http://doc.4d.com/4Dv15/4D/15.1/CONVERT-PICTURE.301-2686255.en.html). IF the image itself is too large for its frame, you might want to scale, crop or transform it with [TRANSFORM PICTURE](http://doc.4d.com/4Dv15/4D/15.1/TRANSFORM-PICTURE.301-2686256.en.html).

##Platform

| carbon | cocoa | win32 | win64 |
|:------:|:-----:|:---------:|:---------:|
|🆗|🆗|🆗|🆗|

##Commands

```c
Jpegoptim
```

##Examples

```
  //read jpeg file
$path:=Get 4D folder(Current resources folder)+"image.jpg"
READ PICTURE FILE($path;$image)
  //by default, all are stripped
$strip:=JPEG_STRIP_COM | JPEG_STRIP_EXIF | JPEG_STRIP_ICC | JPEG_STRIP_IPTC | JPEG_STRIP_XMP
  //0:lossless optimisation. 1...100:lossy optimisation
$quality:=0

$folderPath:=System folder(Desktop)+Generate UUID+Folder separator
CREATE FOLDER($folderPath;*)

For ($quality;0;100)
$jpeg:=Jpegoptim ($image;$strip;$quality)
WRITE PICTURE FILE($folderPath+String($quality)+".jpg";$jpeg)
End for 
```

##Discussion

4D pictures can contain multiple formats. The plugin first searches for .jpeg format. If found, "meta" information is stripped as instructed. If quality is specified, a lossy conversion is applied too.
