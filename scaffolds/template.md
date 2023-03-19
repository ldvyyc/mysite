<% await tp.file.move("/source/_posts/" + ((tp.file.title.includes("未命名") || tp.file.title.toLowerCase().includes("untitled"))  ? (await tp.system.prompt("请输入要创建的文件名")) : tp.file.title)) %>
---
title: <% tp.file.title %>
author: Frank Yu
categories: 
img: https://s2.loli.net/2023/03/11/8nTKz7lUIEvLPSg.png
toc: true
mathjax: true
cover: false
top: false
summary: Some Posts
date: <% tp.file.creation_date("YYYY-MM-DD, dddd") %>
time: <% tp.file.creation_date("HH:mm") %>
tags: 
- 
---

