---
title: "本地数据概述 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Access, Visual Studio 中的 .mdb 文件"
  - "数据 [Visual Studio], 本地"
  - "数据访问 [Visual Studio], 疑难解答"
  - "本地数据"
  - "LocalDB"
  - "SQL Express"
  - "SQL Server Compact"
  - "SQL Server Express"
  - "SQL Server LocalDB"
  - "SQL Server, 本地数据"
  - "SQLEXPRESS"
ms.assetid: d6afa5ac-2bb8-49f2-a50e-f71f611ed506
caps.latest.revision: 71
caps.handback.revision: 66
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 本地数据概述
如果使用本地数据，那么将应用程序连接到本地计算机上的数据库文件，而不是连接到单独服务器上的数据库。  例如，可以将你在 Visual Studio 中开发的应用程序连接到下列本地数据库文件：  
  
-   SQL Server Express LocalDB 数据库文件 \(.mdf\)  
  
-   SQL Server Express 数据库文件 \(.mdf\)  
  
-   Microsoft Access 数据库文件 \(.mdb\)  
  
 下表提供了介绍如何将应用程序连接到本地数据的主题的链接：  
  
|主题|说明|  
|--------|--------|  
|[演练：在 Visual Studio 中创建本地数据库文件](../data-tools/create-a-sql-database-by-using-a-designer.md)|分步介绍如何创建本地数据库文件，可使用该文件测试数据功能并生成应用程序。|  
|[演练：连接到本地数据库文件中的数据（Windows 窗体）](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Local%20Database%20File%20\(Windows%20Forms\).md)|分步介绍创建简单的 Windows 应用程序时如何连接到 SQL Server Express LocalDB 数据库。|  
|[演练：连接到 Access 数据库中的数据（Windows 窗体）](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)|分步介绍如何连接到 Microsoft Access 数据库。|  
|[如何：连接到 Northwind 数据库](../data-tools/how-to-connect-to-the-northwind-database.md)|介绍如何连接到 [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]、SQL Server Compact、SQL Server Express 和 Access 中的 Northwind 示例数据库。|  
  
 在创建数据源并将其配置为访问本地数据文件后，你可以使用在处理任何其他源中的数据时所用的技术和对象，来处理此数据源中的数据。  有关更多信息，请参见[创建数据应用程序](../data-tools/creating-data-applications.md)。  
  
## 将数据库集成到你的应用程序中  
 如果连接到本地数据，不仅可以连接到数据库文件，还可以将其集成到你的应用程序中。  例如，你可以打开**“项目”**菜单，浏览到现有的 .sdf、.mdf 或 .mdb 文件，然后将其添加到你的项目中。  
  
 如果添加本地数据文件，则创建类型化数据集和指向应用程序中数据库文件的动态连接字符串。  将数据库文件添加到项目中时，使用**“数据源配置向导”**指定要包含的对象。  
  
> [!NOTE]
>  你可以将 .sdf、.mdf 或 .mdb 文件从“文件资源管理器”拖到**“解决方案资源管理器”**中，从而自动配置你的连接并启动**“数据源配置向导”**。  随后可指定要在应用程序中使用的对象。  
  
 如果使用**“数据源配置向导”**为本地数据文件创建数据源，则系统会提示你在项目中包含该文件。  如果不包含它，则应用程序将只包含硬编码路径指向的连接字符串，而非实际数据文件。  有关更多信息，请参见[如何：管理项目中的本地数据文件](../data-tools/how-to-manage-local-data-files-in-your-project.md)。  
  
 完成该向导后，数据库文件和数据集将显示在**“解决方案资源管理器”**\/**“数据库资源管理器”**中，并且指定的数据库对象会显示在**“数据源”**窗口中。  通过将某些项从**“数据源”**窗口拖到你的窗体上，可以创建绑定到基础数据的控件。  若要打开**“数据源”**窗口，请打开**“数据”**菜单，然后选择**“显示数据源”**。  有关更多信息，请参见[在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)。  
  
## 使用数据库文件  
 你可能需要先将现有数据库文件 \(.mdf\) 转换为 [!INCLUDE[sql_Denali_short](../data-tools/includes/sql_denali_short_md.md)] 数据库文件，然后才能在 Visual Studio 中使用该文件。  连接到现有数据库文件后，会出现询问你是否升级的消息框。  
  
> [!IMPORTANT]
>  如果升级数据库文件 \(.mdf\)，你将无法在 SQL Server 的较早版本中将其打开。  
  
 如果**“SQL Server 实例名称”**设置为 SQLEXPRESS 且已安装 SQL Server 2008 Express，则无需转换数据库文件 \(.mdf\)。  如果安装了 Visual Studio 2010，则 SQL Server 2008 Express 已安装。  若要为此数据库文件更改实例名称，请打开 Visual Studio，然后打开**“添加连接”**对话框，指定服务器名称 `.\SQLEXPRESS`，然后指定数据库或数据库文件名。  
  
## SQL Server Express LocalDB 和 SQL Server Express  
 你可将基于服务的数据库文件 \(.mdf\) 添加到 Visual Studio 中的任何项目。  你可使用 Visual Studio 中的设计器来设计表和其他数据库对象，也可运行查询。  
  
 在 Visual Studio 中创建基于服务的数据库后，它会使用 SQL Server Express LocalDB 引擎访问数据库文件 \(.mdf\)，而 Visual Studio 的早期版本使用的是 SQL Server Express 引擎。  
  
 SQL Server Express LocalDB 是 SQL Server 的轻量版本，你可以像在 SQL Server 数据库中一样通过很多方式进行编程。  SQL Server Express LocalDB 在用户模式下运行，你可以更加快速地安装它，系统必备组件更少，而且无需配置。  
  
> [!NOTE]
>  有关 SQL Server Express LocalDB 的更多信息，请参见 Microsoft 网站上的[向 LocalDB 引入经改进的 SQL Express](http://go.microsoft.com/fwlink/?LinkId=234375) 和 [LocalDB：我的数据库在哪里？](http://go.microsoft.com/fwlink/?LinkId=234376)。  
  
 在 Visual Studio 中，可以默认使用 SQL Server Express，而不是 SQL Server Express LocalDB。  在菜单栏上，依次选择**“工具”**、**“选项”**。  在**“数据库工具”**节点之下，选择**“数据连接”**。  在**“SQL Server 实例名称”**文本框中，输入 `SQLEXPRESS`。  或者，你可以为 SQL Server 实例名称输入其他值（例如 `SQL2008`）。  
  
 下表描述了 SQL Server Express LocalDB 和 SQL Server Express 引擎之间的差异。  
  
||SQL Server Express LocalDB|SQL Server Express|  
|-|--------------------------------|------------------------|  
|创建基于服务的数据库时的数据库类型|在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 和 [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] 中，为 SQL Server Express LocalDB|在 Visual Studio 2010 和早期版本中，为 SQL Server Express|  
|“工具”\/“选项”中的 SQL Server 实例名称|\(LocalDB\)\\v11.0|SQLEXPRESS|  
|连接字符串中的数据源值|\(LocalDB\)\\v11.0|.\\SQLEXPRESS|  
|连接字符串中的 AttachDbFilename 值|文件路径|文件路径|  
|需要用户实例（连接字符串中“用户实例 \= True”）|否|是|  
|数据库文件扩展名|.mdf|.mdf|  
  
## SQL Server Express LocalDB 的优势  
  
-   SQL Server Express LocalDB 在其所启用功能方面与基于服务的 SQL Server 版本兼容。  在 SQL Server 中，无需升级即可从 SQL Server Express LocalDB 向 SQL Server 或 SQL Azure 中移动任意数据库或 Transact\-SQL 代码。  因此，可以使用 SQL Server Express LocalDB 开发以 SQL Server 所有版本为目标的应用程序。  
  
-   SQL Server Express LocalDB 与较高版本的 SQL Server 一样，同样支持查询优化器和查询处理器。  
  
## 每个项目包含数据库的两个副本  
 生成项目时，数据库文件可能会从根项目文件夹复制到输出（**“bin”**）文件夹。  此行为取决于该文件的**“复制到输出目录”**属性，而该属性的默认值则取决于你正在使用的数据库文件的类型。  
  
 若要查看**“解决方案资源管理器”**中的**“bin”**文件夹，请选择工具栏上的**“显示所有文件”**按钮。  
  
> [!NOTE]
>  **“复制到输出目录”**属性不适用于 Web 或 C\+\+ 项目。  
  
 项目根文件夹中的数据库文件仅在你使用**“服务器资源管理器”**\/**“数据库资源管理器”**或其他 [Visual Database Tools](http://msdn.microsoft.com/zh-cn/6b145922-2f00-47db-befc-bf351b4809a1) 编辑数据库架构或数据时才会更改。  
  
 在应用程序开发期间更改数据时，将更改**“bin”**文件夹中的数据库。  例如，选择 F5 键调试应用程序时，就会连接到该文件夹中的数据库。  
  
|**“复制到输出目录”**属性的值|行为|  
|-----------------------|--------|  
|**“如果较新则复制”**（.sdf 文件的默认值）|首次生成项目时，数据库文件会从项目目录复制到**“bin”**目录。  然后系统会在每次重新生成项目时比较文件的**“修改日期”**属性。  如果项目文件夹中的文件较新，系统会将其复制到**“bin”**文件夹，替换之前的文件。  否则，不复制文件。 **Caution:**  对于 .mdb 或 .mdf 文件，我们不建议使用此值。  即使数据未更改，数据库文件也可更改。  只要打开连接（例如，展开**“服务器资源管理器”**中的**“表”**节点），文件就会标记为较新。|  
|**“始终复制”**（.mdf 和 .mdb 文件的默认值）|每次生成应用程序时，数据库文件都会从项目目录复制到**“bin”**目录。  在输出文件夹中对数据文件所做的任何更改都会在下次运行应用程序时被覆盖。|  
|**不复制**|系统从不覆盖**“bin”**目录中的文件。  你的应用程序会创建指向输出目录中的数据库文件的动态连接字符串。  因此，如果想要输出目录中的数据与项目目录中的数据匹配，必须手动将文件复制到输出目录。|  
  
## 与本地数据相关的常见问题  
 下表阐述了使用本地数据文件时可能会遇到的常见问题。  
  
|问题|说明|  
|--------|--------|  
|每次我测试我的应用程序并修改数据后，下次运行此应用程序时我的更改都消失了。|**“复制到输出目录”**属性的值是**“如果较新则复制”**或**“始终复制”**。  每次生成项目时，输出文件夹中的数据库（测试应用程序时被修改的数据库）都会被覆盖。  有关更多信息，请参见[如何：管理项目中的本地数据文件](../data-tools/how-to-manage-local-data-files-in-your-project.md)。|  
|此时会显示一条消息，指明数据文件被锁定。|对于 Access（.mdb 文件）：请验证是否未在其他程序中打开该文件，例如在 Access 中。<br /><br /> 对于 SQL Server Express（.mdf 文件）：如果尝试在 Visual Studio IDE 外部复制、移动或重命名数据文件，SQL Express 会锁定它。|  
|当一个以上用户尝试同时访问同一数据库时，访问会被拒绝。|Visual Studio 利用 SQL Server Express 的用户实例功能，为每个用户单独创建 SQL Server 实例。  在某个用户访问文件后，所有后续用户将无法连接。  例如，因为 IIS 通常是在不同帐户下运行的，如果你尝试同时在 ASP.NET Development Server 和 Internet 信息服务 \(IIS\) 中运行 Web 应用程序，则可能会出现这种情况。|  
  
## 请参阅  
 [演练：连接到本地数据库文件中的数据（Windows 窗体）](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Local%20Database%20File%20\(Windows%20Forms\).md)   
 [演练：连接到 Access 数据库中的数据（Windows 窗体）](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)