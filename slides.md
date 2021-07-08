---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# some information about the slides, markdown enabled
info: |
  Author: [Hsuan](https://hsuan.app)
---

# CMS 介紹

Contest Management System

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    讓我們開始吧 <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" alt="GitHub"
    class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>


<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

# 什麼是CMS?

CMS 是 IOI2012 時所開發的，用以管理程式競賽環境

- 🧑‍💻 **簡單上手** - 程式都封裝好了，只需要一些程式碼就可以上手了
- 📤 **模組化** - 模組化的服務，處理大流量可以多開

<br>
<br>

[官方文檔](https://cms.readthedocs.io/en/v1.4/Introduction.html) · <a href="https://github.com/cms-dev/cms/tree/v1.4" target="_blank" alt="GitHub"
class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
<carbon-logo-github />
</a>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>

---

# 服務

|     |     |
| --- | --- |
| ResourceService | 管理service |
| EvaluationService | 分配job給worker |
| ScoringService | 處理submission的結果、計算成績 |
| ProxyService | 將成績傳送到Ranking |
| LogService | 管理紀錄檔的服務 |
| PrintingService | 列印相關 |
| Worker | 跑code的程式 |
| Checker | 檢查服務是否還活著 |
| ContestWebServer | 比賽伺服器 |
| AdminWebServer | 管理員伺服器 |

---
layout: image-right
image: https://source.unsplash.com/collection/94734566/1920x1080
---

# Ranking Web Server

Ranking Web Server 是獨立出來的一套程式，可以開很多個，應付大流量

記得重新開之前要先drop
```shell
cmsRankingWebServer --drop
```

Proxy Service 也要重開
```shell
cmsProxyService 0 
```