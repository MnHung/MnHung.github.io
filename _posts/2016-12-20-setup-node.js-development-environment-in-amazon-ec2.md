---
layout: post
title: Setup Node.js development environment in Amazon EC2
---

本篇副標題應該訂為「如何一路排除問題，直到可以在 EC2 上開發 Node.js 應用」，當然細節很多，畢竟 EC2 提供的是乾淨的 OS，要怎麼使用全權在你，當然有很多種方式可以達成「開發 Node.js 應用」的目標，這裡先列出這些前提與目標：

 - EC2 instance 為 Ubuntu Server 16.04 的 t2.micro。它是**免費**方案（Free tier eligible），但不小心還是會超出免費標準
 - Node.js 版本為 v6.2.2。選擇這個版本是根據我當前的專案，當然你可以根據你的需要指定安裝別的版本
 - NPM 版本為 3.9.5。選擇這個版本也是配合專案與 Node.js 版本
 - 遠端開發的方式採用 **FTP**。為什麼用 FTP？因為從台灣用 ssh 連線到 EC2 instance 的速度實在有點慢，你不會想用 vi/vim 開發的。選擇 FTP 可以讓你在本地執行的編輯器上快速編寫，存檔的時候才以 FTP 同步。當然這還是有許多缺點，也許有其他更好的方式。

下面會假設你已經準備好一個全新 EC2 instance 了，不會再多做說明怎麼建立，如果你需要的話，網路上有很多圖文並茂的文章教你[怎麼建立 EC2 instance](https://www.google.com.tw/search?q=aws%20ec2%20%E5%BB%BA%E7%AB%8B)。接下來我將會帶著你從一個全新的 EC2 instance 開始。首先，我們必須要：