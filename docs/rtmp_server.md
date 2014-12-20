# RTMP SERVER


[http://redstarofsleep.iteye.com/blog/2123752](http://redstarofsleep.iteye.com/blog/2123752)

```
ffmpeg -re -i "/home/badpoet/hello.mp4" -vcodec libx264 -vprofile baseline -acodec aac  -ar 44100 -strict -2 -ac 1 -f flv -s 1280x720 -q 10 rtmp://166.111.206.70:1935/myapp/test1
```

视频路径随便改

要改推到的rtmp的路径，需要配套改`/etc/nginx/site-enabled/rtmp`中的内容

然后浏览器打开`rtmp://166.111.206.70:1935/myapp/test1`即可