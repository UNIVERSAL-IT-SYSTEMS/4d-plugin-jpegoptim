# 4d-plugin-jpegoptim
Reduce size of JPG.

Based on [jpegoptim 1.4.3](https://github.com/tjko/jpegoptim)

Example
---
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
