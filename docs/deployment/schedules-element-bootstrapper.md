---
title: "&lt;计划&gt;元素 （引导程序） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords: <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
caps.latest.revision: "5"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 104c187d373113e8e5dafe589af3995bef5c8cdc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;计划&gt;元素 （引导程序）
`Schedules`元素包含`Schedule`元素，用于定义所定义的命令在特定时间`Command`元素应运行。  
  
## <a name="syntax"></a>语法  
  
```  
<Schedules>  
    <Schedule  
        Name  
    >  
        <BuildList />  
        <BeforePackage />  
        <AfterPackage />  
    </Schedule>  
</Schedules>  
```  
  
## <a name="elements-and-attributes"></a>元素和属性  
 `Schedules`元素是的子`Product`元素。 每个`Product`元素可能具有最多一个`Schedules`元素。 `Schedules`元素没有任何特性。  
  
## <a name="schedule"></a>计划  
 `Schedule`元素是的子`Schedules`元素。 A`Schedules`元素必须具有至少一个`Schedule`元素。  
  
 `Schedule`具有以下属性。  
  
|特性|说明|  
|---------------|-----------------|  
|`Name`|必需。 计划项的名称。 这对应于`ScheduleName`属性`Command`元素。 当`Command`引用指定的计划中，在由该指示的时间将仅执行`Schedule`元素。 计划还可能与`FailIf`和`BypassIf`元素，用于限制对指定的计划上执行的这些条件的测试。 有关详细信息，请参阅[\<命令 > 元素](../deployment/commands-element-bootstrapper.md)。|  
  
 给定`Schedule`元素可能具有以下的子级中恰好有一个。  
  
## <a name="buildlist"></a>BuildList  
 `BuildList`元素指示安装程序引导应用程序启动之后立即执行命令。  
  
## <a name="beforepackage"></a>BeforePackage  
 `BeforePackage`元素指示安装程序在安装指定的包之前执行命令。  
  
## <a name="afterpackage"></a>AfterPackage  
 `AfterPackage`元素指示安装程序在之后安装指定的包执行命令。  
  
## <a name="see-also"></a>另请参阅  
 [\<产品 > 元素](../deployment/product-element-bootstrapper.md)   
 [产品和包架构引用](../deployment/product-and-package-schema-reference.md)