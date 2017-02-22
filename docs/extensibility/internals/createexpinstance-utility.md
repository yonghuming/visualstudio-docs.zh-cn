---
title: "CreateExpInstance 实用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "实验性生成"
  - "试验性的配置单元"
  - "实验实例"
  - "createexpinstance"
  - "createexpinst"
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# CreateExpInstance 实用程序
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用 CreateExpInstance 实用程序来创建、 重置，或删除 Visual Studio 的实验实例。 可以使用的实验实例来调试和测试 Visual Studio 扩展，而无需更改基础产品。  
  
## 语法  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### 参数  
 \/ 创建  
 创建的实验实例。  
  
 \/ 重置  
 删除的实验实例，然后创建一个新。  
  
 \/Clean  
 删除的实验实例。  
  
 \/ VSInstance  
 包含基本的 Visual Studio 实例，若要复制的目录的名称。  
  
 \/ RootSuffix  
 要追加到实验实例中目录的名称后缀。  
  
## 备注  
 当使用 Visual Studio 扩展时，可以按 f5 键以打开默认的实验实例，然后安装当前的扩展。 如果没有实验实例可用时，Visual Studio 将创建一个具有默认设置。  
  
 实验实例的默认位置取决于 Visual Studio 版本数量。 例如，对于 Visual Studio 2015，位置是 %localappdata%\\Microsoft\\VisualStudio\\14.0Exp\\ 的目录位置中的所有文件被都认为是该实例的一部分。 除非目录名称更改为默认位置，任何其他的实验实例将不加载由 Visual Studio 中。  
  
 在打开的实验实例时，visual Studio 不访问系统注册表。 这不同于早期版本的 Visual Studio 中，使用注册表配置单元的实验版本。  
  
 CreateExpInstance 实用程序将替换 VsRegEx 实用程序。  
  
 下面的示例将重置默认值的 Visual Studio 的实验实例。  
  
 **CreateExpInstance.exe \/Reset \/VSInstance \= 14.0 \/RootSuffix \= Exp**  
  
## 请参阅  
 [发布产品](../../misc/releasing-a-visual-studio-integration-product.md)