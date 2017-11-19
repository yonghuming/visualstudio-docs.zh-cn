---
title: "如何： 使用内置可着色项 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 519b842f99ff3e4460626b82aafd24a02f9e720d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-built-in-colorable-items"></a>如何： 使用内置可着色项
使用内置可着色项之前，你必须首先向发出信号集成的开发环境 (IDE) 不提供你自己自定义可着色项，在这种情况下将是<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>对象。 通过设置语言服务的注册表项来执行此操作。  
  
### <a name="to-use-built-in-colorable-items"></a>若要使用内置可着色项  
  
1.  下 HKEY_LOCAL_MACHINE\VisualStudio\\*X.Y*\Languages\Language 服务\\*语言名称*，其中*X.Y*是的版本[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]和*语言名称*是名称的你的语言，创建 DWORD 注册表条目值，调用`RequestStockColors`。  
  
2.  设置`RequestStockColors`注册表条目值设置为 1。  
  
     创建注册表项，你的着色器的后<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法可以使用的成员<xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS>枚举，以填充以供编辑器的颜色属性的数组中。  
  
    > [!NOTE]
    >  如果你要提供自定义可着色项，则未设置此注册表项。 有关详细信息，请参阅[自定义可着色项](../../extensibility/internals/custom-colorable-items.md)。  
  
## <a name="see-also"></a>另请参阅  
 [语法着色中自定义编辑器](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [语法着色中旧语言服务](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [实现语法着色](../../extensibility/internals/implementing-syntax-coloring.md)   
 [自定义可着色项](../../extensibility/internals/custom-colorable-items.md)   
 [注册旧语言服务](../../extensibility/internals/registering-a-legacy-language-service2.md)