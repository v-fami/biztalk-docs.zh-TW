---
title: 如何將原則新增至應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [policies], adding to applications
- policies, applications
- applications, policies
- policies, adding to applications
ms.assetid: 93b3ce5e-8c63-4c64-9bdc-1747541ba9a8
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2fe3d2b217757d9d06b1954a5d950f4ea88bd91
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004063"
---
# <a name="how-to-add-a-policy-to-an-application"></a><span data-ttu-id="b073b-102">如何新增原則至應用程式</span><span class="sxs-lookup"><span data-stu-id="b073b-102">How to Add a Policy to an Application</span></span>
<span data-ttu-id="b073b-103">本主題描述如何使用 [BizTalk Server 管理] 主控台或命令列，將原則新增至 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b073b-103">This topic describes how to use the BizTalk Server Administration console or the command line to add a policy to a BizTalk application.</span></span> <span data-ttu-id="b073b-104">使用管理主控台時，您可以新增多個原則，一次。</span><span class="sxs-lookup"><span data-stu-id="b073b-104">When using the administration console, you can add more than one policy at a time.</span></span> <span data-ttu-id="b073b-105">新增原則至應用程式可以讓該原則提供給該應用程式以及參考它的其他任何應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="b073b-105">Adding a policy to an application makes it available for use by that application as well as any other applications that reference it.</span></span>  
  
 <span data-ttu-id="b073b-106">當您新增原則至應用程式時，請牢記下列要點：</span><span class="sxs-lookup"><span data-stu-id="b073b-106">When adding a policy to an application, bear in mind the following important points:</span></span>  
  
-   <span data-ttu-id="b073b-107">您可以將原則新增至應用程式的原則必須存在於 BizTalk 群組，規則引擎資料庫，必須將它發行，如中所述之前[如何匯入原則](../core/how-to-import-a-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="b073b-107">Before you can add a policy to an application, the policy must exist in the Rule Engine database for the BizTalk group, and it must be published, as described in [How to Import a Policy](../core/how-to-import-a-policy.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b073b-108">當您使用 [規則引擎部署精靈] 從「規則引擎」資料庫移除原則後，該原則依然會出現在管理主控台中，不過您將無法予以發佈。</span><span class="sxs-lookup"><span data-stu-id="b073b-108">When you remove a policy from the Rule Engine database by using the Rule Engine Deployment Wizard, it will still display in the administration console, but, you will not be able to publish it.</span></span> <span data-ttu-id="b073b-109">如需有關 「 規則引擎部署精靈 」 的詳細資訊，請參閱[如何部署和解除部署原則和詞彙](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md)。</span><span class="sxs-lookup"><span data-stu-id="b073b-109">For more information about the Rule Engine Deployment Wizard, see [How to Deploy and Undeploy Policies and Vocabularies](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md).</span></span>  
  
-   <span data-ttu-id="b073b-110">此原則不能已存在於 BizTalk 群組的另一個應用程式中。</span><span class="sxs-lookup"><span data-stu-id="b073b-110">The policy cannot already exist in another application in the BizTalk group.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="b073b-111">如果原則是由兩個或多個應用程式所共用，您應該建立個別的應用程式來容納此原則，然後建立參考，從使用此原則的應用程式參考到包含此原則的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b073b-111">If a policy is shared across two or more applications, you should create a separate application to contain the policy and then create references from the applications that use the policy to the application containing the policy.</span></span> <span data-ttu-id="b073b-112">這是因為如果您停止了包含原則的應用程式，該原則就會自動解除部署，而且任何使用此原則的應用程式都將無法再使用它。</span><span class="sxs-lookup"><span data-stu-id="b073b-112">This is because if you stop an application that contains a policy, the policy is automatically undeployed and no longer functions for any of the applications that use it.</span></span> <span data-ttu-id="b073b-113">如需新增參考的指示，請參閱[如何加入另一個應用程式的參考](../core/how-to-add-a-reference-to-another-application.md)。</span><span class="sxs-lookup"><span data-stu-id="b073b-113">For instructions on adding a reference, see [How to Add a Reference to Another Application](../core/how-to-add-a-reference-to-another-application.md).</span></span>  
  
-   <span data-ttu-id="b073b-114">原則也必須部署之後，才會生效並開始運作。</span><span class="sxs-lookup"><span data-stu-id="b073b-114">For the policy to take effect and begin functioning, it must also be deployed.</span></span> <span data-ttu-id="b073b-115">原則會自動部署應用程式啟動時，或您可以手動將它們部署中所述[如何部署或解除部署原則](../core/how-to-deploy-or-undeploy-a-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="b073b-115">Policies are automatically deployed when the application starts, or you can manually deploy them as described in [How to Deploy or Undeploy a Policy](../core/how-to-deploy-or-undeploy-a-policy.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b073b-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="b073b-116">Prerequisites</span></span>  
 <span data-ttu-id="b073b-117">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="b073b-117">To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="b073b-118">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="b073b-118">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="to-add-a-policy-to-an-application"></a><span data-ttu-id="b073b-119">新增原則至應用程式</span><span class="sxs-lookup"><span data-stu-id="b073b-119">To add a policy to an application</span></span>  
  
#### <a name="using-the-biztalk-server-administration-console"></a><span data-ttu-id="b073b-120">使用 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="b073b-120">Using the BizTalk Server Administration console</span></span>  
  
1. <span data-ttu-id="b073b-121">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="b073b-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="b073b-122">在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]和 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="b073b-122">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] and the BizTalk group.</span></span>  
  
3. <span data-ttu-id="b073b-123">展開 應用程式中，展開您想要新增原則，並以滑鼠右鍵按一下應用的程式**原則**。</span><span class="sxs-lookup"><span data-stu-id="b073b-123">Expand Applications, expand the application to which you want to add a policy, and then right-click **Policies**.</span></span>  
  
4. <span data-ttu-id="b073b-124">指向**新增**然後按一下**原則**。</span><span class="sxs-lookup"><span data-stu-id="b073b-124">Point to **Add** and click **Policy**.</span></span>  
  
5. <span data-ttu-id="b073b-125">選取每個原則和版本來新增，然後按一下核取方塊**確定**。</span><span class="sxs-lookup"><span data-stu-id="b073b-125">Select the check box of each policy and version to add, and then click **OK**.</span></span>  
  
#### <a name="using-the-command-line"></a><span data-ttu-id="b073b-126">使用命令列</span><span class="sxs-lookup"><span data-stu-id="b073b-126">Using the command line</span></span>  
  
1. <span data-ttu-id="b073b-127">開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別`cmd`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="b073b-127">Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="b073b-128">輸入下列命令，並以適當的值替代，如下表所述：</span><span class="sxs-lookup"><span data-stu-id="b073b-128">Type the following command, substituting the appropriate values, as described in the following table:</span></span>  
  
    <span data-ttu-id="b073b-129">**BTSTask AddResource** [**/ApplicationName:**<em>值</em>] **/Type:System.BizTalk:Rules** [**覆寫**] **/Name:**<em>值</em>**/Version:**<em>值</em>[**/Server:**<em>值</em>] [**/Database:**<em>值</em>]</span><span class="sxs-lookup"><span data-stu-id="b073b-129">**BTSTask AddResource** [**/ApplicationName:**<em>value</em>] **/Type:System.BizTalk:Rules** [**Overwrite**] **/Name:**<em>value</em>**/Version:**<em>value</em> [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="b073b-130">參數值會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="b073b-130">Parameter values are case sensitive.</span></span> <span data-ttu-id="b073b-131">參數名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="b073b-131">Parameter names are not case sensitive.</span></span> <span data-ttu-id="b073b-132">此外，當您使用這個命令新增原則至應用程式時，也會自動新增該原則所使用的任何詞彙。</span><span class="sxs-lookup"><span data-stu-id="b073b-132">Also, when you add a policy to an application by using this command, any vocabularies used by the policy are automatically added as well.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="b073b-133">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="b073b-133">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
    <span data-ttu-id="b073b-134">範例</span><span class="sxs-lookup"><span data-stu-id="b073b-134">Example:</span></span>  
  
    <span data-ttu-id="b073b-135">**BTSTask AddResource /applicationname: myapplication /Type:System.BizTalk:Rules / 覆寫 /Name:MyPolicy /Version:1.0 /Server:MyDatabaseServer /Database:BizTalkMgmtDb**</span><span class="sxs-lookup"><span data-stu-id="b073b-135">**BTSTask AddResource /ApplicationName:MyApplication /Type:System.BizTalk:Rules /Overwrite /Name:MyPolicy /Version:1.0 /Server:MyDatabaseServer /Database:BizTalkMgmtDb**</span></span>  
  
   |<span data-ttu-id="b073b-136">參數</span><span class="sxs-lookup"><span data-stu-id="b073b-136">Parameter</span></span>|<span data-ttu-id="b073b-137">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="b073b-137">Value</span></span>|  
   |---------------|-----------|  
   |<span data-ttu-id="b073b-138">**/ 應用程式名稱**</span><span class="sxs-lookup"><span data-stu-id="b073b-138">**/ApplicationName**</span></span>|<span data-ttu-id="b073b-139">加入原則的 BizTalk 應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="b073b-139">Name of the BizTalk application to which to add the policy.</span></span> <span data-ttu-id="b073b-140">若未指定應用程式名稱，將使用群組預設的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b073b-140">If the application name is not specified, the default BizTalk application for the group is used.</span></span> <span data-ttu-id="b073b-141">名稱如果包含空格，則必須括在雙引號 (") 中。</span><span class="sxs-lookup"><span data-stu-id="b073b-141">Names that include spaces must be enclosed in double quotation marks (").</span></span>|  
   |<span data-ttu-id="b073b-142">**/ 類型**</span><span class="sxs-lookup"><span data-stu-id="b073b-142">**/Type**</span></span>|<span data-ttu-id="b073b-143">**System.biztalk: rules**</span><span class="sxs-lookup"><span data-stu-id="b073b-143">**System.BizTalk:Rules**</span></span>|  
   |<span data-ttu-id="b073b-144">**/ 覆寫**</span><span class="sxs-lookup"><span data-stu-id="b073b-144">**/Overwrite**</span></span>|<span data-ttu-id="b073b-145">此選項指定更新現有的原則。</span><span class="sxs-lookup"><span data-stu-id="b073b-145">Option to update an existing policy.</span></span> <span data-ttu-id="b073b-146">若未指定此選項，且應用程式中現有的原則與所加入的原則同名，AddResource 作業將會失敗。</span><span class="sxs-lookup"><span data-stu-id="b073b-146">If not specified, and a policy already exists in the application that has the same name as the policy being added, the AddResource operation fails.</span></span>|  
   |<span data-ttu-id="b073b-147">**/ 名稱**</span><span class="sxs-lookup"><span data-stu-id="b073b-147">**/Name**</span></span>|<span data-ttu-id="b073b-148">此原則的名稱。</span><span class="sxs-lookup"><span data-stu-id="b073b-148">Name of the policy.</span></span>|  
   |<span data-ttu-id="b073b-149">**/ 版本**</span><span class="sxs-lookup"><span data-stu-id="b073b-149">**/Version**</span></span>|<span data-ttu-id="b073b-150">原則的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="b073b-150">Version number of the policy.</span></span>|  
   |<span data-ttu-id="b073b-151">**/ 伺服器**</span><span class="sxs-lookup"><span data-stu-id="b073b-151">**/Server**</span></span>|<span data-ttu-id="b073b-152">裝載 BizTalk 管理資料庫的 SQL Server 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="b073b-152">Name of the SQL Server instance hosting the BizTalk Management database.</span></span> <span data-ttu-id="b073b-153">如果您指定 Database 參數，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="b073b-153">Required if you specify the Database parameter.</span></span> <span data-ttu-id="b073b-154">如果未指定 Server 及 Database 參數，將會使用群組的預設 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="b073b-154">If Server and Database parameters are not specified, the default BizTalk Management database for the group is used.</span></span>|  
   |<span data-ttu-id="b073b-155">**/ 資料庫**</span><span class="sxs-lookup"><span data-stu-id="b073b-155">**/Database**</span></span>|<span data-ttu-id="b073b-156">BizTalk 管理資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="b073b-156">Name of the BizTalk Management database.</span></span> <span data-ttu-id="b073b-157">如果您指定 Server 參數，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="b073b-157">Required if you specify the Server parameter.</span></span> <span data-ttu-id="b073b-158">如果未指定 Server 及 Database 參數，將會使用群組的預設 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="b073b-158">If Server and Database parameters are not specified, the default BizTalk Management database for the group is used.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b073b-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b073b-159">See Also</span></span>  
 <span data-ttu-id="b073b-160">[管理原則](../core/managing-policies.md) </span><span class="sxs-lookup"><span data-stu-id="b073b-160">[Managing Policies](../core/managing-policies.md) </span></span>  
 <span data-ttu-id="b073b-161">[建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md) </span><span class="sxs-lookup"><span data-stu-id="b073b-161">[Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md) </span></span>  
 [<span data-ttu-id="b073b-162">AddResource 命令：原則</span><span class="sxs-lookup"><span data-stu-id="b073b-162">AddResource Command: Policy</span></span>](../core/addresource-command-policy.md)