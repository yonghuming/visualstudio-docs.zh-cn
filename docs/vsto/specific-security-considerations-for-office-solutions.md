---
title: "Office 解决方案的特定安全注意事项 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- troubleshooting Office development in Visual Studio, security
- trusted code [Office development in Visual Studio]
- blocked code [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], object model guard
- malicious code [Office development in Visual Studio]
- Outlook object model guard [Office development in Visual Studio]
- security [Office development in Visual Studio], troubleshooting
ms.assetid: 6a8b3e12-26c6-4ee2-a37e-d5bc8df9c5d1
caps.latest.revision: "51"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: dcbda36113bbf17ec65b9397e8312b03dcf7615a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="specific-security-considerations-for-office-solutions"></a>Office 解决方案的特定安全注意事项
  Microsoft .NET Framework 和 Microsoft Office 提供的安全功能有助于保护你的 Office 解决方案免受可能的安全威胁。 本主题将介绍其中一些威胁并提供有助于免受这些威胁的建议。 还包括有关 Microsoft Office 安全设置如何影响 Office 解决方案的信息。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="trusted-code-is-repurposed-in-a-new-malicious-document"></a>在新的恶意文档中重新使用了受信任的代码  
 攻击者可以获取旨在用于特定用途的受信任的代码，例如，下载雇佣申请中的个人信息，并在另一个文档（例如工作表）中重用它。 该代码不知道原始文档未在运行，且可能会带来其他威胁，如透露个人信息或由其他用户打开时用提升的特权执行代码。 或者，攻击者可轻易修改工作表中的数据，使得该数据在发送到受害者计算机时出现异常行为。 通过更改链接到代码的工作表的值、公式或演示文稿特征，恶意用户可能通过发送已修改的文件攻击另一个用户。 通过修改工作表中的值，用户也可能访问他们不应该看到的信息。  
  
 由于程序集定位和文档定位必须有足够的证据才能执行，所以这种攻击不容易装入。 例如，电子邮件附件中的文档或不受信任的 Intranet 服务器上的文档没有足够的权限，从而无法运行。  
  
 要使此类攻击成为可能，则代码本身的编写方式必须使其基于可能不受信任的数据进行决策。 一个示例就是创建具有隐藏单元格的工作表，其中包含数据库服务器的名称。 用户将工作表提交给 ASPX 页，它会使用 SQL 身份验证和硬编码的 SA 密码尝试连接到该服务器。 攻击者可以将隐藏单元格的内容替换为另一个计算机名称，并获取 SA 密码。 为避免此问题，切勿硬编码密码，并始终在访问服务器之前针对已知善意的服务器的内部列表检查服务器 ID。  
  
### <a name="recommendations"></a>建议  
  
-   始终验证输入和数据，无论它是来自用户、文档、数据库、Web 服务还是任何其他源。  
  
-   公开特定类型的功能（例如代表用户获取特权数据并将其放置于未受保护的工作表中）时要谨慎。  
  
-   根据应用程序的类型，验证在执行任何代码之前原始文档正在运行可能会有用。 例如，验证它正在从存储在已知的安全位置的文档运行。  
  
-   如果你的应用程序将执行任何特权操作，则在文档打开时显示警告可能是一个好办法。 例如，可以创建显示应用程序将访问个人信息的初始屏幕或启动对话框，并让用户选择继续还是取消。 如果最终用户从看似无害的文档获取这样的警告，他/她将能够在危及任何内容之前退出该应用程序。  
  
## <a name="code-is-blocked-by-the-outlook-object-model-guard"></a>代码被 Outlook 对象模型防护阻止  
 Microsoft Office 可以限制代码在对象模型中使用某些属性、方法和对象。 通过限制对这些对象的访问，Outlook 有助于防止电子邮件蠕虫和病毒出于恶意目的使用对象模型。 此安全功能称为 Outlook 对象模型防护。 如果 VSTO 外接程序在启用对象模型防护时尝试使用受限的属性或方法，Outlook 会显示一条安全警告，让用户能够停止操作或授予在有限时段内对属性或方法的访问权限。 如果用户停止操作，则使用 Visual Studio 中的 Office 解决方案创建的 Outlook VSTO 外接程序将引发 <xref:System.Runtime.InteropServices.COMException>。  
  
 对象模型防护可以以不同的方式影响 VSTO 外接程序，具体取决于 Outlook 是否与 Microsoft Exchange Server 一起使用：  
  
-   如果 Outlook 未与 Exchange 一起使用，则管理员可以启用或禁用计算机上所有 VSTO 外接程序的对象模型防护。  
  
-   如果 Outlook 与 Exchange 一起使用，则管理员可以启用或禁用计算机上所有 VSTO 外接程序的对象模型防护，或指定特定 VSTO 外接程序可以在不遇到对象模型防护的情况下运行。 管理员还可以修改对象模型特定区域的对象模型防护的行为。 例如，管理员可以自动允许 VSTO 外接程序以编程方式发送电子邮件，即使启用了对象模型防护也是如此。  
  
 从 Outlook 2007 中开始，更改了对象模型防护的行为以改善开发人员和用户体验，同时还有助于保障 Outlook 安全。 有关详细信息，请参阅 [Outlook 2007 中的代码安全性变化](http://go.microsoft.com/fwlink/?LinkId=73429)。  
  
### <a name="minimizing-object-model-guard-warnings"></a>最小化对象模型防护警告  
 若要帮助在你使用受限的属性和方法时避免出现安全警告，请确保 VSTO 外接程序从项目中 `Application` 类的 `ThisAddIn` 字段获取 Outlook 对象。 有关此字段的详细信息，请参阅 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)。  
  
 对象模型防护仅可信任从此对象获取的 Outlook 对象。 与此相反，从新的 Microsoft.Office.Interop.Outlook.Application 对象获取的对象不受信任，和受限的属性和方法将引发安全警告，如果启用了对象模型防护。  
  
 如果启用了对象模型防护，下面的代码示例将显示一条安全警告。 Microsoft.Office.Interop.Outlook.MailItem 类 To 属性受对象模型防护。 Microsoft.Office.Interop.Outlook.MailItem 对象不受信任的因为代码从使用创建 Microsoft.Office.Interop.Outlook.Application**新**运算符，而不是从获取它`Application`字段。  
  
 [!code-csharp[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#1)]
 [!code-vb[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#1)]  
  
 下面的代码示例演示如何使用受对象模型防护信任 Microsoft.Office.Interop.Outlook.MailItem 对象属性的受限。 该代码使用受信任`Application`要获取 Microsoft.Office.Interop.Outlook.MailItem 字段。  
  
 [!code-csharp[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#2)]
 [!code-vb[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#2)]  
  
> [!NOTE]  
>  如果 Outlook 与 Exchange 一起使用，则从 `ThisAddIn.Application` 获取所有 Outlook 对象不能保证 VSTO 外接程序能够访问整个 Outlook 对象模型。 例如，如果 Exchange 管理员将 Outlook 自动设置为拒绝所有尝试访问地址信息使用 Outlook 对象模型，则 Outlook 将不允许前面的代码示例，若要访问收件人属性中，即使该代码示例使用受信任`ThisAddIn.Application`字段。  
  
### <a name="specifying-which-add-ins-to-trust-when-using-exchange"></a>指定使用 Exchange 时要信任的外接程序  
 当 Outlook 与 Exchange 一起使用时，管理员可以指定某些 VSTO 外接程序可以在不遇到对象模型防护的情况下运行。 不能单独信任使用 Visual Studio 中的 Office 解决方案创建的 Outlook VSTO 外接程序；只能将它们作为一个组来信任。  
  
 Outlook 信任基于 VSTO 外接程序入口点 DLL 的哈希代码的 VSTO 外接程序。 面向 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 的所有 Outlook VSTO 外接程序使用同一个入口点 DLL (VSTOLoader.dll)。 这意味着，如果管理员信任任何面向 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 的 VSTO 外接程序在不遇到对象模型防护的情况下运行，则面向 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 的所有其他 VSTO 外接程序也均受信任。 有关信任特定 VSTO 外接程序在不遇到对象模型防护的情况下运行的详细信息，请参阅 [指定 Outlook 用于管理病毒防护功能的方法](http://go.microsoft.com/fwlink/?LinkId=128773)。  
  
## <a name="permission-changes-do-not-take-effect-immediately"></a>权限更改不会立即生效  
 如果管理员调整文档或程序集的权限，则用户必须退出并重启所有 Office 应用程序，才会实行这些更改。  
  
 托管 Microsoft Office 应用程序的其他应用程序也可以阻止实行新权限。 当安全策略发生更改时，用户应当退出使用 Office 的所有（托管的或独立的）应用程序。  
  
## <a name="trust-center-settings-in-the-microsoft-office-system-do-not-affect-add-ins-or-document-level-customizations"></a>Microsoft Office System 中的“信任中心”设置不影响外接程序或文档级自定义项  
 通过设置“信任中心” 中的选项，用户可以阻止 VSTO 外接程序加载。 但是，使用 Visual Studio 中的 Office 解决方案创建的 VSTO 外接程序和文档级自定义项不受这些信任设置的影响。  
  
 如果用户通过使用“信任中心” 阻止 VSTO 外接程序加载，则将不会加载以下几种类型的 VSTO 外接程序：  
  
-   托管和非托管的 COM VSTO 外接程序。  
  
-   托管和非托管的智能文档。  
  
-   托管和非托管的自动化 VSTO 外接程序。  
  
-   托管和非托管的实时数据组件。  
  
 下面的过程介绍用户如何能使用“信任中心”  来限制 VSTO 外接程序在 Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 和 Microsoft Office 2010 中加载。 这些过程不影响使用 Visual Studio 中的 Office 开发工具创建的 VSTO 外接程序或自定义项。  
  
#### <a name="to-disable-vsto-add-ins-in-microsoft-office-2010-and-microsoft-includeoffice15shortvstoincludesoffice-15-short-mdmd-applications"></a>在 Microsoft Office 2010 和 Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 应用程序中禁用 VSTO 外接程序  
  
1.  选择“文件”  选项卡。  
  
2.  选择*ApplicationName* **选项**按钮。  
  
3.  在类别窗格中，选择“信任中心” 。  
  
4.  在细节窗格中，选择“信任中心设置” 。  
  
5.  在类别窗格中，选择“外接程序” 。  
  
6.  在细节窗格中，选择“要求应用程序外接程序由受信任的发布者签名”  或“禁用所有应用程序外接程序” 。  
  
## <a name="see-also"></a>另请参阅  
 [确保 Office 解决方案的安全](../vsto/securing-office-solutions.md)  
  
  