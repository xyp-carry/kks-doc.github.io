---
title: 开发者部署
weight: 10
bookToc: true
---

# 开发者部署

## 1. 下载KKS源码
从 https://github.com/xyp-carry/KKS 下载。
```bash
git clone https://github.com/xyp-carry/KKS.git
cd KKS
```

## 2. 安装python依赖
```python
pip install -r requirements.txt

cd installations # 安装yoloV13版本的ultralytics
pip install .
```

## 3. 安装 Dify
dify安装教程：https://github.com/langgenius/dify


## 4. 安装微信 3.9 版本
安装地址：https://weixin.qq.com/updates?platform=windows&version=3.9.12

## 5. 配置KKS
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

6. 启动KKS
```bash
python cilent.py
```