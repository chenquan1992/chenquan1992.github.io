---
layout: post_one
title: 直播
categories: 其他技术
description: 直播
keywords: 直播
---

***酒逢知己饮，诗向会人吟。相识满天下，知心能几人？***

1. 不管是花椒、还是虎牙或者其他的直播网站，都有一个直播的源地址是可以在前端页面找到的  
比如：虎牙的地址就有  
```javascript
var flvUrl = "https://txdirect.flv.huya.com/huyalive/20118320-2616989698-11239885166878916608-3273716274-10057-A-0-1.flv?wsSecret=30e70b240b0ae194f9b932907fbb7f2a&wsTime=5da19715&&sphdcdn=al_7-tx_3-js_3-ws_7-bd_2-hw_2&sphdDC=huya&sphd=264_*&fs=gctex&u=417481448697&t=100&sv=1910112100";  
var flvUrl = "https://1grhdgmtigazdnptafaauyco.ourdvsss.com/ws4.stream.huya.com/huyalive/9999991206518181-1206518181-2564-2413159818-66-A-26281708601-1.flv?wsSecret=c5de03b5e4175e753ac1c51e2f18341b&wsTime=5da19230&fs=bgct&u=306390712997&t=100&sv=1910112100";  
var flvUrl = "https://aldirect.flv.huya.com/backsrc/20118320-2616989698-11239885166878916608-3273716274-10057-A-0-1.flv?wsSecret=30e70b240b0ae194f9b932907fbb7f2a&wsTime=5da19715&&sphdcdn=al_7-tx_3-js_3-ws_7-bd_2-hw_2&sphdDC=huya&sphd=264_*&fs=gctex&u=417481448697&t=100&sv=1910112100";  
```
只要细心的去找就能发现，或者使用 fiddler 的抓包软件去获取播放的源地址  
这样做的目的是实现在虎牙上做直播，然后再自己的网站上可以看到视频  
毕竟直播的带宽价格太高了

```html
<!-- 播放直播源的代码-->
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
    // var flvUrl = "http://al2-flv.live.huajiao.com/live_huajiao_v2/_LC_AL2_non_20327561715708543191016488_OX.flv";
    // var flvUrl = "https://aldirect.flv.huya.com/backsrc/20118320-2616989698-11239885166878916608-3273716274-10057-A-0-1.flv?wsSecret=30e70b240b0ae194f9b932907fbb7f2a&wsTime=5da19715&&sphdcdn=al_7-tx_3-js_3-ws_7-bd_2-hw_2&sphdDC=huya&sphd=264_*&fs=gctex&u=417481448697&t=100&sv=1910112100";
    // var flvUrl = "https://1grhdgmtigazdnptafaauyco.ourdvsss.com/ws4.stream.huya.com/huyalive/9999991206518181-1206518181-2564-2413159818-66-A-26281708601-1.flv?wsSecret=c5de03b5e4175e753ac1c51e2f18341b&wsTime=5da19230&fs=bgct&u=306390712997&t=100&sv=1910112100";
    var flvUrl = "https://txdirect.flv.huya.com/huyalive/20118320-2616989698-11239885166878916608-3273716274-10057-A-0-1.flv?wsSecret=30e70b240b0ae194f9b932907fbb7f2a&wsTime=5da19715&&sphdcdn=al_7-tx_3-js_3-ws_7-bd_2-hw_2&sphdDC=huya&sphd=264_*&fs=gctex&u=417481448697&t=100&sv=1910112100";
    // var flvUrl = "http://wm.video.huajiao.com/vod-wm-huajiao-bj/223723225_4-1570554616-5b1fb084-8e3f-8567.mp4";
    // http://qh2-flv.live.huajiao.com/live_huajiao_v2/_LC_QH1_non_h265_SD_7737332015706923881545172_OX.flv
    // play_url=http://al2-flv.live.huajiao.com/live_huajiao_v2/_LC_AL2_non_20327561715708543191016488_OX.flv

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


