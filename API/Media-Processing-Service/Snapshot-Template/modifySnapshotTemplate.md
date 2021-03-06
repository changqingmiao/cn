# modifySnapshotTemplate


## 描述
修改截图模板

## 请求方式
PATCH

## 请求地址
https://mps.jdcloud-api.com/v1/snapshotTemplates/{templateId}


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**templateId**|String|True| |模板ID|
|**title**|String|False| |模板标题。长度不超过 128 个字节。UTF-8 编码。|
|**startTime**|Integer|False| |截图起始时间，单位为秒，缺省值为 0|
|**frameType**|String|False| |截图帧类型。取值范围：normal、intra|
|**format**|String|False| |截图格式。取值范围：jpg、png|
|**number**|Integer|False| |截图数量，缺省值为 10|
|**interval**|Integer|False| |截图间隔|
|**width**|Integer|False| |截图宽度，取值范围：[8, 4096]<br>|
|**height**|Integer|False| |截图高度，取值范围：[8, 4096]<br>|
|**fillType**|String|False| |填充方式，当视频宽高与截图宽高指定值不能匹配时的填充处理方式。取值范围：<br>  stretch - 伸缩<br>  black - 留黑<br>  white - 留白<br>  gauss - 高斯模糊<br>缺省值为 black<br>|
|**spriteConfig**|[SpriteConfig](user-content-modifysnapshottemplate#spriteconfig)|False| |雪碧图配置|

### <div id="spriteconfig">SpriteConfig</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**rows**|Integer|True| |雪碧图小图行数。雪碧图行列积必须不大于100<br>|
|**columns**|Integer|True| |雪碧图小图列数。雪碧图行列积必须不大于100<br>|
|**cellWidth**|Integer|False| |雪碧图单元格宽度<br>取值范围：[8, 4096]，不能为奇数<br>未设置时，回退为截图宽度 width<br>|
|**cellHeight**|Integer|False| |雪碧图单元格高度，<br>取值范围：[8, 4096]，不能为奇数<br>未设置时，系统自动会自动设置为截图高度 height<br>|
|**doKeepShots**|Boolean|False| |是否保留截图<br>雪碧图的截图方式是先截取普通图，然后合成雪碧图。此字段控制是否保留截图。<br>|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](user-content-modifysnapshottemplate#result)|修改截图模板结果|
|**requestId**|String|请求ID|

### <div id="result">Result</div>
|名称|类型|描述|
|---|---|---|
|**templateId**|String|模板ID|
|**title**|String|模板标题。长度不超过 128 个字节。UTF-8 编码。|
|**startTime**|Integer|截图起始时间，单位：秒|
|**frameType**|String|截图帧类型。|
|**format**|String|截图格式。取值范围：jpg、png|
|**number**|Integer|截图数量|
|**interval**|Integer|截图间隔|
|**width**|Integer|截图宽度|
|**height**|Integer|截图高度|
|**fillType**|String|填充方式|
|**spriteConfig**|[SpriteConfig](user-content-modifysnapshottemplate#spriteconfig)|雪碧图配置|
|**createTime**|String|创建时间|
|**updateTime**|String|修改时间|
### <div id="spriteconfig">SpriteConfig</div>
|名称|类型|描述|
|---|---|---|
|**rows**|Integer|雪碧图小图行数。雪碧图行列积必须不大于100<br>|
|**columns**|Integer|雪碧图小图列数。雪碧图行列积必须不大于100<br>|
|**cellWidth**|Integer|雪碧图单元格宽度<br>取值范围：[8, 4096]，不能为奇数<br>未设置时，回退为截图宽度 width<br>|
|**cellHeight**|Integer|雪碧图单元格高度，<br>取值范围：[8, 4096]，不能为奇数<br>未设置时，系统自动会自动设置为截图高度 height<br>|
|**doKeepShots**|Boolean|是否保留截图<br>雪碧图的截图方式是先截取普通图，然后合成雪碧图。此字段控制是否保留截图。<br>|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|

## 请求示例
PATCH
```
https://mps.jdcloud-api.com/v1/snapshotTemplates/c35a7f843a6e49a4a32b1f8fab99fbd8

```

```
{
    "title": "我的截图模板"
}
```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41", 
    "result": {
        "createTime": "2019-04-16T15:51:32Z", 
        "fillType": "stretch", 
        "format": "jpg", 
        "frameType": "any", 
        "height": 480, 
        "interval": 10, 
        "number": 10, 
        "spriteConfig": {
            "cellHeight": 48, 
            "cellWidth": 48, 
            "columns": 10, 
            "doKeepShots": true, 
            "rows": 10
        }, 
        "startTime": 0, 
        "templateId": "c35a7f843a6e49a4a32b1f8fab99fbd8", 
        "title": "我的截图模板", 
        "updateTime": "2019-04-16T15:51:32Z", 
        "width": 720
    }
}
```
