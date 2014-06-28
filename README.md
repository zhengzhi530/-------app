app
==========

* 一个用手机当盘点机用的app，可以外接蓝牙扫枪或者用手机摄像头扫码（慢）
* 用 jqm做界面，cordova（phonegap）生成app。
* 数据传输可以直接用手机存储卡传递文件，也可以用附带的一个简单web服务直接传输到服务器上。

目录结构
========

* spchkm 手机端程序目录
  * spchkm.apk  手机端安装程序.
  * www 源程序.
* flask 服务器端目录
  * myweb 简易的web程序，可直接下载运行 myweb.exe。 myweb.py为源程序。

说明
======
* 一.服务器端（可选）
    * 注意：数据文件都存放在data目录下，不要删除data目录。
    * 在服务器上运行myweb.exe(以管理员身份),此为一个简单的http web服务器，可以方便地与手机盘点app交换数据。
    * 1.通过mis程序导出的商品资料goods.txt(请固定用此文件名)放在data下，手机app就可以直接下载，不用人工拷贝到手机上。
    * 2.手机app上的盘点及收货数据也可以直接上传到data目录下，分别是pd.txt, rk.txt,可以方便地导入到mis系统中。


* 二.手机端
    * spchkm.apk是手机上的app安装程序（android系统）
    * 可直接拷贝到手机上运行安装，也可在运行服务端程序后，在手机浏览器上：
    * http://服务器ip:5000/ 去下载app。
    * 比如服务器ip是123.123.123.250，则：http://123.123.123.250:5000/

注（cordova生成android app）：
=============================
> cordova build android --release

> jarsigner -verbose -keystore spchkm.keystore -signedjar spchkm_signed.apk spchkm-release-unsigned.apk spchkm.keystore

> zipalign -v 4 spchkm_signed.apk  spchkm.apk
