---
title: "MSBuild 错误 MSB3190 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GenerateManifest.InvalidRequestedExecutionLevel"
helpviewer_keywords: 
  - "MSB3190"
ms.assetid: 45b45688-9345-45db-adc8-3e200f1c17eb
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3190
**MSB3190: ClickOnce 不支持请求的执行级别“\<level\>”。**  
  
 在运行 Windows Vista 的计算机上，当应用程序的嵌入式用户帐户控制 \(UAC\) 清单指定以管理凭据运行 ClickOnce 应用程序时，便会产生此错误。  ClickOnce 和免注册 COM 需要指定以当前用户的身份运行应用程序的外部清单。  
  
 ClickOnce 不接受执行级别 `requireAdministrator` 或 `highestAvailable`。  如果指定上述级别之一，则会出现此错误。  ClickOnce 要求 `asInvoker`，但也可接受无 `<requestedExecutionLevel>` 节点，此设置指定文件\/注册表虚拟化（表明未生成任何清单；这是为了向后兼容）。  
  
> [!NOTE]
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。  您安装的 Visual Studio 版本以及使用的设置决定了这些元素。  有关更多信息，请参见 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 更正此错误  
  
-   生成一个外部 UAC 清单 \(app.manifest\)，该清单指定以当前用户的身份 \(`asInvoker`\) 运行应用程序。  
  
     在 Visual C\# 项目中，转到项目设计器的**“应用程序”**页面，单击**“清单”**列表中的**“Properties\\app.manifest”**。  有关更多信息，请参见[“项目设计器”\-\>“应用程序”页 \(C\#\)](../ide/reference/application-page-project-designer-csharp.md)。  
  
     在 Visual Basic 项目中，转到项目设计器的**“应用程序”**页面，单击**“查看 UAC 设置”**按钮。  此时将打开 app.manifest，以供进行编辑。  对清单中的以下标记进行编辑，使其更改为：  
  
    ```  
    <requestedExecutionLevel level="asInvoker" />  
    ```  
  
     有关更多信息，请参见[“项目设计器”, “应用程序”页 \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md)。  
  
-   有关如何生成 UAC 清单和指定执行级别的更多信息，请参见 [Windows Vista 上的 ClickOnce 部署](../deployment/clickonce-deployment-on-windows-vista.md)。  
  
## 请参阅  
 [“项目设计器”\-\>“应用程序”页 \(C\#\)](../ide/reference/application-page-project-designer-csharp.md)   
 [“项目设计器”, “应用程序”页 \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [Windows Vista 上的 ClickOnce 部署](../deployment/clickonce-deployment-on-windows-vista.md)