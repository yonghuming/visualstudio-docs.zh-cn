---
title: "在 JavaScript 中使用 Windows 运行时 | Microsoft Docs"
ms.custom: ""
ms.date: "02/03/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JavaScript, Windows 运行时"
ms.assetid: 90658546-f746-4e34-a7d1-71cf9ee322a2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 在 JavaScript 中使用 Windows 运行时
当你使用 JavaScript 编写 [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)] 或 Windows Phone 应用商店应用时，可以按使用本机 JavaScript 对象、方法和属性大致相同的方式来使用 Windows 运行时类、方法以及属性。  本主题提供介绍性信息以及指向主题的链接，这些主题解释了在 JavaScript 中使用 Windows 运行时 API 的基本概念，包括如何表示 Windows 运行时类型的解释、如何使用异步 Windows 运行时方法以及如何侦听和处理 Windows 运行时事件。  
  
 你可以在 [JavaScript 语言参考](../javascript/javascript-language-reference.md)中查找 JavaScript 参考文档。  
  
> [!IMPORTANT]
>  Windows 运行时功能不适用于在 Internet Explorer 中运行的应用。  
  
## Windows 运行时参考文档  
 有关参考文档，请参阅 [Windows Runtime reference](http://msdn.microsoft.com/zh-cn/8fe97dbf-8cd4-435f-b481-9e83d0519f9e)。  代码示例在 JavaScript 中以及在 C\+\+、C\# 和 Visual Basic 中可用。  
  
## 在 C\+\+、C\# 或 Visual Basic 中编写 Windows 运行时组件  
 有关针对可以在 JavaScript 中使用的 Windows 运行时组件编写的说明和准则，请参阅 [创建 Windows 运行时组件](../Topic/Creating%20Windows%20Runtime%20Components.md)。  
  
## 使用 Windows 运行时功能的大小写约定  
 在 JavaScript 中针对 Windows 运行时功能的大小写约定与其他语言中的约定略有不同：  
  
-   针对 Pascal 的命名空间和类：  
  
    ```javascript  
    Windows.Deployment.PackageInfo;  
    ```  
  
-   类的成员，包括方法和属性以及结构和枚举的成员，都采用 camel 大小写格式：  
  
    ```javascript  
    Deployment.PackageInfo.createPackage();  
    ```  
  
-   事件名称都采用小写格式：  
  
    ```javascript  
    dataTransferManager.ontargetapplicationchosen;  
    ```  
  
## 请参阅  
 [使用 Windows 运行时 API 时的注意事项](../jswinrt/considerations-when-using-the-windows-runtime-api.md)   
 [使用 Windows 运行时异步方法](../jswinrt/using-windows-runtime-asynchronous-methods.md)   
 [在 JavaScript 中处理 Windows 运行时事件](../jswinrt/handling-windows-runtime-events-in-javascript.md)   
 [Windows 运行时类型的 JavaScript 表示形式](../jswinrt/javascript-representation-of-windows-runtime-types.md)   
 [Windows 运行时 DateTime 和 TimeSpan 的 JavaScript 投影](../jswinrt/windows-runtime-datetime-and-timespan-representations.md)