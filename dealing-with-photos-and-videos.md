##### Bulk replace images extensions (i.e. from JPG to jpg):
```
for i in *.JPG; do mv -i ${i} ${i%}.jpg; done
```

#### Bulk resizing of images (from here):
##### Replace originals:
```
find . -name "*.jpg" -exec convert -resize 900x -quality 85% {} {} \;
```
##### Make smaller copies in another directory:
```
mkdir tmp; find . -name "*.JPG" -exec convert -resize 900x -quality 100% {} tmp/{} \;
```

#### Make a movie from a sequence of images using mencoder:
```
rm filelist.txt; ls *.JPG >> filelist.txt; mencoder "mf://@filelist.txt" -mf fps=10 -o ./output_10fps.avi -ovc lavc -lavcopts vcodec=mpeg4
```
#### To deal with artifacts resulted from a high resolution images, use one of the following commands:
##### For images with a ratio of 3/4:
```
rm filelist.txt; ls *.JPG >> filelist.txt; mencoder "mf://@filelist.txt" -mf fps=6 -vf scale=1080:810 -o ./output_6fps.avi -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=10000
```

##### For images with a ratio of 2/3:
```
rm filelist.txt; ls *.JPG >> filelist.txt; mencoder "mf://@filelist.txt" -mf fps=6 -vf scale=1080:720 -o ./output_6fps.avi -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=10000
```

##### For images with a ratio of 9/16:
```
rm filelist.txt; ls *.JPG >> filelist.txt; mencoder "mf://@filelist.txt" -mf fps=6 -vf scale=1080:608 -o ./output_6fps.avi -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=10000
```

##### Reverse order:
```
rm filelist.txt; ls -r *.JPG >> filelist.txt; mencoder "mf://@filelist.txt" -mf fps=10 -o ./output_10fps_reversed.avi -ovc lavc -lavcopts vcodec=mpeg4
```

To resize the movie add: `-vf scale=x:y`

##### Rotate a movie:
```
ffmpeg -i in.avi -vf "transpose=2" out.avi
```
Where:
* 0 = 90 Counter Clockwise and Vertical Flip (default)
* 1 = 90 Clockwise
* 2 = 90 Counter Clockwise
* 3 = 90 Clockwise and Vertical Flip
