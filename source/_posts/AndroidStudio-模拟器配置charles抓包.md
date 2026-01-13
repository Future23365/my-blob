---
title: Android Studio 模拟器配置charles抓包
date: 2023-02-01 17:41:54
tags:
categories: 问题总结
---
### 证书准备
1. Charles 导出pem格式根证书
2. 使用命令： <code>openssl x509 -subject_hash_old -in \<证书文件></code> 获取证书hash
3. 将整书文件改名为<code>\<获取到的hash>.0</code>

### 模拟器准备
1. 进入模拟器目录mac: <code>cd Library/Android/SDK/emulator</code>,使用命令打开模拟器<code>./emulator -avd <模拟器名称> -writable-system</code>（不使用命令行打开<code>adb remount</code>将会执行失败）
2. adb root
3. adb remount
4. 使用Android Studio直接将更改后的./证书文件拖入<code>etc/security/cacerts</code>目录下即可

致此，成功将证书安装到模拟器中的根证书中，可能愉快的抓https的包了
