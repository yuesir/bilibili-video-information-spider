## B站视频信息(av号，播放量，弹幕数，硬币数，分享量，评论数，收藏数)爬虫</br>

    在参考 [bili-spider](https://github.com/chenjiandongx/bili-spider)的代码后，</br>
我在他的代码的基础上进行改进，并最终做出成果(已经把我的代码pull requests了)。</br>
    我的代码在服务器上跑了5天，最终跑出了1300万条视频信息，数据库文件有300M，GitHub无法上传，</br>
我就放到了百度云里：https://pan.baidu.com/s/1ggxaanL ，密码: i8mb。</br>

# 准备工作</br>
    我使用的是Python3和Python自带的sqlite数据库。</br>
    安装需要的库</br>
```python
pip install requests,concurrent,sqlite3,threading,time
```
    直接刷新视频页面来获取视频信息太慢，通过api地址能快速获取视频信息。</br>
如：https://api.bilibili.com/x/web-interface/archive/stat?aid=19801429，</br>
在浏览器中打开这个页面，可以获取json格式的数据：</br>
```javascript
{
  "code":0,
  "message":"0",
  "ttl":1,
  "data":{
    "aid":19801429,
    "view":583,
    "danmaku":4,
    "reply":2,
    "favorite":378,
    "coin":6,
    "share":6,
    "now_rank":0,
    "his_rank":0,
    "no_reprint":0,
    "copyright":2}
}
```

代码见 [bilibili-spider.py](bilibili-spider.py)