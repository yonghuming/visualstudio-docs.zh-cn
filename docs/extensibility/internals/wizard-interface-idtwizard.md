---
title: "向导界面 (IDTWizard) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDTWizard 接口"
  - "向导、 接口"
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# 向导界面 (IDTWizard)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

集成 \(IDE\)开发环境 \(ide\) 使用 <xref:EnvDTE.IDTWizard> 接口用向导进行通信。  向导在 IDE 必须实现此接口以便安装。  
  
 <xref:EnvDTE.IDTWizard.Execute%2A> 方法是唯一的方法与 <xref:EnvDTE.IDTWizard> 接口。  向导实现此方法，而且 IDE 调用接口中的方法。  下面的示例演示方法的签名。  
  
```  
/* IDTWizard Method */  
STDMETHOD(Execute)(THIS_  
   /* [in] */ IDispatch *Application,  
   /* [in] */ long hwndOwner,  
   /* [in] */ SAFEARRAY * *ContextParams,  
   /* [in] */ SAFEARRAY * *CustomParams,  
   /* [out] [in] */ wizardResult *RetVal  
   );  
```  
  
 启动 framework for **新项目** 和 **添加新项目** 向导类似。  首先为，则在 Dteinternal.h 调用 <xref:EnvDTE.IDTWizard> 接口定义。  唯一的区别是设置传递给接口的上下文和自定义参数，该接口调用时。  
  
 以下信息描述向导在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 必须实现工作的 <xref:EnvDTE.IDTWizard> 接口。  IDE 调用在向导的 <xref:EnvDTE.IDTWizard.Execute%2A> 方法，向其传递以下内容:  
  
-   DTE 对象  
  
     DTE 对象是自动化模型的根。  
  
-   句柄如代码段， `hwndOwner ([in] long)`所示的窗口 " 对话框。  
  
     该向导使用此 `hwndOwner` 作为父提供向导对话框。  
  
-   上下文参数传递给接口作为 SAFEARRAY 为代码段所示， `[in] SAFEARRAY (VARIANT)* ContextParams`变量。  
  
     上下文参数包含特定于该向导启动的值和项目的当前状态。  IDE 通过上下文参数到向导。  有关更多信息，请参见 [上下文参数](../../extensibility/internals/context-parameters.md)。  
  
-   自定义参数传递给接口作为 SAFEARRAY 为代码段所示， `[in] SAFEARRAY (VARIANT)* CustomParams`一个变量。  
  
     自定义参数包含用户定义的类型参数。  .vsz 文件传递自定义参数对 IDE。  `Param=` 语句确定值。  有关更多信息，请参见 [自定义参数](../../extensibility/internals/custom-parameters.md)。  
  
-   返回接口的值。  
  
    ```  
    wizardResultSuccess = -1,  
    wizardResultFailure = 0  
    wizardResultCancel = 1  
    wizardResultBackout = 2  
    ```  
  
## 请参阅  
 [上下文参数](../../extensibility/internals/context-parameters.md)   
 [自定义参数](../../extensibility/internals/custom-parameters.md)   
 [向导](../../extensibility/internals/wizards.md)   
 [向导 \(。Vsz\) 文件](../../extensibility/internals/wizard-dot-vsz-file.md)