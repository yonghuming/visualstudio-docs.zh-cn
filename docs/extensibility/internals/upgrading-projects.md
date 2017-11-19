---
title: "升级项目 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ed049293c50fc59c7f6541a3b4a4cc58c6bd5a7b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="upgrading-projects"></a>升级项目
一个版本的模型更改为项目模型[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]到下一个可能需要项目和解决方案进行升级以便它们可以在较新版本上运行。 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]提供可以用于在您自己的项目中实现升级支持的接口。  
  
## <a name="upgrade-strategies"></a>升级策略  
 若要支持升级，项目系统实现必须定义和实现升级策略。 在确定你的策略，你可以选择支持并行 (SxS) 备份和 / 或副本备份。  
  
-   SxS 备份意味着项目将复制需要就地升级，添加合适的文件名称后缀，例如，".old"那些文件。  
  
-   将复制，项目会将所有项目项都复制到用户提供的备份位置的备用方法。 然后升级原始的项目位置处的相关文件。  
  
## <a name="how-upgrade-works"></a>如何升级工作原理  
 在早期版本中创建的解决方案时[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]打开在较新版本中，解决方案文件以确定它是否需要升级的 IDE 检查。 如果升级是必需的**升级向导**自动启动以指导用户完成升级过程。  
  
 当升级需求的解决方案时，它会查询其升级策略每个项目工厂。 策略确定项目工厂支持复制备份或 SxS 备份。 信息发送到**升级向导**，其中收集备份所需的信息，并向用户呈现的适用选项。  
  
### <a name="multi-project-solutions"></a>多项目解决方案  
 如果解决方案包含多个项目和升级策略不同，如项目工厂时仅支持 SxS 备份的 c + + 项目和仅支持复制备份的 Web 项目，必须协商升级策略。  
  
 解决方案查询的每个项目工厂<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>。 然后，它调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A>全局项目文件是否需要升级并确定支持的升级策略。 **升级向导**然后调用。  
  
 用户完成该向导后<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>上执行实际升级每个项目工厂调用。 若要简化备份过程，IVsProjectUpgradeViaFactory 方法提供<xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>服务记录的升级过程的详细信息。 无法缓存此服务。  
  
 更新所有相关的全局文件之后, 可以选择每个项目工厂实例化一个项目。 项目实现必须支持<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>然后调用方法来升级所有相关的项目项。  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>方法不提供 SVsUpgradeLogger 服务。 此服务可以通过调用获取<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>。  
  
## <a name="best-practices"></a>最佳做法  
 使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>服务以检查是否可以编辑文件，然后才能编辑它，并可以将其保存在保存它之前。 这将帮助你备份和升级实现处理在源代码管理下的项目文件、 文件为没有足够的权限，依此类推。  
  
 使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>服务备份的所有阶段和升级以提供有关升级过程成功与否的信息。  
  
 有关备份并将项目升级的详细信息，请参阅注释为 IVsProjectUpgrade vsshell2.idl 中。  
  
## <a name="upgrading-custom-projects"></a>升级自定义项目
如果你更改保留在产品的不同 Visual Studio 版本之间的项目文件中的信息，则你需要支持将项目文件从旧版本升级到新版本。 若要支持升级，您可以参与**Visual Studio 转换向导**，实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>接口。 此接口包含可用于复制升级的唯一机制。 项目的升级作为解决方案打开的一部分而发生。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>接口由项目工厂实现或至少应为可获得从项目工厂。  
  
 使用的旧机制<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>接口仍受支持，但从概念上讲作为项目打开的一部分升级项目系统。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>接口因此由[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]环境即使<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>调用或实现接口。 此方法允许你使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>实现复制项目的升级时，仅部分并通过委托进行就地 （可能在新的位置） 工作的其余部分<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>接口。  
  
 有关示例实现的<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>，请参阅[VSSDK 示例](http://aka.ms/vs2015sdksamples)。  
  
 项目升级时出现下列情况：  
  
-   如果文件是项目不能支持的较新格式，则它必须返回一个指出此情况的错误。 这假定你产品的较旧版本包含检查版本代码。  
  
-   如果<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>中指定标志<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>方法，则升级将实现项目在打开之前的就地升级。  
  
-   如果<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>中指定标志<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>作为复制升级实现方法，升级。  
  
-   如果<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>中指定标志<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>调用，则已提示用户由环境之后打开该项目的就地升级，升级项目文件。 例如，当用户打开解决方案的较旧版本时，环境会提示用户升级。  
  
-   如果<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>中未指定标志<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>调用，则必须提示用户升级项目文件。  
  
     下面是一个升级提示消息示例：  
  
     “项目“%1”由 Visual Studio 的较旧版本创建。 如果使用此版本的 Visual Studio 打开它，你将不能用较旧版本的 Visual Studio 打开它。 是否要继续并打开此项目？”  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>实现 IVsProjectUpgradeViaFactory  
  
1.  实现的方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>接口，专门<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>方法在你项目工厂实现中，或使该实现可从项目工厂实现调用。  
  
2.  如果你想要执行就地升级作为解决方案打开的一部分，提供标志<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>作为`VSPUVF_FLAGS`中的参数你<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>实现。  
  
3.  如果你想要执行就地升级作为解决方案打开的一部分，提供标志<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>作为`VSPUVF_FLAGS`中的参数你<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>实现。  
  
4.  有关这两个步骤 2 和 3，实际文件升级步骤，使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>，可以实现中所述"实现`IVsProjectUpgade`"部分下面，或者你可以将实际文件升级委派到<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>。  
  
5.  使用的方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>发布升级相关的用户使用 Visual Studio 迁移向导的消息。  
  
6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade>接口用于实现需作为项目升级的一部分发生的文件升级任何类型。 此接口不能从调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>，但会将其作为一种机制来升级属于项目系统中，但主项目系统的文件可能不是直接感知到。 例如，如果编译器相关文件和属性未由处理项目系统其余部分的同一开发团队处理，则可能会发生这种情况。  
  
### <a name="ivsprojectupgrade-implementation"></a>IVsProjectUpgrade 实现  
 如果你的项目系统实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>仅，它不能参与**Visual Studio 转换向导**。 但是，即使你实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>接口，你可以仍将文件升级委派到<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>实现。  
  
#### <a name="to-implement-ivsprojectupgrade"></a>实现 IVsProjectUpgrade  
  
1.  当用户尝试打开一个项目，<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>后打开该项目和任何其他用户操作执行前项目由环境中调用方法。 如果用户已提示升级解决方案，则<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>标志会传递中`grfUpgradeFlags`参数。 如果用户打开一个项目直接，此类通过使用**添加现有项目**命令，则<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>标志不传递，并将该项目需要提示用户升级。  
  
2.  以响应<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>调用，该项目必须评估是否升级该项目文件。 如果项目不需要将项目类型升级到新版本，则它可以只返回<xref:Microsoft.VisualStudio.VSConstants.S_OK>标志。  
  
3.  如果该项目需要将项目类型升级到新版本，则它必须确定是否可以通过调用修改项目文件<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>方法并传入的值<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>为`rgfQueryEdit`参数。 该项目接下来需要执行以下操作：  
  
    -   如果`VSQueryEditResult`中返回值`pfEditCanceled`参数是<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>，然后升级可以继续，因为项目文件可以进行编写。  
  
    -   如果`VSQueryEditResult`中返回值`pfEditCanceled`参数是<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>和`VSQueryEditResult`值具有<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>设置位，然后<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>必须返回失败，因为用户应该解决权限问题本身。 该项目接下来应执行以下操作：  
  
         向用户报告错误，通过调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>并返回<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>错误代码传递给<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>。  
  
    -   如果`VSQueryEditResult`值是<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>和`VSQueryEditResultFlags`值具有<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>设置位，则应通过调用签出项目文件<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>， <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>，...)。  
  
4.  如果<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>项目文件上的调用均会导致文件被签出和最新版本被检索，然后卸载并重新加载项目。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>创建的项目的另一个实例后再次调用方法。 在这第二次调用上，项目文件可以写入磁盘；建议项目使用 .OLD 扩展名按以前的格式保存项目文件的副本、进行必要的升级更改，并以新格式保存项目文件。 同样，如果在升级过程中的任何部分失败，该方法必须指示故障通过返回<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>。 这将导致项目无法在解决方案资源管理器中卸载。  
  
     务必了解发生在这种情况在其环境中的整个过程调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>（指定 ReportOnly 的值） 的方法返回<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>和<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>标志。  
  
5.  用户尝试打开项目文件。  
  
6.  环境调用你<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>实现。  
  
7.  如果<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>返回`true`，然后，该环境调用你<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>实现。  
  
8.  环境调用你<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A>实现，以打开文件并初始化项目对象，例如，Project1。  
  
9. 环境调用你的 `IVsProjectUpgrade::UpgradeProject` 实现来确定是否需要升级项目文件。  
  
10. 你调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>和传入的值<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>为`rgfQueryEdit`参数。  
  
11. 环境将恢复<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>为`VSQueryEditResult`和<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>中设置位`VSQueryEditResultFlags`。  
  
12. 你<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>实现调用`IVsQueryEditQuerySave::QueryEditFiles`(<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>， <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>)。  
  
 此调用可能导致项目文件的新副本被签出、最新版本被检索，以及需要重新加载项目文件。 在这种情况下，将发生以下两种情况中的一种：  
  
-   如果你处理自己的项目重载，则环境将调用你<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>(VSITEMID_ROOT) 实现。 当你收到此调用时，请重新加载项目的第一个实例 (Project1) 并继续升级项目文件。 则环境知道你处理自己的项目重载，是否返回`true`为<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>(<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>)。  
  
-   如果不处理自己的项目重载，则返回`false`为<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>(<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>)。 在这种情况下之前, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>（QEF_ForceEdit_NoPrompting，QEF_DisallowInMemoryEdits） 返回时，环境将创建的项目，例如，Project2，另一个新实例，如下所示：  
  
    1.  环境调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A>上你第一个项目对象 Project1，因此使此对象处于非活动状态。  
  
    2.  环境调用你的 `IVsProjectFactory::CreateProject` 实现来创建项目的第二个实例 Project2。  
  
    3.  环境调用你的 `IPersistFileFormat::Load` 实现，以打开该文件并初始化第二个项目对象 Project2。  
  
    4.  环境第二次调用 `IVsProjectUpgrade::UpgradeProject` 以确定是否应升级项目对象。 但是，此调用在项目的第二个新实例 Project2 上进行。 这就是在解决方案中打开的项目。  
  
        > [!NOTE]
        >  第一个项目，Project1 处于非活动状态，则您必须返回的实例中<xref:Microsoft.VisualStudio.VSConstants.S_OK>从首次调用你<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>实现。  
  
    5.  你调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>和传入的值<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>为`rgfQueryEdit`参数。  
  
    6.  环境将恢复<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>和升级可以继续，因为项目文件可以进行编写。  
  
 如果您不能升级，则返回<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>从`IVsProjectUpgrade::UpgradeProject`。 如果不需要升级或你选择不升级，请将 `IVsProjectUpgrade::UpgradeProject` 调用视作不执行任何操作。 如果返回<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>，占位符节点添加到你的项目的解决方案。  
  
## <a name="upgrading-project-items"></a>升级项目项
  
如果你添加或管理未实现项目系统中的项，你可能需要参与项目升级过程。 Crystal Reports 是可以添加到项目系统的项的一个示例。  
  
 通常情况下，项目项实施者想要利用已完全实例化和已升级的项目，因为它们需要了解哪些项目引用以及其他项目属性还有哪些以进行升级的决策。  
  
### <a name="to-get-the-project-upgrade-notification"></a>若要获取项目升级通知  
  
1.  设置<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading>在项目项实现标志 （在 vsshell80.idl 中定义）。 这将导致您的项目项 VSPackage 自动加载时[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]shell 确定项目系统正在升级。  
  
2.  建议<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>接口通过<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A>方法。  
  
3.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>接口激发后的项目系统实现完成其升级操作和创建新升级后的项目。 根据方案，<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>后激发接口<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>，或<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A>方法。  
  
### <a name="to-upgrade-the-project-item-files"></a>若要升级项目项文件  
  
1.  请务必小心，你必须在项目项实现管理文件备份过程。 这尤其适用于通过并行备份，其中`fUpgradeFlag`参数<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>方法设置为<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>，沿指定为".old"的端文件放置以前已备份的文件的位置。 早于该项目已升级时的系统时间的备份的文件可以指定为过时。 此外，它们可能会覆盖除非采取特定步骤来防止这种情况。  
  
2.  在时您的项目项获取的项目升级时，通知**Visual Studio 转换向导**仍显示。 因此，应使用的方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>接口，以提供到向导 UI 升级的消息。  
  
## <a name="see-also"></a>另请参阅  
 [项目](../../extensibility/internals/projects.md)   
