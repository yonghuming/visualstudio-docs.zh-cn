---
title: "Excel Communicator 示例接口 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1dbf1090-762c-4824-82dd-2d7c2c6f00b6
caps.latest.revision: 11
ms.author: douge
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5ab78b6b8eaa8156ed2c8a807b1d8a80e75afa84
ms.openlocfilehash: 58423d52947c920d42c91508922e5a84ef239b23
ms.lasthandoff: 04/04/2017

---
# <a name="sample-excel-communicator-interface"></a>示例 Excel Communicator 接口
`IExcelUICommunication` 示例接口在 `ExcelAddIn` 项目的 `ExcelUICommunicator` 对象中使用。  
  
## <a name="iexceluicommunication-interface"></a>IExcelUICommunication 接口  
 此接口定义 `CodedUIExtension`（在编码的 UI 测试进程中运行）和 `ExcelCodedUIAddIn`（在 [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 进程中运行）之间的通信点。  
  
 `ExcelCodedUIAddinHelper` 程序集具有 `ExcelUICommunicator` 类，该类派生自此接口并使用 Excel 对象模型来处理方法。  
  
 某些方法从 Excel 中获取请求的信息，然后创建并返回其中一个信息对象，如 `CellInformation` 对象。  
  
 其他方法使用提供的信息对象，在 Excel 中查找相应的控件，并对控件执行某一进程。 例如，`ScrollIntoView` 方法滚动工作表，以显示指定单元格。  
  
## <a name="codeduiextensibilitysample-and-excelcodeduiaddinhelper-communication"></a>CodedUIExtensibilitySample 和 ExcelCodedUIAddinHelper 通信  
 `ExcelCodedUIAddinHelper` 程序集在 Excel 进程中运行，具有实现 `IExcelUITestCommunication` 接口的 `UICommunicator` 类，并且该类直接从 Excel UI 获取或设置所需的信息。  
  
 `CodedUIExtensibilitySample` 程序集在 Visual Studio 编码的 UI 测试进程中运行。 此程序集具有 `Communicator` 类，此类打开 .NET 远程处理信道，其 `Instance` 属性通过 `IExcelUICommunication` 接口来使用 `ExcelCodedUIAddinHelper` 程序集中的 `UICommunicator` 对象，以便在两个程序集之间来回传递请求和信息对象，例如 `CellInformation` 对象。  
  
## <a name="see-also"></a>另请参阅  
 [扩展编码的 UI 测试和操作录制以支持 Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [用于编码的 UI 测试的 Excel 示例外接程序](../test/sample-excel-add-in-for-coded-ui-testing.md)   
 [用于 Excel 的编码的 UI 测试扩展示例](../test/sample-coded-ui-test-extension-for-excel.md)

