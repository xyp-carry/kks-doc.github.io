---
title: 基础配置
weight: 11
bookToc: true
---

# 配置Dify
获取 Dify 知识库API key
![获取API](../../img/get_dify_API.png)

配置dify默认模型，后续在知识库创建中会使用，不设置会报错。从模型运营商中下载对应的运营商，并在默认模型设置的位置添加默认的embedding模型。
![获取API](../../img/setting_dify.png)

# 配置知识库
可以选择多种配置模式:  
*   **通用模式**：将知识块的全部内容作为知识库的文档上传，检索时根据全文进行关键词检索和语义检索。  
*   **QA模式**：将知识块的问题和回答分别作为知识库的文档上传，检索时根据问题进行关键词检索和语义检索，返回对应的回答。

![Dify知识库](../../img/Dify_knowledge_UI.png)

## 通用模式配置

在`config.json`中配置`Custom`为`false`，即可使用通用模式。

```bash
client --createknowledge -k test
```
若成功会显示
```bash
已检测到配置，构建通用模式的知识库
已成功建立知识库 test，ID为 XXXXXXXXXXXXXX
```

插入数据到知识库

将excel文件放于同个文件夹下，文件名命名为`Input.xlsx`，每一条数据占一行，第一列是question，第二列是answer。
```bash
client -i -k test 
```
若成功会显示
```bash
开始解析文档
100%|██████████████████████████████|1/1[00:00<00:00, 986.66it/s]
```

删除知识库
```bash
client -rm -k test
```
若成功会显示
```bash
已成功删除知识库 test，ID为 XXXXXXXXXXXXXXXXXXXXXXXX
```

·

## QA模式配置
在`config.json`中配置`Custom`为`true`，即可使用QA模式，以下为配置文件的示例，使用的是智谱AI的`embedding-3`模型。
```json
"rule": {
            "indexing_technique": "high_quality",
            "doc_form": "qa_model",
            "doc_language":"中文",
            "embedding_model": "embedding-3",
            "embedding_model_provider": "langgenius/zhipuai/zhipuai",
            "embedding_available": true
        }
```
QA模式的插入、删除操作与通用模式相同。

## 更多操作
若需要进行更多操作可以使用dify的前端页面完成，在dify正常启动时，打开浏览器，输入`http://127.0.0.1/datasets`，即可进入dify的知识库配置页面，比如需要对单个知识块进行删除、修改的操作。