---
title: xxx 的文档
titleOnly: true
weight: 1
bookToc: false
---

# 文档模板

阅读地址：<https://kern-crates.github.io/hugo-book-template>

仓库地址：<https://github.com/kern-crates/hugo-book-template>

## 首次使用

1. 创建一个 Github 仓库，假设为 my-doc
2. 将该模板下载至本地，并上传至 Github 仓库

```bash
# 下载模板到 my-doc 目录，并拉取 hugo-book 子模块
git clone https://github.com/kern-crates/hugo-book-template.git my-doc --recursive

# 进入 my-doc 目录
cd my-doc

# 删除旧仓库记录，重新，初始化并设置成你自己的仓库地址
rm .git -rf
git init
git remote add origin your-repo-url # 💡: 修改此处

# 修改内容

# 推送提交
git commit -m "init"
git push --set-upstream origin main
```

3. Github 设置从 Github Action 中部署 Pages。具体见 [#1](https://github.com/kern-crates/hugo-book-template/issues/1)。
4. 在 `hugo.toml` 文件修改你的仓库等信息，尤其那些带 `💡` 的地方
5. 开启 giscus 评论区，具体见 [#3](https://github.com/kern-crates/hugo-book-template/issues/3)。  
   如果你不想要评论区，请把 `layouts/partials/docs/comments.html`
   文件删除，因为它关联了这个模板仓库的评论区。

## 添加/更新文档

在 `content/` 目录添加或者更新文档。

以下是一些 make 命令简化流程：

* `make new doc=design/hi.md`：从模板中创建 `content/design/hi.md` 文件
* `make serve`：本地预览文档，访问地址默认为 `localhost:3001`
  * 如需修改地址和端口，使用 `make serve BIND=xxx PORT=xxx`
* `make generate`：在 public 目录中生成静态网页
  * 通常需要 baseURL 调整地址：`make generate baseURL=your-url`

注意：make 命令将把 README.md 的内容复制到 `content/_index.md`，以保持生成的网页主页与 README 内容一致。

## 相关链接

* AsyncOS 文档 ( <https://asyncos.github.io> ）采用相同的结构和模板，可以参考它的内容
* [hugo-book](https://github.com/alex-shpak/hugo-book) 主题
