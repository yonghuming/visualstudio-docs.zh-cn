---
title: "自定义文档属性概述"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "_AssemblyLocation 属性"
  - "_AssemblyName 属性"
  - "自定义文档属性"
  - "文档级自定义项 [Visual Studio 中的 Office 开发], 自定义属性"
  - "文档 [Visual Studio 中的 Office 开发], 自定义属性"
  - "Office 文档 [Visual Studio 中的 Office 开发], 自定义属性"
ms.assetid: 9a215904-b760-4a49-93e8-a1a708ce0526
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# 自定义文档属性概述
  生成文档级项目时，Visual Studio 会向项目中的文档添加两个自定义属性：\_AssemblyLocation 和 \_AssemblyName。  当用户打开文档时，Microsoft Office 应用程序将检查这些自定义文档属性。  如果这些属性存在于文档中，应用程序将加载 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]，后者将启动自定义项。  有关更多信息，请参见[Visual Studio 中 Office 解决方案的体系结构](../vsto/architecture-of-office-solutions-in-visual-studio.md)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## \_AssemblyName  
 此属性包含 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]的 Office 解决方案加载程序组件中某个接口的 CLSID。  此 CLSID 值为 4E3C66D5\-58D4\-491E\-A7D4\-64AF99AF6E8B。  绝对不要更改此值。  
  
## \_AssemblyLocation  
 此属性包含一个字符串，该字符串提供有关自定义项部署清单的详细信息。  有关清单的更多信息，请参见 [Office 解决方案中的应用程序和部署清单](../vsto/application-and-deployment-manifests-in-office-solutions.md)。  
  
 \_AssemblyLocation 属性值可以有不同的格式，具体取决于解决方案的部署方式：  
  
-   如果发布解决方案的目的是为了从网站、UNC 路径或者 CD 或 USB 驱动器中进行安装，则 \_AssemblyLocation 属性的格式为*部署清单路径*|*解决方案 ID*。  下面的字符串是一个示例：  
  
     file:\/\/deployserver\/MyShare\/ExcelWorkbook1.vsto|74744e4b\-e4d6\-41eb\-84f7\-ad20346fe2d9  
  
-   如果在 Visual Studio 中运行或调试解决方案，则 \_AssemblyLocation 属性的格式为*部署清单名称*|*解决方案 ID*|vstolocal。  下面的字符串是一个示例：  
  
     ExcelWorkbook1.vsto|74744e4b\-e4d6\-41eb\-84f7\-ad20346fe2d9|vstolocal  
  
 *解决方案 ID* 是 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 用于标识解决方案的 GUID。  当您生成项目时，*SolutionID* 自动生成。**vstolocal** 一词向指示 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 应从文件夹加载程序集和文档相同。  
  
## 请参阅  
 [Visual Studio 中 Office 解决方案的体系结构](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [文档级自定义项的体系结构](../vsto/architecture-of-document-level-customizations.md)   
 [Office 解决方案中的应用程序和部署清单](../vsto/application-and-deployment-manifests-in-office-solutions.md)   
 [如何：使用 ClickOnce 发布 Office 解决方案](http://msdn.microsoft.com/zh-cn/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)   
 [如何：创建和修改自定义文档属性](../vsto/how-to-create-and-modify-custom-document-properties.md)  
  
  