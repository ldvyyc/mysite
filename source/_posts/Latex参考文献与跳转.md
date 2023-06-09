
---
title: Latex参考文献与跳转
author: Frank Yu
categories: Waffle
img: https://s2.loli.net/2023/03/11/8nTKz7lUIEvLPSg.png
toc: true
mathjax: true
cover: false
top: false
summary: How to insert reference in Latex.
date: 2023-06-09, Friday
time: 20:25
tags: 
- Latex
- Tools
---

## 目标

希望能够在latex中实现点击跳转参考文献，点击跳转文章内的图表。

## 参考文献

使用bibtex插入参考文献，需要在tex文件同级目录下新建一个Ref.bib文件，文件中插入参考文献的bib格式数据。这里的数据一般在论文网站可以直接导出，复制进来即可。

![同级目录下添加bib文件](https://cdn.jsdelivr.net/gh/ldvyyc/ImgBed/20230609204359.png)


### 插入参考文献

需要在tex文件结尾添加下面的几行code：

```tex
\bibliographystyle{plainnat} %参考文献显示格式，plain，plainnat，unsrt等。
\nocite{*} %这句话的意思是展示所有bib中存在的参考文献，不管是否在文章中引用过。没有这句话就只显示论文中引用过的文献。
\bibliography{Ref} %这里引用同目录下的Ref.bib

\end{document}

```
### 引用参考文献

使用natbib包+citet调用。

```tex
\usepackage{natbib}         % 可以添加修饰 \usepackage[...]{natbib}
\usepackage{hyperref}       % hyperlinks

%正文中：
\cite{...} %展示序号
\citet{...} %展示格式，默认为Author+year，可以在引用natbib包的时候更改引用格式
```
### 完整示例代码

```tex
\documentclass[12pt]{article} %文档头

\usepackage[UTF8]{ctex} % 显示中文
\usepackage{natbib} % 导入natbib包，使用author-year格式
\usepackage{hyperref} % 导入超链接包，在文中文献引用处点击可实现跳转

\begin{document} % 开始文档

\section{参考文献引用} % 第一部分

测试引用参考文献\citet{GU2021429}

\bibliographystyle{plainnat} 
\bibliography{Cmm} % 参考文献bib文件名称

\end{document}

```

### 效果

![引用参考文献效果](https://cdn.jsdelivr.net/gh/ldvyyc/ImgBed/20230609204115.png)

可以点击正文中的链接，自动跳转到参考文献对应文章处。导出pdf仍然生效。

## 引用图表

使用 \label 添加标签，使用 \ref 引用标签。

### 示例代码

```tex
\documentclass[12pt]{article} %文档头

\usepackage[UTF8]{ctex} % 显示中文
\usepackage{natbib} % 导入natbib包，使用author-year格式
\usepackage{hyperref} % 导入超链接包，在文中文献引用处点击可实现跳转
\usepackage{booktabs} % 导入三线表需要的宏包
\usepackage{multirow}
\usepackage{multicol}
\begin{document} % 开始文档

\section{引用示例} % 第一部分

\begin{table}[htbp]
    \setlength{\abovecaptionskip}{0.05cm}
    \renewcommand{\arraystretch}{0.7}
  \caption{测试}
  \label{Table 1}             % 设置Table的label
  \centering
  \begin{tabular}{cccccccc}
    \toprule
     & & \multicolumn{6}{c}{K}                   \\
    \cmidrule(r){3-8}
    Model     & Test Assets     & 1 & 2 & 3 & 4 & 5 & 6 \\
    \midrule
    CNN & $r_t$ & - & - & - & - & - & -\\
    \bottomrule
  \end{tabular}
\end{table}

测试，表格\ref{Table 1} 在这里。 % 引用Table的label

\end{document}
```

### 效果

![引用图表效果](https://cdn.jsdelivr.net/gh/ldvyyc/ImgBed/20230609205154.png)

点击序号可以跳转到表格位置。