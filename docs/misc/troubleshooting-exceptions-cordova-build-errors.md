---
title: "异常疑难解答：Cordova 生成错误 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BLD102"
  - "BLD10205"
  - "BLD301"
  - "BLD401"
  - "BLDErr_Build_NodeMissing"
  - "BLDErr_BLD_Win8Required"
ms.assetid: 781c09e3-0704-4b30-9230-036cbdb2dff9
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
---
# 异常疑难解答：Cordova 生成错误
本主题介绍了一些使用 Visual Studio 用于 Apache Cordova 的工具时可能会遇到的更常见的错误消息。  
  
-   [MSBUILD：cordova 生成错误 BLD102：没有此文件或目录“config.xml”](#BLD102)  
  
-   [MSBUILD：cordova 生成错误 BLD301：尚未配置远程 iOS 生成代理](#BLD301)  
  
-   [MSBUILD：cordova 生成错误 BLD401：找不到模块&lt;模块名称&gt;](#BLD401)  
  
-   [MSBUILD：cordova 生成错误 BLD10205：请安装 Android 目标](#BLD10205)  
  
-   [无法确定到 Node.js 可执行文件的 BLDErr_Build_NodeMissing 路径。](#BLDErr_Build_NodeMissing)  
  
-   [BLDErr_Build_Win8Required](#BLDErr_Build_Win8Required)  
  
 如果需要更多常规帮助来解决 Cordova 应用中的错误，请参阅[解决生成错误](https://taco.visualstudio.com/en-us/docs/resolving-build-errors/)。  
  
##  <a name="BLD102"></a> MSBUILD：cordova 生成错误 BLD102：没有此文件或目录“config.xml”  
 如遇到此错误，请确保你的项目在项目根中含有 config.xml 文件，并确保你的项目是在本地计算机中而不是驻留在网络共享上。  
  
 有关详细信息，请参阅此[堆栈溢出文章](http://stackoverflow.com/questions/27134007/new-cordova-project-gives-the-error-bld00102-no-such-file-or-directory-confi)。  
  
##  <a name="BLD301"></a> MSBUILD：cordova 生成错误 BLD301：尚未配置远程 iOS 生成代理  
 完整的错误字符串是：  
  
-   MSBUILD：cordova 生成错误 BLD301：尚未配置远程 iOS 生成代理。 在“工具”\>“选项”\>“用于 Apache Cordova 的工具”\>“远程代理配置”中配置。 有关详细信息和备用方案，请参阅http:\/\/go.microsoft.com\/fwlink\/?LinkID\=511904  
  
 有关安装和配置适用于 iOS 的 remotebuild 代理的详细信息，请参阅 [iOS 安装指南。](http://taco.visualstudio.com/en-us/docs/ios-guide/)  
  
##  <a name="BLD401"></a> MSBUILD：cordova 生成错误 BLD401：找不到模块\<模块名称\>  
 完整的错误字符串是：  
  
-   MSBUILD：cordova 生成错误 BLD401：错误：BLD00401：找不到模块\<模块名称\>。 请转到“工具”\-\-\>“选项”\-\-\>“用于 Apache Cordova 的工具”\-\-\>“Cordova 工具”\-\-\>“清理 Cordova 缓存”，然后尝试再次生成。  
  
 你可能需要清除缓存并重新安装 vs\-tac。 有关详细信息，请参阅[重新安装 vs\-tac](http://taco.visualstudio.com/en-us/docs/configure-vs-tools-apache-cordova#vstac)。  
  
 清除缓存后，删除项目中的 platforms 文件夹。 然后尝试再次生成。  
  
##  <a name="BLD10205"></a> MSBUILD：cordova 生成错误 BLD10205：请安装 Android 目标  
 如果遇到此错误，请确保使用 Android SDK 管理器 \(SDK Manager.exe\) 为所选目标设备安装所需的依赖项。  
  
 有关所需的 API 级别和其他 Android SDK 组件的详细信息，请参阅[手动安装依赖项](http://taco.visualstudio.com/en-us/docs/configure-vs-tools-apache-cordova#ThirdParty)。  
  
 你也需验证 Visual Studio 用于查找 Android SDK 的位置。 若要执行此操作，请参阅[替代系统环境变量](http://taco.visualstudio.com/en-us/docs/configure-vs-tools-apache-cordova#env-var)。  
  
 有关安装正确组件以使用本工具的详细信息，请参阅[第三方工具](http://taco.visualstudio.com/en-us/docs/install-vs-tools-apache-cordova#choose)。  
  
##  <a name="BLDErr_Build_NodeMissing"></a> 无法确定到 Node.js 可执行文件的 BLDErr\_Build\_NodeMissing 路径。  
 如果 Node.js 已安装到非默认位置，则 Visual Studio 可能无法找到该路径。 将 Node.js 重新安装到默认位置。 有关详细信息，请参阅此[堆栈溢出文章](http://stackoverflow.com/questions/32203992/vs2015-cordova-apps-blderr-build-nodemissing)以及有关[安全更新 Node.js](http://taco.visualstudio.com/en-us/docs/change-node-version/)的文章。  
  
##  <a name="BLDErr_Build_Win8Required"></a> BLDErr\_Build\_Win8Required  
 Windows 8.1 需要面向在使用 Visual Studio Tools for Apache Cordova 创建的应用中的 Windows。