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
    "title": "江主席怒斥香港记者",
    "length": 176,
    "cover": "/some/strange/url.png",
    "tags": [
        "江主席",
        "记者",
        "naive"
    ],
    "description": "让你们感受一下"
}
```

注意id键的值是string类型。

##### comment

```
{
    "comment_id": 30,
    "mid": "233233233",
    "content": "吼啊",
    "user_id": "abcde",
    "user_name": "平西王",
    "user_avatar": "/some/strange/url.png"
    "video_id": "65546",
    "reply_to": "233233233"
    "floor": 1
}
```

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

##### authentication

`GET/POST /api/user/_login` 可能需要配合LoginForm使用。关于表单的问题还要再讨论

`GET/POST /api/user/_logout` (login required)

`POST /api/user/_signup` 

##### user

`GET /api/user/{id}` 获取用户模型（JSON-string）

`GET /api/userinfo` (login required)获取有权限的用户模型

`PUT /api/userinfo` (login required)修改用户信息

##### comment

`POST /api/comment/{video_id}` 在某个视频下评论（参数里有回复楼层之类的。不需要提供id，会在session中找）

剩下的懒得想了！靠你们啦

##### notification

`GET /api/notification/` (login required)获取用户当前的通知列表

`GET /api/notice/{nid}` (login required)获取某条具体的通知

`PUT /api/notice/{nid}` (login required)标记某条通知为已读过/未读过（http参数 read?=True）
##### video
`GET /api/video` 获取资源列表（视频模型JSON-array）（相当于使用`GET /api/videolist`）

`GET /api/video/{id}` 获取视频资源，返回值为视频模型JSON。

`POST /api/video` (login required) 上传视频资源 

<del>`DELETE /api/video/{id}` 删除视频资源</del>

##### videolist

所有查询类请求均支持offset(?=0), size(?=10), order_by(?="time"), reverse(?=False), filters(?=None)参数

order_by参数可有以下选择：

+ time: 按上传时间排序。reverse为False（默认）时，最早上传的视频靠前。
+ count: 按点击量排序。reverse为False（默认）时，点击量最少的视频靠前。

filters参数为一key-value字典。下面列出的所有url模板中可能的参数都可以写在filters中。另外，如果uri中的属性与filters中的属性冲突，优先采用uri中的属性。<del>当filters为None时，可能会获得更好的查询性能。</del>

`GET /api/videolist` 最general的查询方式。

`GET /api/videolist/owner/{id}` 获取指定用户上传的视频列表

`GET /api/videolist/tag/{query}` 获取指定标签的视频列表

`GET /api/videolist/name/{query}` 获取指定名字的视频列表

`GET /api/videolist/keyword/{query}` 按关键字搜索的视频列表