---
title: "从域特定语言生成代码 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e3706cc9-2afd-456a-a879-68425a248ebc
caps.latest.revision: 13
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 13
---
# 从域特定语言生成代码
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Microsoft [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 提供了一个强大的方法生成代码，文档，配置文件以及其他项目基于模型表示的数据。  使用 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]，可以创建表示数据的设置类，因此，您可以编写在名称和属性反映该数据的类的文本模板。  
  
 例如， Fabrikam 具有客户的名称和电子邮件地址 XML 文件。  其开发人员使用属性名和电子邮件创建客户是类的一个模型，。  在编写处理数据的多个文本模板，包括作为 HTML 页的一部分，生成所有 customers 表的此片段:  
  
```  
<table>  
<# foreach (Customer c in ContactList) {  #>  
  <tr><td> <#= c.FullName #> </td>   
      <td> <#= c.EmailAddress #> </td> </tr>  
<# } #>  </table>  
```  
  
 当客户数据库处理时， XML 文件读入模型存储区。  指令 *处理器*，使用创建 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]，具有 customer 类的代码可用在文本模板。 许多文本模板可以执行相同的存储。  
  
 文本模板设置 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]非常重要。  它们用于生成源代码用于来集成 project [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的工具域模型元素的和 VSPackage 和控件的。  
  
 本节讨论一些方法，可用来创建、修改和调试用于 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]的文本模板。  
  
## 本节内容  
 [从文本模板访问模型](../modeling/accessing-models-from-text-templates.md)  
  
 提供有关引用域特定语言的基本信息在文本模板。  
  
 [演练：调试访问模型的文本模板](../Topic/Walkthrough:%20Debugging%20a%20Text%20Template%20that%20Accesses%20a%20Model.md)  
  
 描述如何执行疑难解答和调试中引用域特定语言 \(dsl\) 的文本模板。  
  
 [演练：将主机连接至生成的指令处理器](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)  
  
 介绍如何连接自定义宿主到生成的指令处理器。  
  
 [DslTextTransform 命令](../modeling/the-dsltexttransform-command.md)  
  
 描述执行 TextTransform 可执行文本模板的命令行引用域特定语言的命令文件。  
  
## 参考  
 [编写 T4 文本模板](../modeling/writing-a-t4-text-template.md)  
  
 提供文本模板指令和控制块的语法。  
  
## 相关章节  
 [使用 T4 文本模板生成设计时代码](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
  
 解释文本模板转换过程。  
  
 [生成过程中的代码生成](../modeling/code-generation-in-a-build-process.md)  
  
 ，如果要在生成服务器，基于 DSL 的文件请阅读本主题。