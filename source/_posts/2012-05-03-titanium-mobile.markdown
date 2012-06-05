---
layout: post
title: "Titanium Mobileことはじめ"
date: 2012-05-03 09:51
comments: true
categories: Android App
---
*この記事の方法では、エミュレータが動かなかったり、実機転送ができなかったりがありまして…いろいろ試行錯誤をしたので、近いうちに記事を修正します…*

#### Titanium MobileのWindows 7へのインストール
「Titanium」は「タイタニウム」と読むそうな。  
以下、Android App開発のためのWindows 7へのインストール手順です。（それぞれ、2012/5/3現在のバージョンです。）


#### (1) JAVA JDKのインストール
[JAVA SE Downloads](http://www.oracle.com/technetwork/java/javase/downloads/index.html)から、Java SE 7u4のJDKをダウンロード。  
ダウンロード後、解凍してインストール（Program Files以下でOK）


#### (2) Android SDKのインストール
[Android SDK](http://developer.android.com/sdk/index.html)から、「installer_r18-windows.exe」をダウンロード。  
ダウンロード後、指示に従ってインストール。その際、JAVA JDKを

    C:\Program Files\Java\jdk1.7.0_04

に指定する。インストール先はProgram Files以下でOK。

インストール後、引き続きSDK ManagerとAVD Managerを立ち上げて初期設定を行う。  

- SDK Managerでは、Tools以下2つとExtra＞Google USB Driverをインストール。時間に余裕があれば、所持している実機に合わせて「Android 2.2」などのDeviceをインストールしておく。（かなり時間がかかる）  
- AVD Managerでは、SDKでDeviceをインストールした場合、Virtual Deviceの設定を行う。  

（これらは後で設定できるので、省略可。）


#### (3) Pathの設定
(1)(2)でインストールしたディレクトリまでのパスを、環境変数に追加

    コントロールパネル→システム環境設定→環境変数→Path

の末尾に

    ;C:\Program Files\Android\android-sdk\platform-tools;C:\Program Files\Android\android-sdk\tools;C:\Program Files\Java\jdk1.7.0_04\bin

を追加する。


#### (4) Titanium Studioのインストール
[Titanium Studio](http://www.appcelerator.com/platform/titanium-studio)からダウンロード。（アカウントを作らないとダウンロードできない？）

ダウンロード後、指示に従ってインストール。ディレクトリを

    C:\TitaniumStudio

に変更してインストール継続。


#### (5) Titanium Studioの日本語化
[Pleadesファイルのダウンロード](http://mergedoc.sourceforge.jp/)から、本体の安定版をダウンロード。  
解凍後、FeaturesとPluginsを

    C:\TitaniumStudio
    
内の同名のフォルダに上書き。

    C:\TitaniumStudio\TitaniumStudio.ini

の末尾に

    -javaagent:plugins/jp.sourceforge.mergedoc.pleiades/pleiades.jar

を追記。


#### (6) JDKのバージョン
このままだと、JDKのバージョンの指定が誤っていて、

    [ERROR] JDK version 1.7.0 detected, but 1.6 is required

というエラーが出てAndroidのエミュレータが起動しないので、

    C:\Users\(ユーザー名)\AppData\Roaming\Titanium\mobilesdk\win32\2.0.1.GA2\android\prereq.py

の21、22行目

    if not version.startswith("1.6"):
        status = "JDK version %s detected, but 1.6 is required" % version

を

    if not version.startswith("1.7"):
        status = "JDK version %s detected, but 1.7 is required" % version

に変更。

