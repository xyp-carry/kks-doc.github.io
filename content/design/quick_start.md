---
title: 快速开始
weight: 2
bookToc: false
---

### 安装步骤

#### 1. 安装 Dify
dify安装教程：https://github.com/langgenius/dify

#### 2. 安装微信 3.9 版本
安装地址：https://weixin.qq.com/updates?platform=windows&version=3.9.12

#### 3. 下载KKS
地址：https://github.com/xyp-carry/KKS-Client
下载zip后直接解压到本地文件夹中。

#### 4. 配置KKS
在config.json中配置Dify的API地址、知识库授权、聊天授权、自定义规则等。
知识库授权的获取来源于Dify的知识库设置。
```python
{
    "Dify": {
        "url": "http://127.0.0.1/", # Dify API地址
        "knowledge_Authorization": "dataset-XXXXXXXXXXX", # Dify 知识库授权
        "chat_Authorization": "app-XXXXXXXXXXXXXXXXX", # Dify 聊天授权
        "Custom": false,
        "rule": {
            "indexing_technique": "high_quality", # 索引 
            "doc_form": "text_model", # text_model和qa_model
            "doc_language":"中文",
            "embedding_model": "embedding-3", # 嵌入模型
            "model_provider": "langgenius/zhipuai/zhipuai", # 模型提供方
            "embedding_available": true
        }
        
    },
    "QAmanager": {
        "base_url": "https://open.bigmodel.cn/api/paas/v4/chat/completions", # 大模型API地址
        "chatmodel": "glm-4.6", # 大模型名称
        "api_key": "XXXXXXXXXXXXXXXXXX" # 大模型API密钥
    }
} 
```
具体的Dify的配置可参考官方API:https://docs.dify.ai/en/use-dify/getting-started/introduction

#### 5. 启动KKS

| 短参数 | 长参数 | 类型 | 默认值 | 说明 |
| :---: | :---: | :---: | :---: | :--- |
| `-n` | `--name` | str | `'robot_test'` | 窗口名称 |
| `-s` | `--start` | flag | `False` | 启动 KKS  |
| `-l` | `--label` | str | `'@robot'` | 回答问题的标签 |
| `-k` | `--knowledgeName` | str | `'os'` | 知识库名称 |
| `-d` | `--dir` | str | `None` | 输出文件目录 |
| `-g` | `--get` | flag | `False` | 获取未确认数据  |
| `-c` | `--confirm` | flag | `False` | 根据文件确认数据 |

启动快捷键
| 快捷键 | 说明 |
| :---: | :--- |
| `Ctrl+Shift+h` | 暂停运行 / 继续运行 |
| `Ctrl+Shift+u` | 总结聊天记录并上传至知识库 |
| `Ctrl+Shift+p` | 退出程序 |

