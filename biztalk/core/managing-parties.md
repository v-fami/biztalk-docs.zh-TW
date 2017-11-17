---
title: "管理合作對象 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.admin.resultsobject.party
helpviewer_keywords:
- Administration Console [BizTalk Server], parties
- managing [parties]
- managing [parties], about managing parties
- parties, managing
ms.assetid: 96d2bcb3-1e38-4dad-a0d6-e5913ba531e7
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06f0c552b84fd8c4f56e2a88c59e8557585c947e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="managing-parties"></a><span data-ttu-id="ac00d-102">管理合作對象</span><span class="sxs-lookup"><span data-stu-id="ac00d-102">Managing Parties</span></span>
<span data-ttu-id="ac00d-103">使用**合作對象**節點，您可以設定商務夥伴 （合作對象） 或內部部門 （商務設定檔） 與[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]解決方案互動。</span><span class="sxs-lookup"><span data-stu-id="ac00d-103">Using the **Parties** node, you can set up business partners (parties) or internal departments (business profiles) with which [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solutions interact.</span></span> <span data-ttu-id="ac00d-104">如需詳細資訊，請參閱[交易夥伴](../core/trading-partners-and-business-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="ac00d-104">For more information, see [Trading Partners](../core/trading-partners-and-business-profiles.md).</span></span>  

<span data-ttu-id="ac00d-105">您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台來建立和設定合作對象。</span><span class="sxs-lookup"><span data-stu-id="ac00d-105">You can create and configure a party using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span> <span data-ttu-id="ac00d-106">在 BizTalk Server 中建立合作對象之後，您可能會想使用協調流程與合作對象互動。</span><span class="sxs-lookup"><span data-stu-id="ac00d-106">After you create a party in BizTalk Server, it is likely that you want to interact with that party using an orchestration.</span></span> <span data-ttu-id="ac00d-107">合作對象可透過角色與協調流程互動。</span><span class="sxs-lookup"><span data-stu-id="ac00d-107">Parties interact with orchestrations through roles.</span></span> <span data-ttu-id="ac00d-108">例如，協調流程中可能有託運角色。</span><span class="sxs-lookup"><span data-stu-id="ac00d-108">For example, you might have a shipping role in your orchestration.</span></span> <span data-ttu-id="ac00d-109">與託運商相關聯的合作對象可能有一或兩個。</span><span class="sxs-lookup"><span data-stu-id="ac00d-109">The shipper would have one or more parties associated with it.</span></span> <span data-ttu-id="ac00d-110">當協調流程需要決定僱用最便宜的託運公司來運送項目時，它可以比較託運商角色中合作對象的價格。</span><span class="sxs-lookup"><span data-stu-id="ac00d-110">When the orchestration needs to decide the least expensive shipping company to use to ship an item, it can compare the prices of the parties in the shipper role.</span></span>  
  
 <span data-ttu-id="ac00d-111">您必須登錄合作對象，使其與特定角色繫結。</span><span class="sxs-lookup"><span data-stu-id="ac00d-111">You must enlist a party to tie it to a specific role.</span></span> <span data-ttu-id="ac00d-112">登錄角色可讓協調流程與合作對象互動。</span><span class="sxs-lookup"><span data-stu-id="ac00d-112">Enlisting a party enables an orchestration to interact with the party.</span></span> <span data-ttu-id="ac00d-113">請參閱[如何登錄或取消登錄角色的合作對象](../core/how-to-enlist-or-unenlist-a-party-for-a-role.md)。</span><span class="sxs-lookup"><span data-stu-id="ac00d-113">See [How to Enlist or Unenlist a Party for a Role](../core/how-to-enlist-or-unenlist-a-party-for-a-role.md).</span></span>
 
## <a name="prerequisites"></a><span data-ttu-id="ac00d-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="ac00d-114">Prerequisites</span></span>  
 <span data-ttu-id="ac00d-115">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="ac00d-115">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
## <a name="create-or-edit-a-party"></a><span data-ttu-id="ac00d-116">建立或編輯合作對象</span><span class="sxs-lookup"><span data-stu-id="ac00d-116">Create or edit a party</span></span>
  
1.  <span data-ttu-id="ac00d-117">開啟 [BizTalk Server 管理] 。</span><span class="sxs-lookup"><span data-stu-id="ac00d-117">Open **BizTalk Server Administration**.</span></span>  <span data-ttu-id="ac00d-118">展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、 依序展開 BizTalk 群組、 以滑鼠右鍵按一下**合作對象**，選取**新增**，然後選取**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="ac00d-118">Expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, right-click **Parties**, select **New**, and then select **Party**.</span></span>  
  
2.  <span data-ttu-id="ac00d-119">在**一般**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ac00d-119">On the **General** page, do the following:</span></span>  
  
    |<span data-ttu-id="ac00d-120">使用</span><span class="sxs-lookup"><span data-stu-id="ac00d-120">Use this</span></span>|<span data-ttu-id="ac00d-121">動作</span><span class="sxs-lookup"><span data-stu-id="ac00d-121">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="ac00d-122">**名稱**</span><span class="sxs-lookup"><span data-stu-id="ac00d-122">**Name**</span></span>|<span data-ttu-id="ac00d-123">輸入合作對象名稱。</span><span class="sxs-lookup"><span data-stu-id="ac00d-123">Enter a party name.</span></span>|  
    |<span data-ttu-id="ac00d-124">**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**</span><span class="sxs-lookup"><span data-stu-id="ac00d-124">**Local BizTalk processes messages received by the party or supports sending messages from this party**</span></span>|<span data-ttu-id="ac00d-125">選取此核取方塊，以指定合作對象代表同時裝載了 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的同一個交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="ac00d-125">Select this checkbox to specify that the party represents the same trading partner that also hosts [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="ac00d-126">**重要事項：**對於兩個合作對象 TPM 解決方案會使用管線的方塊外，隨附於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您必須選取此核取方塊，至少一個合作對象。</span><span class="sxs-lookup"><span data-stu-id="ac00d-126">**Important:**  For a two-party TPM solution that uses out-of-the-box pipelines shipped with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you must select this check box for at least one party.</span></span> <span data-ttu-id="ac00d-127">**注意：**某些屬性如果您清除此核取方塊，將會停用時建立此合作對象的協議。</span><span class="sxs-lookup"><span data-stu-id="ac00d-127">**Note:**  If you clear this check box, some properties will be disabled while creating the agreements for this party.</span></span>|  
    |<span data-ttu-id="ac00d-128">**其他屬性 – 名稱/值**</span><span class="sxs-lookup"><span data-stu-id="ac00d-128">**Additional Properties – Name / Value**</span></span>|<span data-ttu-id="ac00d-129">請輸入名稱-值組來儲存合作對象的任何資訊。</span><span class="sxs-lookup"><span data-stu-id="ac00d-129">Enter a name-value pair to store any information about the party.</span></span> <span data-ttu-id="ac00d-130">您可以視需要新增任意數目的名稱-值組。</span><span class="sxs-lookup"><span data-stu-id="ac00d-130">You can add as many name-value pairs as you want.</span></span> <span data-ttu-id="ac00d-131">**請注意**： 名稱 / 值組不會由 BizTalk Server 進行任何處理; 此資料僅供資訊。</span><span class="sxs-lookup"><span data-stu-id="ac00d-131">**Note**:  The name-value pairs are not used by the BizTalk Server for any processing; this data is for information purposes only.</span></span>|  
    |<span data-ttu-id="ac00d-132">**Delete**</span><span class="sxs-lookup"><span data-stu-id="ac00d-132">**Delete**</span></span>|<span data-ttu-id="ac00d-133">選取即可刪除選取的名稱 / 值組。</span><span class="sxs-lookup"><span data-stu-id="ac00d-133">Select to delete the selected name-value pair.</span></span>|  
  
3.  <span data-ttu-id="ac00d-134">在**傳送埠**頁面上，執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="ac00d-134">On the **Send Ports** page, do the following.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ac00d-135">在 [!INCLUDE[prague](../includes/prague-md.md)] 中，設定相關傳送埠的動作是在協議層級進行。</span><span class="sxs-lookup"><span data-stu-id="ac00d-135">In [!INCLUDE[prague](../includes/prague-md.md)], the send port association is done at the agreement level.</span></span> <span data-ttu-id="ac00d-136">**傳送埠**可用為合作對象屬性的一部分是純粹是為了回溯相容性 頁面。</span><span class="sxs-lookup"><span data-stu-id="ac00d-136">The **Send Ports** page available as part of the party properties is purely for backward compatibility.</span></span> <span data-ttu-id="ac00d-137">當您將傳送埠與協議相關聯後，傳送埠設定也會傳播到合作對象設定，而您就可以在此頁面看到該傳送埠關聯。</span><span class="sxs-lookup"><span data-stu-id="ac00d-137">Whenever you associate a send port with an agreement, the send port setting is also propagated to the party setting and you can see the send port association in this page as well.</span></span> <span data-ttu-id="ac00d-138">但是，並非反之亦然。</span><span class="sxs-lookup"><span data-stu-id="ac00d-138">However, the reverse is not true.</span></span> <span data-ttu-id="ac00d-139">在您將傳送埠與合作夥伴相關聯後，該傳送埠無法自動出現在協議設定中。</span><span class="sxs-lookup"><span data-stu-id="ac00d-139">You cannot associate a send port with a party and then have that send port be automatically available as part of the agreement settings.</span></span>  
  
    |<span data-ttu-id="ac00d-140">使用</span><span class="sxs-lookup"><span data-stu-id="ac00d-140">Use this</span></span>|<span data-ttu-id="ac00d-141">動作</span><span class="sxs-lookup"><span data-stu-id="ac00d-141">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="ac00d-142">**傳送埠-名稱**</span><span class="sxs-lookup"><span data-stu-id="ac00d-142">**Send ports - Name**</span></span>|<span data-ttu-id="ac00d-143">從下拉式清單選取要繫結至此合作對象的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="ac00d-143">From the drop-down list, select a send port to bind to this party.</span></span>|  
    |<span data-ttu-id="ac00d-144">**傳送埠-URI**</span><span class="sxs-lookup"><span data-stu-id="ac00d-144">**Send ports - URI**</span></span>|<span data-ttu-id="ac00d-145">顯示傳送埠位址。</span><span class="sxs-lookup"><span data-stu-id="ac00d-145">Displays the send port address.</span></span>|  
    |<span data-ttu-id="ac00d-146">**移除**</span><span class="sxs-lookup"><span data-stu-id="ac00d-146">**Remove**</span></span>|<span data-ttu-id="ac00d-147">選取此選項，以從合作對象移除選取的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="ac00d-147">Select to remove the selected send port from the party.</span></span>|  
    |<span data-ttu-id="ac00d-148">**屬性**</span><span class="sxs-lookup"><span data-stu-id="ac00d-148">**Properties**</span></span>|<span data-ttu-id="ac00d-149">選取即可顯示**傳送埠屬性**選取的傳送埠 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ac00d-149">Select to display the **Send Port Properties** dialog box for the selected send port.</span></span>|  
  
4.  <span data-ttu-id="ac00d-150">在**憑證**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ac00d-150">On the **Certificate** page, do the following:</span></span>  
  
    |<span data-ttu-id="ac00d-151">使用</span><span class="sxs-lookup"><span data-stu-id="ac00d-151">Use this</span></span>|<span data-ttu-id="ac00d-152">動作</span><span class="sxs-lookup"><span data-stu-id="ac00d-152">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="ac00d-153">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="ac00d-153">**Browse**</span></span>|<span data-ttu-id="ac00d-154">選取即可顯示**選取憑證**對話方塊，其中的本機電腦 」 或 「 其他人憑證存放區設定要套用至訊息傳送至合作對象選取簽章憑證。</span><span class="sxs-lookup"><span data-stu-id="ac00d-154">Select to display the **Select Certificate** dialog box, where you select the signature certificate from the Local Machine or Other People certificate store to apply to messages transmitted to the party.</span></span>|  
    |<span data-ttu-id="ac00d-155">**一般名稱**</span><span class="sxs-lookup"><span data-stu-id="ac00d-155">**Common Name**</span></span>|<span data-ttu-id="ac00d-156">顯示選取憑證的描述。</span><span class="sxs-lookup"><span data-stu-id="ac00d-156">Displays a description of the selected certificate.</span></span>|  
    |<span data-ttu-id="ac00d-157">**憑證指紋**</span><span class="sxs-lookup"><span data-stu-id="ac00d-157">**Thumbprint**</span></span>|<span data-ttu-id="ac00d-158">顯示私密金鑰憑證的指紋，此私密金鑰憑證是用於合作對象解析與簽章驗證。</span><span class="sxs-lookup"><span data-stu-id="ac00d-158">Displays the thumbprint of the private key certificate that is used for party resolution and signature verification.</span></span> <span data-ttu-id="ac00d-159">憑證指紋的格式為 HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH，其中 H 是十六進位數字 (0 到 9 的數字或是 A 到 F 的字母)。</span><span class="sxs-lookup"><span data-stu-id="ac00d-159">The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit (a number from 0 through 9 or a letter from A through F).</span></span>|  
    |<span data-ttu-id="ac00d-160">**移除憑證**</span><span class="sxs-lookup"><span data-stu-id="ac00d-160">**Remove certificate**</span></span>|<span data-ttu-id="ac00d-161">選取以移除顯示的憑證。</span><span class="sxs-lookup"><span data-stu-id="ac00d-161">Select to remove the displayed certificate.</span></span>|  
  
5.  <span data-ttu-id="ac00d-162">選取**套用**接受這些屬性，或選取**確定**來完成組態設定。</span><span class="sxs-lookup"><span data-stu-id="ac00d-162">Select **Apply** to accept the properties, or select **OK** to complete the configuration setting.</span></span> <span data-ttu-id="ac00d-163">任何一項動作都會驗證設定。</span><span class="sxs-lookup"><span data-stu-id="ac00d-163">Either action will validate the settings</span></span>  

### <a name="update-an-existing-party"></a><span data-ttu-id="ac00d-164">更新現有的合作對象</span><span class="sxs-lookup"><span data-stu-id="ac00d-164">Update an existing party</span></span>
<span data-ttu-id="ac00d-165">在合作對象登錄至角色且連接埠已繫結之後，您可以：</span><span class="sxs-lookup"><span data-stu-id="ac00d-165">After a party is enlisted to a role and the ports are bound, you can:</span></span>  
  
-   <span data-ttu-id="ac00d-166">編輯合作對象的名稱和描述</span><span class="sxs-lookup"><span data-stu-id="ac00d-166">Edit the party's name and description</span></span>  
-   <span data-ttu-id="ac00d-167">編輯合作對象的憑證</span><span class="sxs-lookup"><span data-stu-id="ac00d-167">Edit the party's certificate</span></span>  
-   <span data-ttu-id="ac00d-168">指定合作對象是否適用於組織裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac00d-168">Specify whether the party is for the organization hosting [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span></span>

1. <span data-ttu-id="ac00d-169">在**BizTalk Server 管理**，然後選取**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="ac00d-169">In **BizTalk Server Administration**, and select **Parties**.</span></span>

2. <span data-ttu-id="ac00d-170">在**合作對象與商務設定檔**窗格中，以滑鼠右鍵按一下您想要檢視或編輯合作對象，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="ac00d-170">In the **Parties and Business Profiles** pane, right-click the party you want to view or edit, and then select **Properties**.</span></span>  

3. <span data-ttu-id="ac00d-171">檢視或編輯的屬性。</span><span class="sxs-lookup"><span data-stu-id="ac00d-171">View or edit the properties.</span></span> 

4. <span data-ttu-id="ac00d-172">選取**套用**接受這些屬性，或選取**確定**來完成組態設定。</span><span class="sxs-lookup"><span data-stu-id="ac00d-172">Select **Apply** to accept the properties, or select **OK** to complete the configuration setting.</span></span> <span data-ttu-id="ac00d-173">下列其中一個動作驗證設定。</span><span class="sxs-lookup"><span data-stu-id="ac00d-173">Either action validate the settings.</span></span>  

## <a name="delete-a-party"></a><span data-ttu-id="ac00d-174">刪除合作對象</span><span class="sxs-lookup"><span data-stu-id="ac00d-174">Delete a party</span></span>
<span data-ttu-id="ac00d-175">刪除合作對象使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="ac00d-175">Delete the party using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ac00d-176">您只能刪除未登錄於角色中的合作對象。</span><span class="sxs-lookup"><span data-stu-id="ac00d-176">You can only delete a party that is not enlisted in a role.</span></span> <span data-ttu-id="ac00d-177">您必須先從登錄合作對象的角色來取消登錄它，才能刪除合作對象。</span><span class="sxs-lookup"><span data-stu-id="ac00d-177">Before you can delete a party, you must first un-enlist it from any of the roles where it is enlisted.</span></span> <span data-ttu-id="ac00d-178">請參閱[如何登錄或取消登錄角色的合作對象](../core/how-to-enlist-or-unenlist-a-party-for-a-role.md)。</span><span class="sxs-lookup"><span data-stu-id="ac00d-178">See [How to Enlist or Unenlist a Party for a Role](../core/how-to-enlist-or-unenlist-a-party-for-a-role.md).</span></span> 

1. <span data-ttu-id="ac00d-179">在**BizTalk Server 管理**，選取**合作對象**，以滑鼠右鍵按一下您想要刪除，然後選取合作對的象**刪除**。</span><span class="sxs-lookup"><span data-stu-id="ac00d-179">In **BizTalk Server Administration**, select **Parties**, right-click the party you want to delete, and then select **Delete**.</span></span>  
  
2.  <span data-ttu-id="ac00d-180">在**確認刪除合作對象**對話方塊中，選取**是**刪除合作對象。</span><span class="sxs-lookup"><span data-stu-id="ac00d-180">In the **Confirm delete party** dialog box, select **Yes** to delete the party.</span></span>  

## <a name="search-for-a-party"></a><span data-ttu-id="ac00d-181">搜尋合作對象</span><span class="sxs-lookup"><span data-stu-id="ac00d-181">Search for a party</span></span>
<span data-ttu-id="ac00d-182">如果您有大量的合作對象建立時，您可以使用**搜尋**選項，以顯示您想要查看的合作對象。</span><span class="sxs-lookup"><span data-stu-id="ac00d-182">If you have a large number of parties created, you can use the **Search** option to  display the parties that you want to see.</span></span>  

1. <span data-ttu-id="ac00d-183">在**BizTalk Server 管理**，選取**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="ac00d-183">In **BizTalk Server Administration**, select **Parties**.</span></span>

3.  <span data-ttu-id="ac00d-184">在**合作對象與商務設定檔**窗格中的，於右上角，輸入搜尋字串中的**搜尋合作對象**文字方塊，然後選取 [搜尋] 圖示。</span><span class="sxs-lookup"><span data-stu-id="ac00d-184">In the **Parties and Business Profiles** pane, towards the top right corner, enter a search string in the **Search Party** text box, and select the search icon.</span></span> <span data-ttu-id="ac00d-185">您也可以按 ENTER 開始搜尋。</span><span class="sxs-lookup"><span data-stu-id="ac00d-185">You can also press ENTER to start the search.</span></span>  
  
     <span data-ttu-id="ac00d-186">當您使用搜尋時，您必須考量以下要點：</span><span class="sxs-lookup"><span data-stu-id="ac00d-186">You must consider the following points while using search:</span></span>  
  
    -   <span data-ttu-id="ac00d-187">搜尋字串不區分大小寫</span><span class="sxs-lookup"><span data-stu-id="ac00d-187">The search string is not case-sensitive</span></span>
  
    -   <span data-ttu-id="ac00d-188">您可以搜尋名稱 （在搜尋子字串） 中的文字。</span><span class="sxs-lookup"><span data-stu-id="ac00d-188">You can search for text within the name (sub-string search).</span></span> <span data-ttu-id="ac00d-189">例如，如果您搜尋 ‘ar’，[[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 會顯示以此搜尋字串開頭的合作對象 (例如 Artist) 或是名稱中包含此搜尋字串的合作對象 (例如 Party1)。</span><span class="sxs-lookup"><span data-stu-id="ac00d-189">For example, if you search for ‘ar’, the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console displays the parties that either start with the search string (e.g. Artist) or the parties that have the search string in their name (e.g. Party1).</span></span>  
  
    -   <span data-ttu-id="ac00d-190">搜尋作業僅限於合作對象名稱。</span><span class="sxs-lookup"><span data-stu-id="ac00d-190">The search operation is limited to party names.</span></span>  
  
4.  <span data-ttu-id="ac00d-191">若要清除搜尋結果，請選取 [搜尋] 方塊旁的紅色 'x'。</span><span class="sxs-lookup"><span data-stu-id="ac00d-191">To clear the search results, select the red 'x' next to the search text box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac00d-192">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac00d-192">See Also</span></span>  
 <span data-ttu-id="ac00d-193">[管理角色連結](../core/managing-role-links.md) </span><span class="sxs-lookup"><span data-stu-id="ac00d-193">[Managing Role Links](../core/managing-role-links.md) </span></span>  
 [<span data-ttu-id="ac00d-194">如何設定合作對象解析管線元件</span><span class="sxs-lookup"><span data-stu-id="ac00d-194">How to Configure the Party Resolution Pipeline Component</span></span>](../core/how-to-configure-the-party-resolution-pipeline-component.md)  
 [<span data-ttu-id="ac00d-195">管理 EDI 和 AS2 解決方案</span><span class="sxs-lookup"><span data-stu-id="ac00d-195">Managing EDI and AS2 Solutions</span></span>](../core/managing-edi-and-as2-solutions.md)