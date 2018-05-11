# 视频相关的坑

##  微信中处理

### 1.1 内联 去掉控制条

``` html
<video id="inline-video" 
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

### 1.2 自动播放 & 预加载 

``` js
   // 在该事件里 play pause一下 视频会处于加载状态 相当于预加载了
  document.addEventListener("WeixinJSBridgeReady", function (){ 
    video.play(); 
    if(!video.hasAttribute('autoplay')) {
      video.pause();
    }
  }, false);
```

### 1.3 黑屏 & 判断视频是否加载

``` js
  video.addEventListener('timeupdate', function (){
      // 当视频的currentTime大于0.1时表示黑屏时间已过，已有视频画面，可以移除loading等遮盖元素
      if ( !video.isPlayed && video.currentTime > 0.1 ){
          video.isPlayed = true; 
          // 这里做处理 隐藏loading等元素
      }
  });
```

### 1.4 监听播放结束事件

``` js
  video.addEventListener('ended', function (){      
    // 结束
  }); 
```

### 1.5 监听播放暂停事件

``` js
  video.addEventListener('pause', function (){      
    // 暂停
  });
```