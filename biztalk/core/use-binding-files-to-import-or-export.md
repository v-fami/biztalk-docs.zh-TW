---
title: 使用繫結檔案匯入或匯出 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9a2a82a-f8d4-4ec2-b8c1-be6cda3f993a
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9ed0f50d6a6d841169b16f3f3ffd485ee345aeb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990591"
---
# <a name="use-binding-files-to-import-or-export"></a><span data-ttu-id="0e012-102">使用繫結檔案匯入或匯出</span><span class="sxs-lookup"><span data-stu-id="0e012-102">Use binding files to import or export</span></span>

<span data-ttu-id="0e012-103">開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]，您可以匯出並匯入繫結檔案，在**合作對象**並**協議**層級。</span><span class="sxs-lookup"><span data-stu-id="0e012-103">Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], you can export and import binding files at the **Parties** and **Agreement** levels.</span></span> <span data-ttu-id="0e012-104">針對先前的 BizTalk 版本，您匯出應用程式層級，就在所述：</span><span class="sxs-lookup"><span data-stu-id="0e012-104">For previous BizTalk versions, you export at the application level, as described at:</span></span> 

* [<span data-ttu-id="0e012-105">如何匯出 EDI-AS2 解決方案的繫結</span><span class="sxs-lookup"><span data-stu-id="0e012-105">How to Export Bindings for an EDI-AS2 Solution</span></span>](../core/how-to-export-bindings-for-an-edi-as2-solution.md)
* [<span data-ttu-id="0e012-106">如何匯入 EDI-AS2 解決方案的繫結</span><span class="sxs-lookup"><span data-stu-id="0e012-106">How to Import Bindings for an EDI-AS2 Solution</span></span>](../core/how-to-import-bindings-for-an-edi-as2-solution.md)

<span data-ttu-id="0e012-107">本主題示範如何匯入和匯出合作對象、 其設定檔、 協議、 後援設定和更多使用[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]和 BTSTask。</span><span class="sxs-lookup"><span data-stu-id="0e012-107">This topic shows you how to import and exports parties, their profiles, agreements, fallback settings, and more using [!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)] and BTSTask.</span></span> 

## <a name="overview"></a><span data-ttu-id="0e012-108">概觀</span><span class="sxs-lookup"><span data-stu-id="0e012-108">Overview</span></span>

<span data-ttu-id="0e012-109">匯入和匯出功能包括：</span><span class="sxs-lookup"><span data-stu-id="0e012-109">Some of the import and export features include:</span></span>

* <span data-ttu-id="0e012-110">從 XML 繫結檔案匯入合作對象、 商務設定檔與協議</span><span class="sxs-lookup"><span data-stu-id="0e012-110">Import parties, business profiles, and agreements from an XML binding file</span></span>
* <span data-ttu-id="0e012-111">將合作對象、 商務設定檔、 協議和 EDI 後援設定匯出到 XML 繫結檔案</span><span class="sxs-lookup"><span data-stu-id="0e012-111">Export parties, business profiles, agreements, and EDI fallback settings to an XML binding file</span></span>
* <span data-ttu-id="0e012-112">匯入繫結檔案時，您可以選擇匯入合作對象或後援設定</span><span class="sxs-lookup"><span data-stu-id="0e012-112">When importing a binding file, you can chose to not import the parties, or the fallback settings</span></span>
* <span data-ttu-id="0e012-113">當匯入合作對象層級，只有合作對象和協議內繫結檔案匯入</span><span class="sxs-lookup"><span data-stu-id="0e012-113">When importing at the Parties-level, only the parties and agreements within the binding file are imported</span></span>
* <span data-ttu-id="0e012-114">將特定合作對象匯出至相同的繫結檔案，並選擇也會匯出這些合作對象相關聯的所有合約</span><span class="sxs-lookup"><span data-stu-id="0e012-114">Export specific parties to the same binding file, and choose to also export all the agreements associated with those parties</span></span>
* <span data-ttu-id="0e012-115">應用程式匯入繫結精靈 可讓您選擇要匯入追蹤設定，或排除合作對象。</span><span class="sxs-lookup"><span data-stu-id="0e012-115">The application import binding wizard lets you choose to import the tracking settings, or exclude the parties.</span></span>
* <span data-ttu-id="0e012-116">包含 BTSTask`ImportParties`和`ExportParties`命令</span><span class="sxs-lookup"><span data-stu-id="0e012-116">BTSTask includes the `ImportParties` and `ExportParties` commands</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="0e012-117">必要條件</span><span class="sxs-lookup"><span data-stu-id="0e012-117">Prerequisites</span></span>

* <span data-ttu-id="0e012-118">您必須以成員的帳戶登入 * * BizTalk Server 系統管理員 」 群組。</span><span class="sxs-lookup"><span data-stu-id="0e012-118">You must be logged on with an account that is a member of the** BizTalk Server Administrators** group.</span></span> <span data-ttu-id="0e012-119">請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="0e012-119">See [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  

* <span data-ttu-id="0e012-120">您必須新增的參考**BizTalk EDI 應用程式**從 BizTalk 應用程式將用於做為 EDI 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0e012-120">You must have added a reference to the **BizTalk EDI Application** from a BizTalk application that will be used as an EDI application.</span></span> <span data-ttu-id="0e012-121">請參閱[後續設定步驟](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="0e012-121">See [Post-configuration steps](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md).</span></span>

## <a name="import-or-export-all-the-trading-partners"></a><span data-ttu-id="0e012-122">匯入或匯出所有交易夥伴</span><span class="sxs-lookup"><span data-stu-id="0e012-122">Import or export all the trading partners</span></span>
1. <span data-ttu-id="0e012-123">開啟**[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]**，再展開 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="0e012-123">Open **[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]**, and expand the BizTalk group.</span></span>
2. <span data-ttu-id="0e012-124">以滑鼠右鍵按一下**合作對象**，然後選取**匯出**。</span><span class="sxs-lookup"><span data-stu-id="0e012-124">Right-click **Parties**, and select **Export**.</span></span> 

    <span data-ttu-id="0e012-125">當您匯出動作目前**合作對象**-層級，您要匯出所有交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="0e012-125">When you export at the **parties**-level, you are exporting all the trading partners.</span></span> <span data-ttu-id="0e012-126">這也會匯出交易夥伴，包括商務設定檔與協議到 XML 檔案所使用的所有項目。</span><span class="sxs-lookup"><span data-stu-id="0e012-126">This also exports everything used by the trading partners, including business profiles, and agreements into an XML file.</span></span> 

3. <span data-ttu-id="0e012-127">以滑鼠右鍵按一下**合作對象**，選取**匯入**，然後選取繫結 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="0e012-127">Right-click **Parties**, select **Import**, and select the binding XML file.</span></span> 

      <span data-ttu-id="0e012-128">若要選擇**排除合作對象**，或**排除 EDI 後援設定**讓它們不會匯入。</span><span class="sxs-lookup"><span data-stu-id="0e012-128">Choose to **Exclude Parties**, or **Exclude EDI Fallback Settings** so they are not imported.</span></span> <span data-ttu-id="0e012-129">否則，繫結檔案中的所有項目會匯入，包括交易夥伴、 商務設定檔與協議。</span><span class="sxs-lookup"><span data-stu-id="0e012-129">Otherwise, everything in the binding file is imported, including the trading partners, business profiles, and agreements.</span></span>     

### <a name="btstask-example"></a><span data-ttu-id="0e012-130">BTSTask 範例</span><span class="sxs-lookup"><span data-stu-id="0e012-130">BTSTask example</span></span>

`BTSTask ImportParties  -Source:"C:\Temp\MyParties.Xml" -ExcludeEdiFallbackSettings`

<span data-ttu-id="0e012-131">請參閱[ImportParties 命令](../core/importparties-command.md)。</span><span class="sxs-lookup"><span data-stu-id="0e012-131">See [ImportParties command](../core/importparties-command.md).</span></span>

    
## <a name="export-individual-partners"></a><span data-ttu-id="0e012-132">匯出個別的合作夥伴</span><span class="sxs-lookup"><span data-stu-id="0e012-132">Export individual partners</span></span>
1. <span data-ttu-id="0e012-133">在  **[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]**，選取**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="0e012-133">In **[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]**, select **Parties**.</span></span>
2. <span data-ttu-id="0e012-134">在 **合作對象與商務設定檔**窗格中，以滑鼠右鍵按一下合作對象，然後選取**匯出**。</span><span class="sxs-lookup"><span data-stu-id="0e012-134">In the **Parties and business profiles** pane, right-click a party, and select **Export**.</span></span>

    <span data-ttu-id="0e012-135">當您匯出特定合作對象時，您可以選擇要匯出所有的合作對象，並使用該合作對象的協議。</span><span class="sxs-lookup"><span data-stu-id="0e012-135">When you export a specific party, you are given the choice to export all the parties, and all the agreements used by that party.</span></span> <span data-ttu-id="0e012-136">您可以取消勾選**匯出選取的合作對象與選取的合作對象中的所有合約**只匯出您所選取的合作對象。</span><span class="sxs-lookup"><span data-stu-id="0e012-136">You can uncheck **Export selected parties and all the agreements within the selected parties** to only export the party you select.</span></span>

3. <span data-ttu-id="0e012-137">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="0e012-137">Select **OK**.</span></span> 

> [!TIP]
> <span data-ttu-id="0e012-138">在**合作對象與商務設定檔**窗格中，您也可以使用**CTRL**並**Shift**清單中選取多個合作對象的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="0e012-138">In the **Parties and business profiles** pane, you can also use the **CTRL** and **Shift** keys to select multiple parties in the list.</span></span> <span data-ttu-id="0e012-139">您選取的合作對象的所有匯出至相同的繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="0e012-139">All of the parties you select export into the same binding file.</span></span>

### <a name="btstask-example"></a><span data-ttu-id="0e012-140">BTSTask 範例</span><span class="sxs-lookup"><span data-stu-id="0e012-140">BTSTask example</span></span>

`BTSTask ExportParties -Destination:"C:\Temp\MyParties.Xml"`

<span data-ttu-id="0e012-141">請參閱[ExportParties 命令](../core/exportparties-command.md)。</span><span class="sxs-lookup"><span data-stu-id="0e012-141">See [ExportParties command](../core/exportparties-command.md).</span></span>


## <a name="import-application-binding-file"></a><span data-ttu-id="0e012-142">匯入應用程式繫結檔案</span><span class="sxs-lookup"><span data-stu-id="0e012-142">Import application binding file</span></span>

<span data-ttu-id="0e012-143">在應用程式層級，您可以將繫結檔案匯入與 EDI 和 AS2 合作對象。</span><span class="sxs-lookup"><span data-stu-id="0e012-143">At the application-level, you can import a binding file with EDI and AS2 parties.</span></span> 

1. <span data-ttu-id="0e012-144">在  **[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]**，展開 **應用程式**</span><span class="sxs-lookup"><span data-stu-id="0e012-144">In **[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]**, expand **Applications**</span></span>
2. <span data-ttu-id="0e012-145">以滑鼠右鍵按一下您的應用程式，然後選取**匯入**。</span><span class="sxs-lookup"><span data-stu-id="0e012-145">Right-click your application, and select **Import**.</span></span>
3. <span data-ttu-id="0e012-146">**匯入追蹤設定**並**排除合作對象**選項可用。</span><span class="sxs-lookup"><span data-stu-id="0e012-146">**Import Tracking Settings** and **Exclude Parties** options are available.</span></span> <span data-ttu-id="0e012-147">使用這些選項，您可以選擇要匯入任何現有的追蹤設定，或排除繫結檔案中的任何 EDI/AS2 合作對象。</span><span class="sxs-lookup"><span data-stu-id="0e012-147">Using these options, you can choose to import any existing tracking settings, or exclude any EDI/AS2 parties within the binding file.</span></span>

    | <span data-ttu-id="0e012-148">設定</span><span class="sxs-lookup"><span data-stu-id="0e012-148">Setting</span></span> | <span data-ttu-id="0e012-149">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0e012-149">Details</span></span> |
    |---|---|
    |<span data-ttu-id="0e012-150">**匯入追蹤設定**</span><span class="sxs-lookup"><span data-stu-id="0e012-150">**Import Tracking Settings**</span></span> | <span data-ttu-id="0e012-151">匯入應用程式，例如追蹤訊息內文，以及追蹤事件內的不同成品上啟用的追蹤設定。</span><span class="sxs-lookup"><span data-stu-id="0e012-151">Imports the tracking settings enabled on the different artifacts within the application, such as track message bodies, and track events.</span></span> <br/><br/><span data-ttu-id="0e012-152">依預設啟用，以確保回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="0e012-152">Enabled by default to ensure backwards-compatibility.</span></span> |
    | <span data-ttu-id="0e012-153">**排除合作對象**</span><span class="sxs-lookup"><span data-stu-id="0e012-153">**Exclude Parties**</span></span>|<span data-ttu-id="0e012-154">執行檔案中現有的未匯入合作對象、 設定檔與協議。</span><span class="sxs-lookup"><span data-stu-id="0e012-154">Does not import parties, profiles, and agreements that existing within the file.</span></span> <br/><br/><span data-ttu-id="0e012-155">為了確保回溯相容性的預設為停用。</span><span class="sxs-lookup"><span data-stu-id="0e012-155">Disabled by default to ensure backwards-compatibility.</span></span>|

   > [!IMPORTANT]
   > <span data-ttu-id="0e012-156">全域追蹤設定會覆寫**匯入追蹤設定**。</span><span class="sxs-lookup"><span data-stu-id="0e012-156">The global tracking settings override **Import Tracking Settings**.</span></span> <span data-ttu-id="0e012-157">因此如果您已停用追蹤，在全域層級，任何追蹤設定不會匯入，即使**匯入追蹤設定**已核取。</span><span class="sxs-lookup"><span data-stu-id="0e012-157">So if you've disabled tracking at the global level, any tracking settings are not imported, even if **Import Tracking Settings** is checked.</span></span>
   > 
   > <span data-ttu-id="0e012-158">**BizTalk 設定儀表板，群組頁面**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]說明**允許匯入追蹤設定**全域設定。</span><span class="sxs-lookup"><span data-stu-id="0e012-158">**BizTalk Settings Dashboard, Group Page** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] explains the **Allow import of tracking settings** global setting.</span></span>

### <a name="btstask-example"></a><span data-ttu-id="0e012-159">BTSTask 範例</span><span class="sxs-lookup"><span data-stu-id="0e012-159">BTSTask example</span></span>

`BTSTask ImportBindings -ApplicationName:MyApplication -Source:C:\Bindings\Binding1.xml -ImportTrackingSettings:true`

<span data-ttu-id="0e012-160">請參閱[ImportBindings 命令](../core/importbindings-command.md)。</span><span class="sxs-lookup"><span data-stu-id="0e012-160">See [ImportBindings command](../core/importbindings-command.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="0e012-161">本節內容</span><span class="sxs-lookup"><span data-stu-id="0e012-161">In this section</span></span>
<span data-ttu-id="0e012-162">若要匯入或匯出舊版 BizTalk EDI 和 AS2 繫結檔案，請參閱：</span><span class="sxs-lookup"><span data-stu-id="0e012-162">To import or export EDI and AS2 binding files on previous BizTalk versions, see:</span></span> 

* [<span data-ttu-id="0e012-163">如何匯出 EDI-AS2 解決方案的繫結</span><span class="sxs-lookup"><span data-stu-id="0e012-163">How to Export Bindings for an EDI-AS2 Solution</span></span>](../core/how-to-export-bindings-for-an-edi-as2-solution.md)
* [<span data-ttu-id="0e012-164">如何匯入 EDI-AS2 解決方案的繫結</span><span class="sxs-lookup"><span data-stu-id="0e012-164">How to Import Bindings for an EDI-AS2 Solution</span></span>](../core/how-to-import-bindings-for-an-edi-as2-solution.md)
