---
title: "如何：注销 VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "示例应用程序 [Visual Studio SDK]，卸载"
  - "安装程序，VSPackage"
ms.assetid: b51522f0-c033-4d93-b928-2171a953032b
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# 如何：注销 VSPackage
默认情况下，生成 VSPackage 时，它们将被注册到实验性注册表配置单元。 对 VSPackage 进行实验后，实验性配置单元可能会填充不打算保留的 VSPackage。  
  
 若要删除在实验性配置单元中注册的所有包，只需通过具有 \/Reset 选项的 CreateExpInstance 工具重置该配置单元即可。 有关详细信息，请参阅[实验实例](../extensibility/the-experimental-instance.md)。  
  
## 注销单个 VSPackage  
  
#### 若要注销非托管的 VSPackage  
  
1.  单击“开始”，再单击“运行”，键入`regsvr32 /u`*pathToVSPackage.dll*，然后单击“确定”。  
  
 由于非托管 VSPackage 包含自注册代码，因此你可以使用 regsvr32 实用工具来对它们进行注册和注销。  
  
#### 注销托管 VSPackage  
  
1.  单击“启动”，再单击“运行”，键入 *Visual Studio SDK installation path*`\EnvSDK\tools\bin\x86\regpkg /unregister` *pathToVSPackage.dll*，然后单击“确定”。  
  
 RegPkg 工具读取可嵌入到托管 VSPackage 中的注册属性。**\/unregister** 开关指示 RegPkg 删除注册表中的信息。  
  
## 请参阅  
 [Visual Studio Integration Samples](http://msdn.microsoft.com/zh-cn/b5dbf078-3af2-4fed-a1ea-171e4ee73a43)