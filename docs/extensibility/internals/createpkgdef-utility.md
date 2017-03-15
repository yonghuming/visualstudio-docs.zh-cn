---
title: "CreatePkgDef 实用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "包定义"
  - "创建 pkgdef"
  - "pkgdef"
  - "createpkgdef"
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# CreatePkgDef 实用程序
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

采用 Visual Studio 扩展中作为参数的.dll 文件，并创建一个.pkgdef 文件附带.dll 文件。 .Pkgdef 文件包含否则将在安装该扩展时写入到系统注册表的所有信息。  
  
> [!NOTE]
>  大部分自动包含在 Visual Studio SDK 的项目模板创建.pkgdef 文件作为生成过程的一部分。 本文档旨在为那些想要手动创建包或转换现有包以使用.pkgdef 部署。  
  
## 语法  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## 参数  
 \= \/`FileName`  
 必需。 设置的.pkgdef 输出文件的名称```FileName`。  
  
 \/codebase  
 可选。 强制通过基本代码实用程序的注册。  
  
 \/assembly  
 强制使用程序集实用程序的注册。  
  
 `AssemblyPath`  
 您想要生成.pkgdef.dll 文件的路径。  
  
## 备注  
 通过使用.pkgdef 文件的扩展部署将替换 Visual Studio 的早期版本的注册表要求。  
  
 .Pkgdef 文件必须安装在以下位置之一: %localappdata%\\Microsoft\\Visual Studio\\14.0\\Extensions\\ 或 %vsinstalldir%\\common7\\ide\\extensions\\。 如果安装文件夹，%localappdata%\\Microsoft\\Visual Studio\\14.0\\Extensions\\ 扩展 Visual Studio 中，将识别，但默认情况下将禁用。 用户可以通过启用扩展 **扩展和更新**。 如果安装文件夹位于 %vsinstalldir%\\common7\\ide\\extensions\\，默认情况下启用扩展。  
  
> [!NOTE]
>  **扩展和更新** 工具不能用于访问扩展，除非为 VSIX 包的一部分安装。  
  
## 请参阅  
 [CreateExpInstance 实用程序](../../extensibility/internals/createexpinstance-utility.md)