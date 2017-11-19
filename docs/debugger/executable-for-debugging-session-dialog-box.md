---
title: "调试会话对话框中可执行文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.exefordebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2fa8dfde80cff512ca6f774d8ee90a524931450
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="executable-for-debugging-session-dialog-box"></a>“调试会话的可执行文件”对话框
当您尝试调试没有指定可执行文件的 DLL 时，将出现该对话框。 Visual Studio 不能直接启动 DLL， 而是启动指定的可执行文件。 在可执行文件调用 DLL 时，您可以调试该 DLL。  
  
 **可执行文件名称**  
 输入调用正在调试的 DLL 的可执行文件的路径名。  
  
 **URL 项目可以访问 (仅限 ATL Server)**  
 如果正在调试 ATL Server DLL，则输入可以找到项目的 URL。  
  
 输入后，这些设置存储在“属性页”项目中，因此，在后续调试会话中，您不必再输入这些设置。 如果需要更改设置，您可以打开“属性页”并更改值。 为调试会话指定可执行文件的详细信息，请参阅[调试 Dll](../debugger/how-to-debug-from-a-dll-project.md)。  
  
## <a name="see-also"></a>另请参阅  
 [在 Visual Studio 中进行调试](../debugger/index.md)  
 [调试器功能简介](../debugger/debugger-feature-tour.md)