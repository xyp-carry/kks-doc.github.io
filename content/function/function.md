---
title: 核心函数使用
weight: 2
bookToc: true
---
# API
## KKoperate
### DifyOperator

```python
from KKSoperator.operator import DifyOperator
operator = DifyOperator(Authorization="Bearer XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX")
```
#### 如何获取Dify API
![技术方案](../../img/get_dify_API.png)
### 获取当前所有知识库id
```python
ids = operator.get_knowledges()
print(ids)
```
```python
['a','b','c',....]
```

### 按知识库名称获取知识库id
```python
id = operator.get_knowledgeid_by_name(knowledge_name="知识库名称")
print(id)
```
```python
'a'
```

### 获取知识库下的已确认文档和未确认文档id

```python
# 如果没有会自动创建
ids = operator.get_documents(knowledge_id="a")
print(ids)
```
```python
{'confirmed': ['a1','a2','a3',....],
 'unconfirmed': ['a4','a5','a6',....]}
```

### 获取当前文档下的所有分块
```python
segments = operator.get_segments(knowledge_id="a",document_id="a1")
```
```python
['a1_1','a1_2','a1_3',....]
```

### 创建知识库
```python
operator.create_knowledge(name="知识库名称")
```
```python
'a'
```

### 删除知识库
```python
operator.delete_knowledge(knowledge_id="a")
```

### 插入分块
```python
operator.insert_segment(knowledge_id="a",document_id="a1",segment_id="a1_1",contents=["分块内容","分块内容2"])
```
```python
None
```

### 将未确认的文档打印出来
```python
# name为知识库名称
operator.Output_unconfirmed(name="a")
```

### 检索分块
```python
operator.query(knowledge_id="a",query="查询内容")
```
```python
{'a1_1': '分块内容', 'a1_2': '分块内容2'}
```

#### 确认文档
```python
# name 为 知识库名称 data 为 dataframe[segmentid,contents]
operator.confirm_by_file(name="a",data="a1")
```
```python
None
```

## KKSqa
```python
qa = QAmanager(base_url = "AI_url",model="modelname",api_key="XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX")
```

#### 上传聊天对话
```python
qa.add_conversation('username','content')
```

#### 添加问题
```python
qa.add_question('question','answer',"source")
```

#### RAGAPI
```python
# context 为 检索分块的结果
qa.rag('query','context')
```

## KKSwx
```python
wx = KKSWx()
```

#### 启动微信检测
```python
# Input为窗口句柄
# Output为消息队列，用于接收微信消息[get]
queue = await wx.start(hwnd)
```

#### 获取窗口句柄
```python
# 输入为要监测的群名称，需要手动将对应的群窗口独立出来
hwnd = wx.find_all_windows_by_keyword("微信")[0]['hwnd']
```

#### 发送信息
```python
# Input为窗口句柄，消息队列，要发送的信息
wx.send_message(hwnd, answer['answer']) # 微信3.9版本
wx.send_message_4(hwnd, answer['answer']) # 微信4.0版本
```
