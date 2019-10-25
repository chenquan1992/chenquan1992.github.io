---
layout: post
title: html 播放直播源(flv,m3u8)
categories: Vue
description: html 播放直播源(flv,m3u8)
keywords: html 播放直播源(flv,m3u8)
---

***逢人且说三分话，未可全抛一片心。有意栽花花不发，无心插柳柳成荫。***

1、html 播放 flv 
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>video</title>
    <!-- Video.js -->
    <link href="https://unpkg.com/video.js/dist/video-js.css" rel="stylesheet">
    <script src="https://unpkg.com/video.js/dist/video.min.js"></script>
    <script src="https://unpkg.com/flv.js/dist/flv.min.js"></script>
    <script src="https://unpkg.com/videojs-flvjs/dist/videojs-flvjs.min.js"></script>
</head>

<body>
<div>
    <video id="videojs-flvjs-player" class="video-js vjs-default-skin vjs-big-play-centered"  width="1024" height="768"> </video>
</div>
</body>

</html>
<script>
    // 直播源
    var flvUrl = "http://wm.video.huajiao.com/vod-wm-huajiao-bj/223723225_4-1570554616-5b1fb084-8e3f-8567.mp4";

    var player = videojs('videojs-flvjs-player', {
        techOrder: ['html5', 'flvjs'],
        flvjs: {
            mediaDataSource: {
                isLive: false,
                cors: true,
                withCredentials: false,
            },
        },
        sources: [{
            src: flvUrl,
            type: 'video/mp4'
        }],
        controls: true,
        preload: "none"
    }, function onPlayerReady() {
        console.log('player ready')

        player.on('error', (err) => {
            console.log('first source load fail')

            player.src({
                src: flvUrl,
                type: 'video/x-flv'
            });

        player.ready(function() {
            console.log('player ready')
            player.load();
            player.play();
        });
    })
    });
</script>

```

2、html 播放 m3u8
```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <title>前端播放m3u8格式视频</title>
    <!--https://www.bootcdn.cn/video.js/-->
    <link href="https://cdn.bootcss.com/video.js/7.6.5/alt/video-js-cdn.min.css" rel="stylesheet">
    <script src="https://cdn.bootcss.com/video.js/6.6.2/video.js"></script>
    <!--https://www.bootcdn.cn/videojs-contrib-hls/-->
    <script src="https://cdn.bootcss.com/videojs-contrib-hls/5.15.0/videojs-contrib-hls.min.js"></script>
</head>
<body>
<video id="myVideo" class="video-js vjs-default-skin vjs-big-play-centered" controls preload="auto" width="1080" height="708" data-setup='{}'>
    <!--<source id="source" src="http://proxy.hls.yy.com/livesystem/15013_xv_64316154_64316154_0_0_0-15013_xa_64316154_64316154_0_0_0.m3u8?org=yyweb&uuid=f1223c4895364d9d8ec5f39361e2e1bf&t=1571968929&tk=54e0046f5498d3f250eb47e7d2a126f3"  type="application/x-mpegURL">-->
    <source id="source" src="http://ivi.bupt.edu.cn/hls/cctv1hd.m3u8"  type="application/x-mpegURL">

</video>
</body>
<script>
    // videojs 简单使用
    var myVideo = videojs('myVideo',{
        bigPlayButton : true,
        textTrackDisplay : false,
        posterImage: false,
        errorDisplay : false,
    })
    myVideo.play() // 视频播放
    myVideo.pause() // 视频暂停
</script>
</html>

```
