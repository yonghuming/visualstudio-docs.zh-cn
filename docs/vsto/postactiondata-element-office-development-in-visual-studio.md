---
title: "&lt;postActionData&gt; 元素（Visual Studio 中的 Office 开发）"
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
  - "<postActionData> 元素"
  - "应用程序清单 [Visual Studio 中的 Office 开发]，<postActionData> 元素"
  - "postActionData 元素"
ms.assetid: e36cbd64-fd27-4413-b293-cf5546fbdfaf
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# &lt;postActionData&gt; 元素（Visual Studio 中的 Office 开发）
  `vstav3`  命名空间的 `postActionData` 元素指定与任何部署后操作关联的数据，这些操作在 Office 解决方案安装后运行。  
  
## 语法  
  
```  
<postActionData>  
</postActionData>  
```  
  
## 元素和属性  
 `postActionData` 元素是可选的且位于 `vstav3`  命名空间中。 每个部署后操作的应用程序清单中只定义了一个 `postActionData` 元素。  
  
 `postActions` 元素没有属性。  
  
 `postActions` 无子元素。  
  
## 部署后操作示例  
  
### 描述  
 下面的代码示例演示 Office 解决方案的应用程序清单中的 `postAction` 元素，该解决方案是使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 部署的。 此代码示例摘自 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md) 中提供的一个更大的示例。  
  
### 代码  
  
```  
<vstav3:postActionData> data in any format </vstav3:postActionData>  
```  
  
## 请参阅  
 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md)   
 [Office 解决方案的部署清单](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)  
  
  