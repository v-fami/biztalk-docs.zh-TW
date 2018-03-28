---
title: 使用繫結檔案匯入或匯出 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9a2a82a-f8d4-4ec2-b8c1-be6cda3f993a
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3707726eb9e8e77e0536f36700fe098d83ad414
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="use-binding-files-to-import-or-export"></a><span data-ttu-id="d7b04-102">使用繫結檔案匯入或匯出</span><span class="sxs-lookup"><span data-stu-id="d7b04-102">Use binding files to import or export</span></span>

<span data-ttu-id="d7b04-103">從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]，您可以匯出並匯入繫結檔案，在**合作對象**和**協議**層級。</span><span class="sxs-lookup"><span data-stu-id="d7b04-103">Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], you can export and import binding files at the **Parties** and **Agreement** levels.</span></span> <span data-ttu-id="d7b04-104">BizTalk 舊版，您將匯出應用程式層級，如下所述：</span><span class="sxs-lookup"><span data-stu-id="d7b04-104">For previous BizTalk versions, you export at the application level, as described at:</span></span> 

* [<span data-ttu-id="d7b04-105">如何匯出 EDI AS2 方案的繫結</span><span class="sxs-lookup"><span data-stu-id="d7b04-105">How to Export Bindings for an EDI-AS2 Solution</span></span>](../core/how-to-export-bindings-for-an-edi-as2-solution.md)
* [<span data-ttu-id="d7b04-106">如何匯入 EDI AS2 方案的繫結</span><span class="sxs-lookup"><span data-stu-id="d7b04-106">How to Import Bindings for an EDI-AS2 Solution</span></span>](../core/how-to-import-bindings-for-an-edi-as2-solution.md)

<span data-ttu-id="d7b04-107">本主題說明如何匯入和匯出合作對象、 其設定檔、 協議、 後援設定，以及更多使用[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]和 BTSTask。</span><span class="sxs-lookup"><span data-stu-id="d7b04-107">This topic shows you how to import and exports parties, their profiles, agreements, fallback settings, and more using [!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)] and BTSTask.</span></span> 

## <a name="overview"></a><span data-ttu-id="d7b04-108">概觀</span><span class="sxs-lookup"><span data-stu-id="d7b04-108">Overview</span></span>

<span data-ttu-id="d7b04-109">匯入和匯出功能包括：</span><span class="sxs-lookup"><span data-stu-id="d7b04-109">Some of the import and export features include:</span></span>

* <span data-ttu-id="d7b04-110">從 XML 繫結檔案匯入的合作對象、 商務設定檔以及協議</span><span class="sxs-lookup"><span data-stu-id="d7b04-110">Import parties, business profiles, and agreements from an XML binding file</span></span>
* <span data-ttu-id="d7b04-111">將合作對象、 商務設定檔、 協議和 EDI 後援設定匯出到 XML 繫結檔案</span><span class="sxs-lookup"><span data-stu-id="d7b04-111">Export parties, business profiles, agreements, and EDI fallback settings to an XML binding file</span></span>
* <span data-ttu-id="d7b04-112">匯入繫結檔案時，您可以選擇匯入合作對象或後援設定</span><span class="sxs-lookup"><span data-stu-id="d7b04-112">When importing a binding file, you can chose to not import the parties, or the fallback settings</span></span>
* <span data-ttu-id="d7b04-113">當匯入在合作對象層級，只有合作對象和協議內繫結檔案匯入</span><span class="sxs-lookup"><span data-stu-id="d7b04-113">When importing at the Parties-level, only the parties and agreements within the binding file are imported</span></span>
* <span data-ttu-id="d7b04-114">相同的繫結檔案匯出特定合作對象，並選擇也會匯出這些合作對象相關聯的所有合約</span><span class="sxs-lookup"><span data-stu-id="d7b04-114">Export specific parties to the same binding file, and choose to also export all the agreements associated with those parties</span></span>
* <span data-ttu-id="d7b04-115">應用程式匯入繫結精靈可讓您選擇要匯入的追蹤設定，或排除的合作對象。</span><span class="sxs-lookup"><span data-stu-id="d7b04-115">The application import binding wizard lets you choose to import the tracking settings, or exclude the parties.</span></span>
* <span data-ttu-id="d7b04-116">BTSTask 包含`ImportParties`和`ExportParties`命令</span><span class="sxs-lookup"><span data-stu-id="d7b04-116">BTSTask includes the `ImportParties` and `ExportParties` commands</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="d7b04-117">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="d7b04-117">Prerequisites</span></span>

* <span data-ttu-id="d7b04-118">您必須以成員的帳戶登入 * * BizTalk Server 系統管理員 * * 群組。</span><span class="sxs-lookup"><span data-stu-id="d7b04-118">You must be logged on with an account that is a member of the** BizTalk Server Administrators** group.</span></span> <span data-ttu-id="d7b04-119">請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="d7b04-119">See [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  

* <span data-ttu-id="d7b04-120">您必須新增參考 **BizTalk EDI 應用程式** 從 BizTalk 應用程式將會做為 EDI 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d7b04-120">You must have added a reference to the **BizTalk EDI Application** from a BizTalk application that will be used as an EDI application.</span></span> <span data-ttu-id="d7b04-121">請參閱[後設定步驟](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="d7b04-121">See [Post-configuration steps](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md).</span></span>

## <a name="import-or-export-all-the-trading-partners"></a><span data-ttu-id="d7b04-122">匯入或匯出所有交易夥伴</span><span class="sxs-lookup"><span data-stu-id="d7b04-122">Import or export all the trading partners</span></span>
1. <span data-ttu-id="d7b04-123">開啟**[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]**，再展開 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="d7b04-123">Open **[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]**, and expand the BizTalk group.</span></span>
2. <span data-ttu-id="d7b04-124">以滑鼠右鍵按一下**合作對象**，然後選取**匯出**。</span><span class="sxs-lookup"><span data-stu-id="d7b04-124">Right-click **Parties**, and select **Export**.</span></span> 

    <span data-ttu-id="d7b04-125">當您匯出在**合作對象**-層級，您要匯出所有交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="d7b04-125">When you export at the **parties**-level, you are exporting all the trading partners.</span></span> <span data-ttu-id="d7b04-126">這也會匯出交易夥伴，包括商務設定檔和協議到 XML 檔案所使用的所有項目。</span><span class="sxs-lookup"><span data-stu-id="d7b04-126">This also exports everything used by the trading partners, including business profiles, and agreements into an XML file.</span></span> 

3. <span data-ttu-id="d7b04-127">以滑鼠右鍵按一下**合作對象**，選取**匯入**，然後選取 繫結的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="d7b04-127">Right-click **Parties**, select **Import**, and select the binding XML file.</span></span> 

      <span data-ttu-id="d7b04-128">選擇**排除合作對象**，或**排除 EDI 後援設定**讓它們不會匯入。</span><span class="sxs-lookup"><span data-stu-id="d7b04-128">Choose to **Exclude Parties**, or **Exclude EDI Fallback Settings** so they are not imported.</span></span> <span data-ttu-id="d7b04-129">否則，繫結檔案中的所有項目會匯入，包括交易夥伴、 商務設定檔和協議。</span><span class="sxs-lookup"><span data-stu-id="d7b04-129">Otherwise, everything in the binding file is imported, including the trading partners, business profiles, and agreements.</span></span>     

### <a name="btstask-example"></a><span data-ttu-id="d7b04-130">BTSTask 範例</span><span class="sxs-lookup"><span data-stu-id="d7b04-130">BTSTask example</span></span>

`BTSTask ImportParties  -Source:"C:\Temp\MyParties.Xml" -ExcludeEdiFallbackSettings`

<span data-ttu-id="d7b04-131">請參閱[ImportParties 命令](../core/importparties-command.md)。</span><span class="sxs-lookup"><span data-stu-id="d7b04-131">See [ImportParties command](../core/importparties-command.md).</span></span>

    
## <a name="export-individual-partners"></a><span data-ttu-id="d7b04-132">匯出個別的夥伴</span><span class="sxs-lookup"><span data-stu-id="d7b04-132">Export individual partners</span></span>
1. <span data-ttu-id="d7b04-133">在**[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]**，選取**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="d7b04-133">In **[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]**, select **Parties**.</span></span>
2. <span data-ttu-id="d7b04-134">在**合作對象與商務設定檔** 窗格中，以滑鼠右鍵按一下合作對象，然後選取**匯出**。</span><span class="sxs-lookup"><span data-stu-id="d7b04-134">In the **Parties and business profiles** pane, right-click a party, and select **Export**.</span></span>

    <span data-ttu-id="d7b04-135">當您匯出特定合作對象時，您可以選擇要匯出所有的合作對象，與該合作對象所使用的所有合約。</span><span class="sxs-lookup"><span data-stu-id="d7b04-135">When you export a specific party, you are given the choice to export all the parties, and all the agreements used by that party.</span></span> <span data-ttu-id="d7b04-136">您可以取消核取**匯出選取的合作對象與選取的合作對象內的所有合約**只匯出選取的合作對象。</span><span class="sxs-lookup"><span data-stu-id="d7b04-136">You can uncheck **Export selected parties and all the agreements within the selected parties** to only export the party you select.</span></span>

3. <span data-ttu-id="d7b04-137">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="d7b04-137">Select **OK**.</span></span> 

> [!TIP]
> <span data-ttu-id="d7b04-138">在**合作對象與商務設定檔** 窗格中，您也可以使用**CTRL**和**Shift**清單中選取多個合作對象的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="d7b04-138">In the **Parties and business profiles** pane, you can also use the **CTRL** and **Shift** keys to select multiple parties in the list.</span></span> <span data-ttu-id="d7b04-139">您選取的合作對象的所有匯出至相同的繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="d7b04-139">All of the parties you select export into the same binding file.</span></span>

### <a name="btstask-example"></a><span data-ttu-id="d7b04-140">BTSTask 範例</span><span class="sxs-lookup"><span data-stu-id="d7b04-140">BTSTask example</span></span>

`BTSTask ExportParties -Destination:"C:\Temp\MyParties.Xml"`

<span data-ttu-id="d7b04-141">請參閱[ExportParties 命令](../core/exportparties-command.md)。</span><span class="sxs-lookup"><span data-stu-id="d7b04-141">See [ExportParties command](../core/exportparties-command.md).</span></span>


## <a name="import-application-binding-file"></a><span data-ttu-id="d7b04-142">匯入應用程式繫結檔案</span><span class="sxs-lookup"><span data-stu-id="d7b04-142">Import application binding file</span></span>

<span data-ttu-id="d7b04-143">在應用程式層級，您可以將繫結檔案匯入與 EDI 和 AS2 合作對象。</span><span class="sxs-lookup"><span data-stu-id="d7b04-143">At the application-level, you can import a binding file with EDI and AS2 parties.</span></span> 

1. <span data-ttu-id="d7b04-144">在**[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]**，依序展開**應用程式**</span><span class="sxs-lookup"><span data-stu-id="d7b04-144">In **[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]**, expand **Applications**</span></span>
2. <span data-ttu-id="d7b04-145">以滑鼠右鍵按一下您的應用程式，然後選取**匯入**。</span><span class="sxs-lookup"><span data-stu-id="d7b04-145">Right-click your application, and select **Import**.</span></span>
3. <span data-ttu-id="d7b04-146">**追蹤設定匯入**和**排除合作對象**可用選項。</span><span class="sxs-lookup"><span data-stu-id="d7b04-146">**Import Tracking Settings** and **Exclude Parties** options are available.</span></span> <span data-ttu-id="d7b04-147">使用這些選項，您可以選擇要匯入任何現有的追蹤設定，或排除任何 EDI/AS2 合作對象繫結檔案中。</span><span class="sxs-lookup"><span data-stu-id="d7b04-147">Using these options, you can choose to import any existing tracking settings, or exclude any EDI/AS2 parties within the binding file.</span></span>

    | <span data-ttu-id="d7b04-148">設定</span><span class="sxs-lookup"><span data-stu-id="d7b04-148">Setting</span></span> | <span data-ttu-id="d7b04-149">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d7b04-149">Details</span></span> |
    |---|---|
    |<span data-ttu-id="d7b04-150">**追蹤設定匯入**</span><span class="sxs-lookup"><span data-stu-id="d7b04-150">**Import Tracking Settings**</span></span> | <span data-ttu-id="d7b04-151">匯入應用程式，例如追蹤訊息內文和追蹤事件中的不同成品上啟用的追蹤設定。</span><span class="sxs-lookup"><span data-stu-id="d7b04-151">Imports the tracking settings enabled on the different artifacts within the application, such as track message bodies, and track events.</span></span> <br/><br/><span data-ttu-id="d7b04-152">依預設啟用，以確保回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="d7b04-152">Enabled by default to ensure backwards-compatibility.</span></span> |
    | <span data-ttu-id="d7b04-153">**排除合作對象**</span><span class="sxs-lookup"><span data-stu-id="d7b04-153">**Exclude Parties**</span></span>|<span data-ttu-id="d7b04-154">執行檔案中現有的未匯入合作對象、 設定檔以及協議。</span><span class="sxs-lookup"><span data-stu-id="d7b04-154">Does not import parties, profiles, and agreements that existing within the file.</span></span> <br/><br/><span data-ttu-id="d7b04-155">預設為停用來確保回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="d7b04-155">Disabled by default to ensure backwards-compatibility.</span></span>|

     > [!IMPORTANT] 
     > <span data-ttu-id="d7b04-156">全域追蹤設定會覆寫**匯入追蹤設定**。</span><span class="sxs-lookup"><span data-stu-id="d7b04-156">The global tracking settings override **Import Tracking Settings**.</span></span> <span data-ttu-id="d7b04-157">因此如果您已停用追蹤在全域層級，任何追蹤設定不會匯入，即使**匯入追蹤設定**已核取。</span><span class="sxs-lookup"><span data-stu-id="d7b04-157">So if you've disabled tracking at the global level, any tracking settings are not imported, even if **Import Tracking Settings** is checked.</span></span>
     > 
     > <span data-ttu-id="d7b04-158">**BizTalk 設定儀表板，群組頁面**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]說明**允許的追蹤設定匯入**全域設定。</span><span class="sxs-lookup"><span data-stu-id="d7b04-158">**BizTalk Settings Dashboard, Group Page** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] explains the **Allow import of tracking settings** global setting.</span></span>

### <a name="btstask-example"></a><span data-ttu-id="d7b04-159">BTSTask 範例</span><span class="sxs-lookup"><span data-stu-id="d7b04-159">BTSTask example</span></span>

`BTSTask ImportBindings -ApplicationName:MyApplication -Source:C:\Bindings\Binding1.xml -ImportTrackingSettings:true`

<span data-ttu-id="d7b04-160">請參閱[ImportBindings 命令](../core/importbindings-command.md)。</span><span class="sxs-lookup"><span data-stu-id="d7b04-160">See [ImportBindings command](../core/importbindings-command.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d7b04-161">本節內容</span><span class="sxs-lookup"><span data-stu-id="d7b04-161">In this section</span></span>
<span data-ttu-id="d7b04-162">若要匯入或匯出在舊版的 BizTalk EDI 和 AS2 繫結檔案，請參閱：</span><span class="sxs-lookup"><span data-stu-id="d7b04-162">To import or export EDI and AS2 binding files on previous BizTalk versions, see:</span></span> 

* [<span data-ttu-id="d7b04-163">如何匯出 EDI AS2 方案的繫結</span><span class="sxs-lookup"><span data-stu-id="d7b04-163">How to Export Bindings for an EDI-AS2 Solution</span></span>](../core/how-to-export-bindings-for-an-edi-as2-solution.md)
* [<span data-ttu-id="d7b04-164">如何匯入 EDI AS2 方案的繫結</span><span class="sxs-lookup"><span data-stu-id="d7b04-164">How to Import Bindings for an EDI-AS2 Solution</span></span>](../core/how-to-import-bindings-for-an-edi-as2-solution.md)
