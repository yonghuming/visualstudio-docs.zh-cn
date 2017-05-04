---
title: "&lt;entryPoint&gt; 元素（Visual Studio 中的 Office 开发） | Microsoft Docs"
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
  - "应用程序清单 [Visual Studio 中的 Office 开发]，<entryPoint> 元素"
  - "<entryPoint> 元素"
  - "entryPoint 元素"
ms.assetid: 0c9d22d0-0852-4260-89c6-b83f24e48793
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# &lt;entryPoint&gt; 元素（Visual Studio 中的 Office 开发）
  `vstav3`  命名空间中的每个 `entryPoint` 元素都标识应在安装此 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 应用程序时运行的自定义程序集。  
  
## 语法  
  
```  
<entryPoint class>  
    <assemblyIdentity />  
</entryPoint>  
```  
  
## 元素和属性  
 `entryPoint` 元素是必需的，它位于 `vstav3`  命名空间中。  
  
 每个 `entryPoint` 元素都只能包含一个自定义程序集。 应用程序清单中可以定义多个 `entryPoint` 元素。  
  
 `entryPoint` 元素具有以下属性。  
  
|特性|描述|  
|--------|--------|  
|`class`|必需。 标识要执行的自定义程序集。 此属性的语法是 *NamespaceName.ClassName*。|  
  
 `entryPoint` 具有以下元素。  
  
### assemblyIdentity  
 必需。`vstav3`  命名空间中的 `assemblyIdentity` 元素引用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 应用程序清单中的现有 `assemblyIdentity` 元素。  
  
 `assemblyIdentity` 的角色及其属性在 [&#60;assemblyIdentity&#62; 元素（ClickOnce 应用程序）](../Topic/%3CassemblyIdentity%3E%20Element%20(ClickOnce%20Application).md) 中定义。  
  
## 文档级自定义项示例  
  
### 描述  
 下面的代码示例演示文档级 Office 解决方案的应用程序清单中的 `entryPoint` 元素，该解决方案是使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 部署的。 此代码示例摘自 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md) 中提供的一个更大的示例。  
  
### 代码  
  
```  
<vstav3:entryPoint class="ContosoExcelWorkbook.ThisWorkbook"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet1"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet2"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet3"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint>  
```  
  
## VSTO 外接程序示例  
  
### 描述  
 下面的代码示例演示应用程序级 Office 解决方案的应用程序清单中的 `entryPoint` 元素，该解决方案是使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 部署的。 此代码示例摘自 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md) 中提供的一个更大的示例。  
  
### 代码  
  
```  
<vstav3:entryPoint class="ContosoOutlookAddIn.ThisAddIn"> <assemblyIdentity name="ContosoOutlookAddIn" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint>  
```  
  
## 请参阅  
 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md)   
 [Office 解决方案的部署清单](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)  
  
  