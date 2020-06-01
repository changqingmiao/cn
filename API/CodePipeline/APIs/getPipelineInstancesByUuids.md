# getPipelineInstancesByUuids


## 描述
根据条件查询流水线执行历史


## 请求方式
GET

## 请求地址
https://pipeline.jdcloud-api.com/v1/regions/{regionId}/instances

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**uuids**|String|True| |流水线执行实例ID，多个ID用逗号分隔|
|**isSimple**|Boolean|False| |流水线执行的状态，如果isSimple是true，只显示每个stage的状态, 而stage中的action状态将被忽略|
|**pageNumber**|Integer|False| |页码；默认为1|
|**pageSize**|Integer|False| |分页大小；默认为10；取值范围[10, 100]|
|**sorts**|Sort[]|False| | |
|**filters**|Filter[]|False| |根据流水线名称查询|

### Filter
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|
### Sort
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|False| |排序条件的名称|
|**direction**|String|False| |排序条件的方向|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**pipelineInstances**|PipelineInstance[]| |
### PipelineInstance
|名称|类型|描述|
|---|---|---|
|**uuid**|String|某一次流水线执行的uuid|
|**startedAt**|Integer|开始执行流水线的时间|
|**doneAt**|Integer|结束执行流水线的时间|
|**durationMs**|Integer|执行持续的时间(ms)|
|**status**|Integer|执行状态|
|**statusHuman**|String|执行状态描述|
|**env**|String|执行时环境变量|
|**failureReason**|Integer|失败原因|
|**falseilureReasonHuman**|String|失败原因描述|
|**stages**|PipelineStage[]| |
### PipelineStage
|名称|类型|描述|
|---|---|---|
|**uuid**|String|阶段(stage)的UUID|
|**name**|String|阶段(stage)的名称|
|**createdAt**|Integer|阶段(stage)创建时间|
|**startedAt**|Integer|阶段(stage)开始时间|
|**doneAt**|Integer|阶段(stage)结束时间|
|**status**|Integer|阶段(stage)当前状态|
|**statusHuman**|String|阶段(stage)当前状态说明|
|**position**|Integer|第几个阶段(stage)|
|**actions**|PipelineAction[]| |
### PipelineAction
|名称|类型|描述|
|---|---|---|
|**uuid**|String|操作(action)的UUID|
|**name**|String|操作(action)的名称|
|**createdAt**|Integer|操作(action)创建时间|
|**startedAt**|Integer|操作(action)开始时间|
|**doneAt**|Integer|操作(action)结束时间|
|**status**|Integer|操作(action)当前状态|
|**statusHuman**|String|操作(action)当前状态说明|
|**links**|ActionLinks| |
|**actionTypeId**|ActionTypeId| |
### ActionTypeId
|名称|类型|描述|
|---|---|---|
|**category**|String|源提供商|
|**owner**|String|源提供商归属|
|**provider**|String|操作提供商|
|**version**|Integer|版本|
### ActionLinks
|名称|类型|描述|
|---|---|---|
|**provider**|ActionLink| |
|**status**|ActionLink| |
|**detail**|ActionLink| |
### ActionLink
|名称|类型|描述|
|---|---|---|
|**label**|String|超链接显示的名称|
|**url**|String|超链接的url|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|