https://zhuanlan.zhihu.com/p/85895180

ffprobe -i 61.avi -v quiet -select_streams v -show_entries frame=pkt_pts_time,pict_type

# 抽取I帧
```bash
ffmpeg -i 61.avi -ss 00:00:32 -to 00:09:15 -vf "select=eq(pict_type\,I)" -vsync vfr -qscale:v 2 output/%08d.png
```

# 抽取P帧

```bash
ffmpeg -i 61.avi -vf "select=eq(pict_type\,P)" -vsync vfr -qscale:v 2 p-output/%08d.png
```

# 抽取B帧

```bash
ffmpeg -i 61.avi -vf "select=eq(pict_type\,B)" -vsync vfr -qscale:v 2 b-output/%08d.png
```



# 均匀抽帧

-r 指定抽取的帧率，即从视频中每秒钟抽取图片的数量。1代表每秒抽取一帧。
```bash
ffmpeg -i 666051400.mp4 -r 1 -q:v 2 -f image2 ./%08d.000000.jpg
```