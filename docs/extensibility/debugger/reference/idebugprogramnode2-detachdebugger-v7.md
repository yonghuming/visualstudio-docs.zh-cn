---
title: "IDebugProgramNode2::DetachDebugger_V7 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
ms.assetid: d2d4b78e-a2dd-4217-97a6-ab648fd2ee2f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ea8843a824eb5e1cd0c7bcd658908d7cdaac98ce
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7
不推荐使用。 请勿使用。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT DetachDebugger_V7 (   
   void   
);  
```  
  
```c#  
int DetachDebugger_V7 ();  
```  
  
## <a name="return-value"></a>返回值  
 实现应始终返回`E_NOTIMPL`。  
  
## <a name="remarks"></a>备注  
  
> [!WARNING]
>  在[!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]，此方法不能再使用，否则应始终返回`E_NOTIMPL`。  
  
 调试器会意外退出时，调用此方法。 当调用此方法时，DE 应该恢复该程序，就好像用户从其分离。 应发送没有更多的调试事件。 程序应该在其所在位置可从调试器的另一个实例附加状态。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
