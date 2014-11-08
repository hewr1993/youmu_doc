# Backend Design Doc

### Requirements

+ 音视频文件的点播服务    - 实现音视频文件的上传，支持断点续传    - 服务器端对上传的视频文件进行转码，转为不同分辨率(手机、流畅、高清)的流媒体文件,并进行存储。    - 用户点播时,相应点播请求,分发视频。    - 采用一定的负载均衡手段,提出并实现实现初步的 CDN 方案(加分点)。+ 音视频直播服务    - 现场采集的音视频文件在本地转为流媒体文件(使用视频采集卡)    - 实时上传服务器，服务器端实时转码    - 实时响应直播用户请求分发到用户    - 考虑直播并发请求数，采用一定的负载均衡和流量控制手段保证直播质量+ 平台后台管理页面    - 可以对于平台上的点播内容和直播进行管理，包括视频(音频)的上传、管理，视频信息(标签、介绍、分类)的修改，视频评论(弹幕)的管理(删除、用户屏蔽)    - 实现分级权限的多用户管理，普通用户可管理自己上传的视频，管理员可管理平台所有视频。
    - 生成分享链接及框架代码(嵌入网页的 html 代码)。    - 视频观看情况监控(视频观看的人数，时间)，视频历史观看数据的简单分析和数据导出。

### Models

定义一些常见的数据模型。

**注意1**：数据模型仍属于unstable阶段。如果需要变更模型，请在issue上提出；如果已有模型发生变更，会通过邮件列表通知每位开发者维护代码。

**注意2**：后端将保证所传回JSON**至少**符合模型要求；后端将不保证对前端传入数据进行（安全性以外的）任何验证。请在前端尽量验证表单数据。

##### user

```
{
    "id": "some unique id",
    "mid": "32435234632462345",
    "name": "江主席",
    "avatar": "/some/strange/url.png",
    "password": "hashed password",
}
```

##### video

```
{
    "video_id": "65546",
    "mid": "34534543dhgfhdf",
    "owner_id": "",
    "owner_mid" : "",
    “disabled": False,
    "title": "江主席怒斥香港记者",
    "upload_time": "SOMEDATETIME"
    "length": 176,
    "cover": "/some/strange/url.png",
    "tags": [
        "江主席",
        "记者",
        "naive"
    ],
    "description": "让你们感受一下",
    "play_count": 35000,
    "like": 455555
}
```

注意id键的值是string类型。

##### comment

```
{
    "comment_id": 30,
    "content": "吼啊",
    "user_id": "abcde",
    "video_id": "65546",
    "reply_to": "",
    "reply_time": "2014-11-06-16:44:00",
    "floor": 1
}
```

replyto选项现在没用。以后考虑要不要加

##### notice

```
靠你们啦~
```

注意：凡是以mid命名的key，均代表它是某一个document在mongo中的id字符串化后的结果。
### APIs

（所有HTML资源的获取方式在此不列）

**注意1**：API仍属于unstable阶段。如果需要变更API，请在issue上提出；如果API发生变更，会通过邮件列表通知每位成员开发者维护代码。

**注意2**：每访问一次API都将带来一定的运行开销，因此前端应尽量调用最合适的API，避免冗余操作。如果某个操作需要多个API进行组合，可能是API设计不合理，请发issue说明。对于一些参数固定且频繁使用的API（例如“点击量前五的视频”），请在issue上说明以开放专用API。<del>专用API将使用cache机制优化性能。</del>

**注意3**：写明login required的就是需要login才能访问的。如果没login会返回空串或者什么我还没想好，但总之前台应该对此有所判断。

##### user

`POST /api/user/_login` 
    
+ Data: username = xx, password = xx （暂时用明文）
+ Return: `{"state":"ok"/"failed"}`

`POST /api/user/_logout` POST but no form

+ Return: `{"state":"ok"/"failed"}`

`POST /api/user/_signup` Form: id = xx, name = xx, password = xx (avatar = xx)

+ Return: `{"state": "ok"/"invalid id"/"invalid password"/...}`

`GET /api/user/{id}` 获取用户模型（JSON-string）

+ Return: User Model Json

`GET /api/user/_me` 获取当前用户的模型，用户未登录则为空串

+ Return: User Model Json

`PUT /api/user/_me` 修改当前用户的信息，

+ Data: name = xx, (avatar = xx)（注意：如果未来有更多选项，这里要把所有个人信息的都传进来，而非只传有改动的几项）

+ Return: `{"state": "ok"/"invalid id"/"password incorrect"/...}`

##### comment

`POST /api/comment/video/{video_id}` 在某个视频下评论（参数里有回复楼层之类的。不需要提供id）

+ Return: `{ "state" : msg }` msg为yes代表成功。其他的可能有need login, no content等均为失败。

`GET /api/comment/video/{video_id}`

+ Return: List of comment model json，返回按照楼层排序

`GET /api/comment/user/{user_id}`

+ Return: List of comment model json，返回按照评论时间排序（可带参数reverse = 0/1，0升序，1降序）

以上两个请求均可以带offset（默认0），size（默认20）的参数。

##### notification

`GET /api/notification/` (login required)获取用户当前的通知列表

`GET /api/notice/{nid}` (login required)获取某条具体的通知

`PUT /api/notice/{nid}` (login required)标记某条通知为已读过/未读过（http参数 read?=True）
##### video
`GET /api/video` 
+ Return: `[video jsons]`（**类似**于使用`GET /api/videolist`）

`GET /api/video/{id}`

+ Return: video json

`POST /api/video/{id}/_play`

+ No para and no return. 视频播放数+1 

<del>`POST /api/video` (login required) 上传视频资源</del>

<del>`DELETE /api/video/{id}` 删除视频资源</del>

`GET /api/video/{id}/_like`赞了此视频的用户列表

+ Return: `{"total": some number}` 

`POST /api/video/{id}/_like`(login required)翻转当前用户赞的状态（赞->未赞，未赞->赞）

+ Return: `{"like": "yes"/"no"}`

`GET /api/video/{video_id}/_like/{user_id}`查询视频被某用户赞过

+ Return: `{"like": "yes"/"no"}`

`GET /api/video/{video_id}/_like/_me`查询自己是否赞过某视频

+ Return: `{"like": "yes"/"no"}`

##### videolist

所有查询类请求均支持offset(?=0), size(?=10), order_by(?="upload_time"), reverse(?=0), filters(?=None)参数

order_by参数可有以下选择：

+ upload_time: 按上传时间排序。reverse为False（默认）时，最早上传的视频靠前。
+ play_count: 按点击量排序。reverse为False（默认）时，点击量最少的视频靠前。
+ like: 同上

<del>filters参数为一key-value字典。下面列出的所有url模板中可能的参数都可以写在filters中。另外，如果uri中的属性与filters中的属性冲突，优先采用uri中的属性。当filters为None时，可能会获得更好的查询性能。</del>

**目前不计划支持复合查询**

`GET /api/videolist` 最general的查询方式。

`GET /api/videolist/owner/{id}` 获取指定用户上传的视频列表

`GET /api/videolist/tag/{query}` 获取指定标签的视频列表

`GET /api/videolist/name/{query}` 获取指定名字的视频列表

`GET /api/videolist/keyword/{query}` 按关键字搜索的视频列表