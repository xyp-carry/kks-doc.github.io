---
# title: 
weight: 10
bookToc: true
---

# Hugo-book

把图片文件 （比如 `pic.png`） 放到 `static/img` 目录，然后 `![](path/to/img/pic.png)` 引用它。

`path/to/img` 与你的页面地址相关，甚至本地预览和 Pages 部署路径都不太一样。

举例来说，当前这个页面
* 本地为 `localhost:3001/hugo-book/`
* Pages 为 `https://kern-crates.github.io/hugo-book-template/hugo-book/`
* 有一个 `static/img/hugo-book.png` 本地图片，那么部署后它所在的地址为
  * 本地：`localhost:3001/img/hugo-book.png`
  * Pages： `https://kern-crates.github.io/hugo-book-template/img/hugo-book.png`
* 那么应该使用 `![](../img/hugo-book.png)` 引用这个图片

![](../img/hugo-book.png)

官方 hugo-book-demo：<https://hugo-book-demo.netlify.app/>
