---
title: "在 JavaScript 中使用 Windows 运行时 | Microsoft Docs"
ms.custom: 
ms.date: 02/03/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime
ms.assetid: 90658546-f746-4e34-a7d1-71cf9ee322a2
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6fbf89668d47d55d1d77a1d7f11765567fc73405
ms.openlocfilehash: c81f5d83056ceb87987e263f09c0d5e5017dbb6f
ms.contentlocale: zh-cn
ms.lasthandoff: 08/11/2017

---
# <a name="using-the-windows-runtime-in-javascript"></a>在 JavaScript 中使用 Windows 运行时
在编写通用 Windows 平台 (UWP) 应用时，可以按使用本机 JavaScript 对象、方法和属性大致相同的方式来使用 Windows 运行时类、方法以及属性。 本主题提供介绍性信息以及指向主题的链接，这些主题解释了在 JavaScript 中使用 Windows 运行时 API 的基本概念，包括如何表示 Windows 运行时类型的解释、如何使用异步 Windows 运行时方法以及如何侦听和处理 Windows 运行时事件。  
  
 可在 [JavaScript 语言参考](../javascript/javascript-language-reference.md)中查看 JavaScript 参考文档。  
  
> [!IMPORTANT]
>  Windows 运行时功能不适用于在 Internet Explorer 中运行的应用。  
  
## <a name="windows-runtime-reference-documentation"></a>Windows 运行时参考文档  
 请参阅 [Windows 运行时参考](https://msdn.microsoft.com/en-us/library/windows/apps/br211377.aspx)查看参考文档。 代码示例在 JavaScript 中以及在 C++、C# 和 Visual Basic 中可用。  
  
## <a name="writing-windows-runtime-components-in-c-c-or-visual-basic"></a>在 C++、C# 或 Visual Basic 中编写 Windows 运行时组件  
 有关编写可用于 JavaScript 的 Windows 运行时组件的说明和指南，请参阅[使用 C++ 创建 Windows 运行时组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)和[使用 C# 和 Visual Basic 创建 Windows 运行时组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)。  
  
## <a name="casing-conventions-with-windows-runtime-features"></a>使用 Windows 运行时功能的大小写约定  
 在 JavaScript 中针对 Windows 运行时功能的大小写约定与其他语言中的约定略有不同：  
  
-   针对 Pascal 的命名空间和类：  
  
    ```JavaScript  
    Windows.Deployment.PackageInfo;  
    ```  
  
-   类的成员，包括方法和属性以及结构和枚举的成员，都采用 camel 大小写格式：  
  
    ```JavaScript  
    Deployment.PackageInfo.createPackage();  
    ```  
  
-   事件名称都采用小写格式：  
  
    ```JavaScript  
    dataTransferManager.ontargetapplicationchosen;  
    ```  
  
## <a name="see-also"></a>另请参阅  
 [使用 Windows 运行时 API 时的注意事项](../jswinrt/considerations-when-using-the-windows-runtime-api.md)   
 [使用 Windows 运行时异步方法](../jswinrt/using-windows-runtime-asynchronous-methods.md)   
 [在 JavaScript 中处理 Windows 运行时事件](../jswinrt/handling-windows-runtime-events-in-javascript.md)   
 [Windows 运行时类型的 JavaScript 表示形式](../jswinrt/javascript-representation-of-windows-runtime-types.md)   
 [Windows 运行时 DateTime 和 TimeSpan 的 JavaScript 投影](../jswinrt/windows-runtime-datetime-and-timespan-representations.md)
