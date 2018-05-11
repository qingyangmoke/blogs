# 视频相关的坑

## 微信中嵌入式播放

``` html
<video id="video" 
       src="XXX" 
       width="100%" 
       height="100%" 
       x5-video-player-type="h5" 
       x5-video-player-fullscreen="true" 
       x-webkit-airplay="true" 
       webkit-playsinline="true" 
       playsinline="true" 
       preload="auto"></video>
```

``` js
   // 在该事件里 play pause一下 视频会处于加载状态 相当于预加载了
  document.addEventListener("WeixinJSBridgeReady", function (){ 
    video.play();
    video.pause();
  }, false);
```