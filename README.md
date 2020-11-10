## # 视频和音频API

- https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/Client-side_web_APIs/Video_and_audio_APIs

## # 项目结构

- │index.html -- html结构
  │script.js -- js文件
  │style.css -- css样式
  	│--progress.css----滑动控件css样式
  	│--style.css----html结构css样式
  │image -- 背景图片
  │videos -- 视频文件

## # 引入字体图标

```html
<!-- 引入字体图标 -->
    <link href="https://stackpath.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css" rel="stylesheet"
   integrity="sha384wvfXpqpZZVQGK6TAh5PVlGOfQNHSoD2xbE+QkPxCAFlNEevoEH3Sl0sibVcOQVnN" crossorigin="anonymous" />
```

## # <video> poster 属性

- 带有预览图的视频播放器

```html
<video src="videos/Marvel-Comics.mp4" id="video" class="screen" poster="image/漫威电影十周年合照.jpg"></video>
```

## # Input Range 对象

- Input Range 对象是 HTML5 中的新对象，表示 HTML <input type="range"> 元素

```html
<!-- 进度条 -->
<input type="range" id="progress" class="progress" min="0" max="100" step="0.1" value="0">
```

- min：设置或返回滑块控件的 min 属性值。
- max：设置或返回滑块控件的 max 属性值。
- step：设置或返回滑块控件的 step 属性值。
- value：设置或返回滑块控件的 value 属性值。

## # @media 查询

```javascript
@media(max-width: 800px) {
    .screen,
    .controls{
        width: 90%;
    }
}
```

- max-width：定义输出设备中的页面最大可见区域宽度。

## # 点击播放或者暂停

```javascript
// 点击播放或者暂停
function toggleVideoStatus(){
    if (video.paused) {
        video.play();
    } else {
        video.pause();
    }
}
```

## # 点击video图标更新

```javascript
// 点击video图标更新
function updatePlayIcon(){
    if (video.paused) {
        play.innerHTML = '<i class=" fa fa-play fa-2x"></i>'
    } else {
        play.innerHTML = '<i class=" fa fa-pause fa-2x"></i>'
    }
}
```

## # 点击video更新进度条和时间戳

```javascript
// 点击video更新进度条和时间戳
function updateProgress(){
    progress.value = (video.currentTime / video.duration) * 100;
    // 获取分钟数
    let mins = Math.floor(video.currentTime / 60);
    if (mins < 10) {
        mins = "0" +String(mins);
    }
    // 获取秒数
    let secs = Math.floor(video.currentTime % 60);
    if (secs < 10 ) {
        secs = "0" +String(secs);
    }

    timestamp.innerHTML = `${mins}:${secs}`;
}
```

## # 停止并还原视频

```javascript
// 停止还原视频
function stopVideo(){
    video.currentTime = 0;
    video.pause();
}
```

## # 拖动进度条改变播放内容和时间戳

```javascript
// 拖动进度条改变播放内容和时间戳
function setVideoProgress(){
    video.currentTime = +progress.value * video.duration / 100
}
```

