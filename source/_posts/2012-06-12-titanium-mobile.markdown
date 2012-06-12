---
layout: post
title: "Titanium Studioでtiapp.xmlが開けなくなった"
date: 2012-06-12 20:09
comments: true
categories: Android App
---
Titanium Studioでアプリを定義するためのファイル「tiapp.xml」が開けなくなったので調べてみると、日本語化していると不具合が起きやすいとのことで、

    C:\TitaniumStudio\TitaniumStudio.ini

に書き足してあった

    -javaagent:plugins/jp.sourceforge.mergedoc.pleiades/pleiades.jar

を削除してみると、無事ファイルが開けるようになりました。

