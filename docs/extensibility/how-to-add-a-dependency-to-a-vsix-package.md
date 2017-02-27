---
title: "如何︰ 添加对 VSIX 包的依赖项 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "包引用"
  - "包的程序集"
  - "包 dll"
  - "vsix 引用"
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 如何︰ 添加对 VSIX 包的依赖项
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以将用于安装尚不存在于目标计算机上的任何依赖项的 VSIX 包部署设置。 若要实现此目的，包括源 source.extension.vsixmanifest 文件 VSIX 依赖关系。  
  
#### 若要添加的依赖项  
  
1.  打开 source.extension.vsixmanifest 文件中的 **设计** 视图。 转到 **依赖关系** 选项卡上，单击 **新建**。  
  
2.  若要添加已安装的扩展︰ 在 **添加新依赖关系** 对话框中，选择 **安装扩展** ，然后，为 **名称**, ，选择列表中的扩展。  
  
3.  若要添加另一个未安装的 VSIX:: 在 **添加新依赖关系** 对话框中，选择 **文件系统上的文件** ，然后使用 **浏览** 按钮以选择的 VSIX。  
  
## 请参阅  
 [VSIX 扩展架构 1.0 引用](http://msdn.microsoft.com/zh-cn/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [VSIX 包的剖析](../extensibility/anatomy-of-a-vsix-package.md)   
 [为 Windows Installer 部署做好准备扩展](../extensibility/preparing-extensions-for-windows-installer-deployment.md)