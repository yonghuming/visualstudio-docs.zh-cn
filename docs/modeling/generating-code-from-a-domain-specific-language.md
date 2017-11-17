---
title: "从域特定语言生成代码 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3706cc9-2afd-456a-a879-68425a248ebc
caps.latest.revision: "13"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 98811cc3e7830dfcbf548bc34c5b3ee268e6f858
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="generating-code-from-a-domain-specific-language"></a>从域特定语言生成代码
Microsoft[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]提供一种强大的方法，从模型中表示的数据生成代码、 文档、 配置文件和其他项目。 使用[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]、 你可以创建一组类，表示数据，并可以编写你的文本模板中的类名称和属性将反映该数据。  
  
 例如，Fabrikam 都有客户名称和电子邮件地址的 XML 文件。 其开发人员创建客户具有属性名称和电子邮件的类的模型。 他们编写多个文本模板处理的数据，包括此片段这样会生成 HTML 页的一部分的所有客户的表：  
  
```  
<table>  
<# foreach (Customer c in ContactList) {  #>  
  <tr><td> <#= c.FullName #> </td>   
      <td> <#= c.EmailAddress #> </td> </tr>  
<# } #>  </table>  
```  
  
 处理客户数据库时，XML 文件读取到模型存储区中。 A*指令处理器*、 通过使用创建[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]，使 Customer 类可供代码文本模板中。 可以针对相同的存储运行多个文本模板。  
  
 文本模板是至关重要的[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]。 它们用于生成域模型以及用于 VSPackage 和用于将集成在工具的控件的元素的源代码[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
 本部分讨论如何创建、 修改和调试文本模板中使用的一些[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]。  
  
## <a name="in-this-section"></a>本节内容  
 [从文本模板访问模型](../modeling/accessing-models-from-text-templates.md)  
  
 提供有关在文本模板中的域特定语言引用的基本信息。  
  
 [演练：调试访问模型的文本模板](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)  
  
 描述如何执行故障排除和调试引用的域特定语言的文本模板上的操作。  
  
 [演练：将主机连接到生成的指令处理器](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)  
  
 介绍如何连接到生成的指令处理器的自定义主机。  
  
 [DslTextTransform 命令](../modeling/the-dsltexttransform-command.md)  
  
 描述引用域特定语言的文本模板在命令行执行 TextTransform 可执行文件的命令文件。  
  
## <a name="reference"></a>参考  
 [编写 T4 文本模板](../modeling/writing-a-t4-text-template.md)  
  
 提供文本模板指令和控制块的语法。  
  
## <a name="related-sections"></a>相关章节  
 [使用 T4 文本模板生成设计时代码](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
  
 说明文本模板转换过程。  
  
 [生成过程中的代码生成](../modeling/code-generation-in-a-build-process.md)  
  
 如果要从在生成服务器上 DSL 生成文件，请阅读本主题。