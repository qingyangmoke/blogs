# tiny.js实战 -- 骨骼动画

## 前言

>tiny.js是一款轻量级 HTML5 2D 游戏引擎，了解更多请移步[官网](http://tinyjs.net/#/)，这里就不再做详细的介绍了
 
## 准备工作

 1. 安装 DragonBones Pro，一款免开源免费的创建骨骼动画的工具，可以直接安装使用。具体使用方法请移步[官网](http://dragonbones.com/cn/index.html)

 2. 打开默认骨骼动画的示例，导出数据和纹理 (Dragon_ske.json、Dragon_tex.json、Dragon_tex.png),使用方法请移步[官网](http://dragonbones.com/cn/index.html)

 3. 引入tiny.js核心库 

 ```js
 <script src="https://a.alipayobjects.com/g/tiny/tiny/1.0.1/tiny.js"></script>
 ```

 4. 引入tiny-plugin-dragonbones骨骼动画插件
```js
 <script src="https://a.alipayobjects.com/g/tiny-plugins/tinyjs-plugin-dragonbones/0.0.1/index.js"></script>
```

## 开始干活

1. 首先我们把刚才导出的骨骼数据和纹理资源加载进来

```js
 Tiny.Loader
    .add("dragonBonesData", "./resource/Dragon/Dragon_ske.json")
    .add("textureDataA", "./resource/Dragon/Dragon_tex.json")
    .add("textureA", "./resource/Dragon/Dragon_tex.png")
    .load(function () {
       initGame();
    });
```

2. 接下来我们初始化tiny

``` js
  var config = {
    showFPS: true, // 显示帧频
    dpi: 1, // 分辨率
    renderOptions: {
      backgroundColor: 0x2a3145 // 画布背景色
    }
  };
  // 初始化App
  var app = new Tiny.Application(config);
  // 新建场景
  var container = new Tiny.Container();
  // 启动场景
  app.run(container);

```
3. 终于到正题了，创建骨骼动画

``` js
  //设置别名
  var dragonBones = Tiny.DragonBones;
  var resources = Tiny.Loader.resources;

  /*+++++++++++ 创建骨骼动画 BEGIN +++++++++++*/

  // 取出来骨骼数据
  var dragonBonesData = resources["dragonBonesData"].data;
  // 从资源中取出来骨骼纹理数据
  var textureData = resources["textureDataA"].data;
  // 从资源中取出来骨骼纹理图片
  var texture = resources["textureA"].texture;

  // 添加骨骼数据
  dragonBones.addDragonBonesData(dragonBonesData);
  // 添加纹理
  dragonBones.addTextureAtlasData(textureData,texture);

  // 创建一个骨骼精灵 Dragon为 DragonBones Pro中定义的骨骼名字
  var armatureDisplay = dragonBones.buildArmatureDisplay('Dragon');

  // 设置精灵在场景中的位置
  armatureDisplay.x = app.renderer.width * 0.5;
  armatureDisplay.y = app.renderer.height * 0.5 + 50;
  armatureDisplay.scale.set(0.3, 0.3);

  // 播放骨骼动画 DragonBones Pro 默认生成四个动作 fall、jump、stand、walk
  var animationState = armatureDisplay.play('walk');

  // 把骨骼对象添加到场景中
  container.addChild(armatureDisplay);

  /*+++++++++++ 创建骨骼动画 END   ++++++++++++*/
}
```

4. 搞定，就是这么简单！

## 有图有真相

<img src='https://gw.alipayobjects.com/zos/rmsportal/WIzZGaviupJrsuNiaddg.gif' />


> 本实例完整代码已托管到了Github, [源码地址](https://github.com/qingyangmoke/blogs-tutorial/tree/master/tinyjs/dragonbones-1/)
