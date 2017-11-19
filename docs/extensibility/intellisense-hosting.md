---
title: "IntelliSense 承载 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 850e4b2ef6d455bb141827fa125c4c7c6860b652
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="intellisense-hosting"></a>IntelliSense 承载
Visual Studio 使 IntelliSense 承载。 IntellSense 承载允许您 IntelliSense 为提供不由 Visual Studio 文本编辑器托管的代码。  
  
## <a name="intellisense-hosting-usage"></a>IntelliSense 承载使用情况  
 在 Visual Studio 中，任何有权访问一完成组和文本缓冲区的代码可以获取 IntelliSense windows 从任何位置中的用户界面 (UI)。 此示例方案是在自动补全**监视**窗口或断点属性窗口的条件字段中。  
  
### <a name="implementation-interfaces"></a>实现接口  
  
#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost  
 承载 IntelliSense 弹出窗口的任何 UI 组件必须支持<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>接口。 默认核心编辑器文本视图包括常用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>接口实现以保留当前的 IntelliSense 功能。 大多数情况下的方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>接口实现的新增功能的子集的表示<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>接口。 该子集包括 IntelliSense UI 处理、 插入符号和选择操作和简单的文本替换功能。 此外，<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>接口使单独智能感知"主题"和"上下文"，以便可以为不直接存在于文本缓冲区正在使用上下文的主体提供 IntelliSense。  
  
#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost.GetHostFlags  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>接口提供程序必须实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A>方法使客户端以确定哪种类型的 IntelliSense 功能主机支持。  
  
 中定义的主机标志[IntelliSenseHostFlags](../extensibility/intellisensehostflags.md)，下面概括了。  
  
|IntelliSense 主机标志|描述|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|设置此标志意味着的上下文缓冲区是只读的和编辑仅发生在主题文本。|  
|IHF_NOSEPERATESUBJECT|设置此标志意味着，存在是没有单独的 IntelliSense 主题。 主题中的上下文缓冲区，如中存在的传统<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>IntelliSense 系统。|  
|IHF_SINGLELINESUBJECT|设置此标志意味着，使用者不是多行支持，如所单行编辑中**监视**窗口。|  
|IHF_FORCECOMMITTOCONTEXT|如果设置此标志，并且必须更新的上下文缓冲区，主机将启用要忽略的上下文缓冲区上的只读标志和编辑以继续。|  
|IHF_OVERTYPE|编辑 （使用者或上下文） 中时，应该在改写模式来完成。|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost.BeforeCompletorCommit 和 IVsIntellisenseHost.AfterCompletorCommit  
 之前和之后文本也会提交，若要启用预处理和后续处理，这些回调方法所调用的完成窗口。  
  
#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor>接口是可共同创建版本的集成的开发环境 (IDE) 使用标准完成窗口。 任何<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>接口可以快速实现通过使用此 completor 接口的智能感知。  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.TextManager.Interop>