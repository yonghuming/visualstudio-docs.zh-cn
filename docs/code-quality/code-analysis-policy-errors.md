---
title: "代码分析策略错误 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.policyfailures
helpviewer_keywords: policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 052bb1314560089feb714027737f35167c947418
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="code-analysis-policy-errors"></a>代码分析策略错误
如果在签入时未满足代码分析策略，会发生以下错误：  
  
 **一个或多个项目的代码分析设置不兼容与代码分析策略。**  
  
 一个或多个代码项目未满足签入到团队项目源代码管理的代码分析需求。 此错误可能是由以下一种或多种情况引起的：  
  
1.  未对解决方案中所有项目的生成版本启用代码分析。  
  
2.  本地规则集对 Visual Studio 中的项目具有限制性较少**操作**设置不是团队项目规则等设置的规则设置为**操作**=**错误**在服务器上其**操作**设置为**警告**或**无**的规则集中运行 Visual Studio 中)。  
  
3.  在 Visual Studio 指定的规则集不包含在团队项目代码分析签入策略中指定的规则集中指定的所有规则。  
  
 **代码分析策略失败。项目 {0} 中出现错误或生成不是最新。**  
  
 要么生成包含错误或已修复的错误，但此修补程序后未执行代码分析。  
  
 **签入失败。代码分析策略要求，签入通过 Visual Studio 与打开的解决方案。**  
  
 代码分析策略要求要签入的所有文件都必须在当前打开的解决方案。 若要更正此错误，打开包含要签入的文件的解决方案。  
  
 **在挂起的签入中不是所有文件都都处于当前打开的解决方案中。**  
  
 代码分析策略要求要签入的所有文件都必须在当前打开的解决方案。 没有打开的解决方案，但"挂起签入"视图中的某些文件不是当前打开的解决方案的一部分，则会出现此错误。 若要更正此错误，打开包含要签入的文件的解决方案。  
  
 **"{0}"的版本不正确。强名称的策略中指定为 {1}。**  
  
 此错误适用于.NET 项目。 所需的代码分析策略规则.dll 存在的本地计算机上，但版本/公钥不匹配。 若要更正此错误，策略创建者必须更新中的.dll *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static 分析 Tools\FxCop\Rules\\* 目录在其计算机上。  
  
 **"{0}"的策略中指定的程序集不存在。**  
  
 此错误适用于.NET 项目。 代码分析策略所需的规则没有对应的客户端计算机上安装的 dll。 若要更正此错误，策略创建者必须更新该 dll 中的*C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static 分析 Tools\FxCop\Rules\\* 目录在其计算机上。  
  
 **项目 {0} 规则设置不是使用代码分析策略的一致性。**  
  
 此错误适用于.NET 项目。 托管的代码规则设置不是像策略要求的那样严格的。 若要更正此错误，客户端设置必须相同或比在服务器上的策略要求更严格。  
  
 **活动配置上未启用代码分析。切换到配置 {0} 并签入前生成项目 {1}。**  
  
 在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、 活动的配置未启用代码分析，但没有启用的至少一种代码分析。  
  
 **必须为项目 {0} 属性中的托管二进制文件时启用代码分析，并生成在签入之前。**  
  
 此错误适用于[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)].NET 应用程序。 策略需要托管的代码分析，以执行，但未启用客户端上当前项目中。  
  
 **必须在项目 {0} 属性中启用代码分析，并生成在签入之前。**  
  
 应用于此错误[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]项目和 Web 项目。 策略需要托管的代码分析，以执行，但未启用客户端上当前项目中。  
  
 **必须在项目 {0} 属性中启用 C/c + + 代码分析，并在签入之前生成。**  
  
 此错误适用于非托管项目。 代码分析策略要求代码分析为 C/c + +，但未启用客户端上当前项目中。  
  
## <a name="see-also"></a>另请参阅  
 [代码分析应用程序错误](../code-quality/code-analysis-application-errors.md)