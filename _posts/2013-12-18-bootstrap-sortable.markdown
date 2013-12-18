---
layout: post
title: 'bootstrap-sortable: 给 Bootstrap Table 添加排序功能'
date: 2013-12-18 17:17
post-link: https://github.com/drvic10k/bootstrap-sortable
---

bootstrap-sortable 这个 JS 库能够给 Bootstrap 的 Table 增添排序
功能，用起来相当简单。

首先，在 HTML 页面中引用以下三个文件：

    <link href="css/bootstrap-sortable.css" rel="stylesheet" media="screen">
    <script src="js/moment.min.js"></script>
    <script src="js/bootstrap-sortable.js"></script>

接着，在 Table 标签中追加 `sortable` 类即可：

    <table class="table table-striped table-hover sortable">
    ...
    </table>
