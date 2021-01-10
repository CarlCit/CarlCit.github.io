---
layout: post
title: "macOS 安装 Jekyll 博客并发布到 GitHub"
subtitle: "Jekyll + macOS + GitHub"
date: 2021-01-09
author: "Carl"
header-style: text
mathjax: true
tags: 
  - 教程
  - Jekyll
  - macOS
  - GitHub
  - application
---

待更新。。。

### 远程仓库克隆到本地
```ruby
# cd 到需要存放的文件夹，克隆 GitHub 仓库的代码
git clone git@github.com:CarlCit/carlcit.github.io.git
```


### 通过 terminal 更新发布到 GitHub


```ruby
jekyll build    				# 构建站点并将静态站点输出到名为 _site 的目录。

# 提交到 GitHub 仓库
git add .  						# 添加到暂存区
git commit -m "提交注释" 		# 提交到本地仓库，注释说明
git push origin main 		# 提交到线上的站点是部署在 main 下面的
```


