---
title: "如何匯出原則 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [policies], exporting
- policies, exporting
- exporting, policies
ms.assetid: 2e46d96a-7762-479b-be20-bd590b2a4f0a
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 752336e0642c42418f6c68ddefb719d02051d937
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-export-a-policy"></a><span data-ttu-id="e3031-102">如何匯出原則</span><span class="sxs-lookup"><span data-stu-id="e3031-102">How to Export a Policy</span></span>
<span data-ttu-id="e3031-103">本主題描述如何使用 BizTalk Server 管理主控台或命令列匯出一個或多個原則及關聯的詞彙。</span><span class="sxs-lookup"><span data-stu-id="e3031-103">This topic describes how to use the BizTalk Server Administration console or the command line to export one or more policies and associated vocabularies.</span></span>  
  
 <span data-ttu-id="e3031-104">匯出原則時，請牢記下列要點：</span><span class="sxs-lookup"><span data-stu-id="e3031-104">When exporting a policy, bear in mind the following important points:</span></span>  
  
-   <span data-ttu-id="e3031-105">使用 [BizTalk Server 管理主控台]，您可以從 BizTalk 群組或 BizTalk 應用程式匯出原則，並且也可以匯出詞彙。</span><span class="sxs-lookup"><span data-stu-id="e3031-105">Using the BizTalk Server Administration console, you can export policies from a BizTalk group or a BizTalk application as well as the vocabularies to export.</span></span> <span data-ttu-id="e3031-106">使用 BTSTask，您可以從應用程式匯出原則，而且所有關聯的詞彙也都將匯出。</span><span class="sxs-lookup"><span data-stu-id="e3031-106">Using BTSTask, you can export policies from an application, and all of the associated vocabularies will be exported as well.</span></span> <span data-ttu-id="e3031-107">您不能選取所要匯出的詞彙。</span><span class="sxs-lookup"><span data-stu-id="e3031-107">You cannot select the vocabularies to export.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="e3031-108">在使用管理主控台時，您可以選取要匯出哪些詞彙。</span><span class="sxs-lookup"><span data-stu-id="e3031-108">When using the administration console, you can select which vocabularies to export.</span></span> <span data-ttu-id="e3031-109">我們建議您選取匯出與原則關聯的所有詞彙。</span><span class="sxs-lookup"><span data-stu-id="e3031-109">We recommend that you select for export all of the vocabularies associated with a policy.</span></span> <span data-ttu-id="e3031-110">這樣一來，您就可以確定需要的詞彙都會存在於目的地環境中。</span><span class="sxs-lookup"><span data-stu-id="e3031-110">This way, you can be sure that the required vocabularies are present in the destination environment.</span></span> <span data-ttu-id="e3031-111">即使需要的詞彙已經在先前部署到目的地環境，如果已刪除其關聯原則，也就會刪除這些詞彙。</span><span class="sxs-lookup"><span data-stu-id="e3031-111">Even if the required vocabularies were previously deployed to the destination environment, if their associated policy was deleted, they would have been deleted as well.</span></span> <span data-ttu-id="e3031-112">這是因為當您刪除原則時，其他原則沒有使用的所有詞彙也都會被刪除。</span><span class="sxs-lookup"><span data-stu-id="e3031-112">This is because when you delete a policy, all of its vocabularies that are not being used by another policy are deleted.</span></span>  
  
-   <span data-ttu-id="e3031-113">您可以再匯入的原則不同 BizTalk 群組，或是在不同的 BizTalk 群組中，應用程式中所述[如何匯入原則](../core/how-to-import-a-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="e3031-113">You can then import the policy or policies into a different BizTalk group or an application in a different BizTalk group, as described in [How to Import a Policy](../core/how-to-import-a-policy.md).</span></span>  
  
-   <span data-ttu-id="e3031-114">在能夠匯出原則之前，該原則必須存在於 BizTalk 群組的「規則引擎」資料庫中。</span><span class="sxs-lookup"><span data-stu-id="e3031-114">Before you can export a policy, it must exist in the Rule Engine database for the BizTalk group.</span></span> <span data-ttu-id="e3031-115">有數種方式可將原則匯入 「 規則引擎 」 資料庫中所述[如何匯入原則](../core/how-to-import-a-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="e3031-115">There are several ways to import a policy into the Rule Engine database, as described in [How to Import a Policy](../core/how-to-import-a-policy.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e3031-116">當您使用 [規則引擎部署精靈] 從「規則引擎」資料庫移除原則後，該原則依然會出現在管理主控台中，不過您將無法予以瀏覽。</span><span class="sxs-lookup"><span data-stu-id="e3031-116">When you remove a policy from the Rule Engine database by using the Rule Engine Deployment Wizard, it will still display in the administration console, but you will not be able to export it.</span></span> <span data-ttu-id="e3031-117">如需規則引擎部署精靈的詳細資訊，請參閱[如何部署和解除部署原則和詞彙](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md)。</span><span class="sxs-lookup"><span data-stu-id="e3031-117">For more information about the Rule Engine Deployment Wizard, see [How to Deploy and Undeploy Policies and Vocabularies](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md).</span></span>  
  
-   <span data-ttu-id="e3031-118">當您使用管理主控台來匯出時，原則和詞彙都將匯出到一個 .xml 檔案中。</span><span class="sxs-lookup"><span data-stu-id="e3031-118">When you use the administration console for exporting, the policies and vocabularies are exported into an .xml file.</span></span> <span data-ttu-id="e3031-119">當您使用 BTSTask 命令列工具來匯出時，原則和詞彙都將匯出到一個應用程式 .msi 檔案中。</span><span class="sxs-lookup"><span data-stu-id="e3031-119">When you use the BTSTask command-line tool for exporting, the policies and vocabularies are exported into an application .msi file.</span></span>  
  
-   <span data-ttu-id="e3031-120">BTSTask 沒有提供匯出原則的特定命令，不過您可以使用 BTSTask 的 ExportApp 命令來選擇性地只匯出您所需要的原則，而不包括其他的成品。</span><span class="sxs-lookup"><span data-stu-id="e3031-120">BTSTask does not provide a specific command for exporting policies; however you can use the ExportApp command of BTSTask to selectively export only the policies you want, and no other artifacts.</span></span> <span data-ttu-id="e3031-121">這樣便會產生包含原則的應用程式 .msi 檔案。</span><span class="sxs-lookup"><span data-stu-id="e3031-121">This generates an application .msi file containing the policies.</span></span> <span data-ttu-id="e3031-122">您可以使用 ImportApp 命令將 .msi 檔案匯入到不同的 BizTalk 群組中。</span><span class="sxs-lookup"><span data-stu-id="e3031-122">You can use the ImportApp command to import the .msi file into a different BizTalk group.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e3031-123">必要條件</span><span class="sxs-lookup"><span data-stu-id="e3031-123">Prerequisites</span></span>  
 <span data-ttu-id="e3031-124">下列是執行本主題所述程序的必要條件：</span><span class="sxs-lookup"><span data-stu-id="e3031-124">The following are prerequisites for performing the procedures in this topic:</span></span>  
  
-   <span data-ttu-id="e3031-125">您必須以 BizTalk Server Administrators 群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="e3031-125">You must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="e3031-126">如需詳細的權限的相關資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="e3031-126">For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
-   <span data-ttu-id="e3031-127">必須安裝「商務規則引擎」。</span><span class="sxs-lookup"><span data-stu-id="e3031-127">The Business Rule Engine must be installed.</span></span> <span data-ttu-id="e3031-128">如需詳細資訊，請參閱[BizTalk Server 2013 和 2013 R2 的安裝概觀](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)。</span><span class="sxs-lookup"><span data-stu-id="e3031-128">For more information, see [Installation Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5).</span></span>  
  
-   <span data-ttu-id="e3031-129">您所要匯出的原則必須存在於 BizTalk 群組的「規則引擎」資料庫中。</span><span class="sxs-lookup"><span data-stu-id="e3031-129">The policy that you want to export must exist in the Rule Engine database for the BizTalk group.</span></span> <span data-ttu-id="e3031-130">如果要從應用程式匯出原則，就必須也曾經將原則新增到應用程式。</span><span class="sxs-lookup"><span data-stu-id="e3031-130">If you want to export the policy from an application, it must have also been added to the application as well.</span></span>  
  
## <a name="to-export-a-policy"></a><span data-ttu-id="e3031-131">若要匯出原則</span><span class="sxs-lookup"><span data-stu-id="e3031-131">To export a policy</span></span>  
  
#### <a name="using-the-biztalk-server-administration-console"></a><span data-ttu-id="e3031-132">使用 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="e3031-132">Using the BizTalk Server Administration console</span></span>  
  
1.  <span data-ttu-id="e3031-133">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="e3031-133">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="e3031-134">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**並展開 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="e3031-134">In the console tree, expand **BizTalk Server Administration** and expand the BizTalk group.</span></span>  
  
3.  <span data-ttu-id="e3031-135">如果您想要選取要從所有的 BizTalk 群組上按一下滑鼠右鍵在原則匯出的原則**應用程式**資料夾中，按一下 **匯出**，然後按一下 **原則**。</span><span class="sxs-lookup"><span data-stu-id="e3031-135">If you want to select the policies to export from all of the policies in a BizTalk group right-click the **Applications** folder, click **Export**, and then click **Policies**.</span></span>  
  
     <span data-ttu-id="e3031-136">OR</span><span class="sxs-lookup"><span data-stu-id="e3031-136">OR</span></span>  
  
     <span data-ttu-id="e3031-137">如果您想要匯出的原則在特定的應用程式中，展開 應用程式 資料夾、 以滑鼠右鍵按一下應用程式，請按一下**匯出**，然後按一下 **原則**。</span><span class="sxs-lookup"><span data-stu-id="e3031-137">If you want to export the policies in a particular application, expand the Applications folder, right-click the application, click **Export**, and then click **Policies**.</span></span>  
  
     <span data-ttu-id="e3031-138">OR</span><span class="sxs-lookup"><span data-stu-id="e3031-138">OR</span></span>  
  
     <span data-ttu-id="e3031-139">如果您想要匯出特定的原則，按一下 [原則] 資料夾包含此原則，以滑鼠右鍵按一下原則，然後按一下**匯出**。</span><span class="sxs-lookup"><span data-stu-id="e3031-139">If you want to export only a particular policy, click the Policies folder that contains the policy, right-click the policy, and then click **Export**.</span></span>  
  
4.  <span data-ttu-id="e3031-140">在 [匯出原則] 頁面中**要匯出的原則**，選取要匯出的原則。</span><span class="sxs-lookup"><span data-stu-id="e3031-140">On the Export Policies page, in **Policies to export**, select the policies to export.</span></span>  
  
5.  <span data-ttu-id="e3031-141">在**要匯出詞彙**，請選取要匯出詞彙的核取方塊，並清除不想匯出任何詞彙的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e3031-141">In **Vocabularies to export**, select the check boxes of the vocabularies to export, and clear the checkboxes of any vocabularies you do not want to export.</span></span> <span data-ttu-id="e3031-142">由此原則所使用的詞彙都會被自動選取。</span><span class="sxs-lookup"><span data-stu-id="e3031-142">The vocabularies used by this policy are automatically selected.</span></span>  
  
6.  <span data-ttu-id="e3031-143">在**要匯出檔案**中，輸入要匯出原則或原則，XML 檔案的路徑，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="e3031-143">In **File to export** into, type the path of the XML file to which to export the policy or policies, and then click **OK**.</span></span>  
  
#### <a name="using-the-command-line"></a><span data-ttu-id="e3031-144">使用命令列</span><span class="sxs-lookup"><span data-stu-id="e3031-144">Using the command line</span></span>  
  
1.  <span data-ttu-id="e3031-145">使用 BTSTask ListApp 命令與 /ResourceSpec 選項，來產生 XML 檔案，其中列出您想要從中匯出原則中所述的 BizTalk 應用程式中的成品[ListApp 命令](../core/listapp-command.md)。</span><span class="sxs-lookup"><span data-stu-id="e3031-145">Use the BTSTask ListApp command with the /ResourceSpec option to generate an XML file that lists the artifacts in the BizTalk application from which you want to export a policy, as described in [ListApp Command](../core/listapp-command.md).</span></span>  
  
2.  <span data-ttu-id="e3031-146">編輯在上一個步驟中產生的 XML 檔案，並刪除所有的成品 (您要匯出的一個或多個原則除外)。</span><span class="sxs-lookup"><span data-stu-id="e3031-146">Edit the XML file generated in the previous step, deleting all of the artifacts except for the policy or policies that you want to export.</span></span>  
  
3.  <span data-ttu-id="e3031-147">使用 BTSTask ExportApp 命令，為 /ResourceSpec 參數指定修改的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="e3031-147">Use the BTSTask ExportApp command, and specify the modified XML file for the /ResourceSpec parameter.</span></span> <span data-ttu-id="e3031-148">如需詳細資訊，請參閱[ExportApp 命令](../core/exportapp-command.md)。</span><span class="sxs-lookup"><span data-stu-id="e3031-148">For more information, see [ExportApp Command](../core/exportapp-command.md).</span></span>  
  
     <span data-ttu-id="e3031-149">BTSTask 會將指定的原則及其關聯的所有詞彙，都匯出到應用程式 .msi 檔案中。</span><span class="sxs-lookup"><span data-stu-id="e3031-149">BTSTask exports the specified policies and all of their associated vocabularies into an application .msi file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3031-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3031-150">See Also</span></span>  
 <span data-ttu-id="e3031-151">[匯出 BizTalk 應用程式、 繫結和原則](../core/exporting-biztalk-applications-bindings-and-policies.md) </span><span class="sxs-lookup"><span data-stu-id="e3031-151">[Exporting BizTalk Applications, Bindings, and Policies](../core/exporting-biztalk-applications-bindings-and-policies.md) </span></span>  
 [<span data-ttu-id="e3031-152">管理原則</span><span class="sxs-lookup"><span data-stu-id="e3031-152">Managing Policies</span></span>](../core/managing-policies.md)