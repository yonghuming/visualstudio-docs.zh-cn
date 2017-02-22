---
title: "如何: 使用内置可着色的项 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "可着色的项"
  - "语言服务，内置可着色的项"
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# 如何: 使用内置可着色的项
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在使用内置可着色项之前，必须先发送信号。集成 \(IDE\)开发环境不是提供拥有自定义可着色项，这是 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> 对象。  通过设置语言服务的注册表项执行此操作。  
  
### 使用内置可着色项  
  
1.  在 HKEY\_LOCAL\_MACHINE \\ \\VisualStudio*X.Y*\\Languages\\Language Services \\*语言名称*下， *X.Y* 是 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 版本，并且 *语言名称* 是该语言的名称，请创建一个 DWORD 注册表输入值调用的 `RequestStockColors`。  
  
2.  设置 `RequestStockColors` 注册表输入值更改为 1。  
  
     在创建注册表项后， colorizer 的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 方法可以使用 <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> 枚举的成员填充颜色属性的编辑器使用。  
  
    > [!NOTE]
    >  ，如果您提供自定义可着色项，不要将此注册表项。  有关更多信息，请参见 [自定义可着色的项](../../extensibility/internals/custom-colorable-items.md)。  
  
## 请参阅  
 [语法着色中自定义编辑器](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [语法着色在传统语言服务](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [实现功能: 语法着色](../../extensibility/internals/implementing-syntax-coloring.md)   
 [自定义可着色的项](../../extensibility/internals/custom-colorable-items.md)   
 [注册早期语言服务](../../extensibility/internals/registering-a-legacy-language-service2.md)