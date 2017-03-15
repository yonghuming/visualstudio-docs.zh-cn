---
title: "示例 Excel Communicator 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1dbf1090-762c-4824-82dd-2d7c2c6f00b6
caps.latest.revision: 11
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 11
---
# 示例 Excel Communicator 接口
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`IExcelUICommunication`  示例接口在 `ExcelAddIn` 项目的 `ExcelUICommunicator` 对象中使用。  
  
## IExcelUICommunication 接口  
 此接口定义在编码的 UI 测试进程中运行的 `CodedUIExtension` 与在 [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 进程中运行的 `ExcelCodedUIAddIn` 之间的通信点。  
  
 `ExcelCodedUIAddinHelper`  程序集具有一个 `ExcelUICommunicator` 类，该类派生自此接口并使用 Excel 对象模型处理方法。  
  
 有些方法从 Excel 获取所请求的信息，然后创建并返回其中一个信息对象，如 `CellInformation` 对象。  
  
 其他方法使用提供的信息对象，在 Excel 中找到对应控件，并对此控件执行一些处理。  例如，`ScrollIntoView` 方法滚动工作表，以使指定单元格可见。  
  
## CodedUIExtensibilitySample and ExcelCodedUIAddinHelper 通信  
 `ExcelCodedUIAddinHelper`  程序集在 Excel 进程中运行并具有 `UICommunicator` 类，该类实现 `IExcelUITestCommunication` 接口并直接从 Excel UI 中获取或设置所需信息。  
  
 `CodedUIExtensibilitySample`  程序集在 Visual Studio 编码的 UI 测试进程中运行。  此程序集具有可打开 .NET 远程处理信道的 `Communicator` 类，并提供使用 `IExcelUICommunication` 接口的 `Instance` 属性，以便使用 `ExcelCodedUIAddinHelper` 程序集中的 `UICommunicator` 对象在两个程序集之间来回传递请求和信息对象，如 `CellInformation` 对象。  
  
## 请参阅  
 [扩展编码的 UI 测试和操作录制以支持 Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [用于编码的 UI 测试的示例 Excel 外接程序](../test/sample-excel-add-in-for-coded-ui-testing.md)   
 [适用于 Excel 的示例编码的 UI 测试扩展](../test/sample-coded-ui-test-extension-for-excel.md)