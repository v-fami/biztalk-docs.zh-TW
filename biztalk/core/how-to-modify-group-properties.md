---
title: 如何修改群組屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- modifying, groups
- configuring, groups
- groups, configuring
- managing [groups], properties
- groups, modifying
- managing [groups], modifying
- groups, properties
ms.assetid: 59e0853d-81b0-43f9-85bf-099868e25fad
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a191011b6824086e26c72ce5e5a182a167ca0e37
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254862"
---
# <a name="how-to-modify-group-properties"></a><span data-ttu-id="fd035-102">如何修改群組屬性</span><span class="sxs-lookup"><span data-stu-id="fd035-102">How to Modify Group Properties</span></span>
<span data-ttu-id="fd035-103">您可以使用這個程序來設定 BizTalk Server 群組的全域屬性，以便選取簽章憑證、修改快取重新整理間隔，並决定 BizTalk Server 將如何處理大型訊息。</span><span class="sxs-lookup"><span data-stu-id="fd035-103">You can use this procedure to configure global properties for your BizTalk Server group so that you can select a signing certificate, modify the cache refresh interval, and determine how BizTalk Server will handle large messages.</span></span> <span data-ttu-id="fd035-104">如需 BizTalk Server 群組屬性的詳細資訊，請參閱[BizTalk 群組](../core/biztalk-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="fd035-104">For more information about BizTalk Server group properties, see [BizTalk Groups](../core/biztalk-groups.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fd035-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="fd035-105">Prerequisites</span></span>  
 <span data-ttu-id="fd035-106">若要執行此程序，您必須以「BizTalk Server 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="fd035-106">To perform this procedure, you must be logged on as a member of the BizTalk Server Administrators group.</span></span>  
  
### <a name="to-configure-biztalk-group-properties"></a><span data-ttu-id="fd035-107">設定 BizTalk 群組屬性</span><span class="sxs-lookup"><span data-stu-id="fd035-107">To configure BizTalk group properties</span></span>  
  
1.  <span data-ttu-id="fd035-108">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="fd035-108">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="fd035-109">在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、 依序展開 BizTalk 群組、 以滑鼠右鍵按一下**BizTalk 群組**，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="fd035-109">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, right-click **BizTalk Group**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="fd035-110">在**群組內容**對話方塊**一般**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="fd035-110">In the **Group Properties** dialog box, on the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="fd035-111">使用</span><span class="sxs-lookup"><span data-stu-id="fd035-111">Use this</span></span>|<span data-ttu-id="fd035-112">動作</span><span class="sxs-lookup"><span data-stu-id="fd035-112">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="fd035-113">**名稱**</span><span class="sxs-lookup"><span data-stu-id="fd035-113">**Name**</span></span>|<span data-ttu-id="fd035-114">輸入群組名稱。</span><span class="sxs-lookup"><span data-stu-id="fd035-114">Type the group name.</span></span> <span data-ttu-id="fd035-115">群組名稱的長度不能超過 128 個字元。</span><span class="sxs-lookup"><span data-stu-id="fd035-115">The group name cannot exceed 128 characters in length.</span></span> <span data-ttu-id="fd035-116">此方塊中的名稱旁會顯示**群組**在主控台樹狀目錄中，以及伺服器名稱和 BizTalk 管理資料庫名稱的節點。</span><span class="sxs-lookup"><span data-stu-id="fd035-116">The name in this box appears next to the **Group** node in the console tree, along with the server name and the BizTalk Management database name.</span></span>|  
    |<span data-ttu-id="fd035-117">**Server**</span><span class="sxs-lookup"><span data-stu-id="fd035-117">**Server**</span></span>|<span data-ttu-id="fd035-118">顯示實際儲存「BizTalk 管理」資料庫的伺服器。</span><span class="sxs-lookup"><span data-stu-id="fd035-118">Displays the server on which the BizTalk Management database is physically stored.</span></span>|  
    |<span data-ttu-id="fd035-119">**資料庫**</span><span class="sxs-lookup"><span data-stu-id="fd035-119">**Database**</span></span>|<span data-ttu-id="fd035-120">顯示儲存此群組之所有組態設定的「BizTalk 管理」資料庫。</span><span class="sxs-lookup"><span data-stu-id="fd035-120">Displays the BizTalk Management database on which all configuration settings for this group are stored.</span></span>|  
    |<span data-ttu-id="fd035-121">**SSO 伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="fd035-121">**SSO Server name**</span></span>|<span data-ttu-id="fd035-122">輸入這部電腦將用來儲存和存取配接器特定資訊的企業單一登入 (SSO) 伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="fd035-122">Type the name of the Enterprise Single Sign-On (SSO) server that this computer will use to store and access adapter-specific information.</span></span> <span data-ttu-id="fd035-123">這是用來連接到 SSO 資料庫之 SSO 伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="fd035-123">This is the name of the SSO server used to connect to the SSO database.</span></span>|  
    |<span data-ttu-id="fd035-124">**BizTalk 系統管理員群組**</span><span class="sxs-lookup"><span data-stu-id="fd035-124">**BizTalk Administrator Group**</span></span>|<span data-ttu-id="fd035-125">顯示系統管理員群組名稱，此群組在安裝完成後擁有管理 BizTalk Server 環境的權限。</span><span class="sxs-lookup"><span data-stu-id="fd035-125">Displays the name of the administrators group that has rights to manage the BizTalk Server environment after installation.</span></span>|  
    |<span data-ttu-id="fd035-126">**BizTalk 操作員群組**</span><span class="sxs-lookup"><span data-stu-id="fd035-126">**BizTalk Operators Group**</span></span>|<span data-ttu-id="fd035-127">顯示擁有檢視組態、執行查詢及執行電腦維護與基本應用程式監控之權限的操作員群組名稱。</span><span class="sxs-lookup"><span data-stu-id="fd035-127">Displays the name of the operators group that has rights to view configuration, run queries, and perform computer maintenance and basic application monitoring.</span></span>|  
    |<span data-ttu-id="fd035-128">**BizTalk Server B2B 操作員**</span><span class="sxs-lookup"><span data-stu-id="fd035-128">**BizTalk Server B2B Operators**</span></span>|<span data-ttu-id="fd035-129">顯示 B2B 操作員群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="fd035-129">Displays the name of the B2B operators group.</span></span>|  
  
4.  <span data-ttu-id="fd035-130">在**資料庫**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="fd035-130">On the **Databases** tab, do the following:</span></span>  
  
    |<span data-ttu-id="fd035-131">使用</span><span class="sxs-lookup"><span data-stu-id="fd035-131">Use this</span></span>|<span data-ttu-id="fd035-132">動作</span><span class="sxs-lookup"><span data-stu-id="fd035-132">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="fd035-133">**資料庫**</span><span class="sxs-lookup"><span data-stu-id="fd035-133">**Databases**</span></span>|<span data-ttu-id="fd035-134">顯示在設定期間所指定之應用程式中的所有資料庫名稱，以及資料庫所在的伺服器。</span><span class="sxs-lookup"><span data-stu-id="fd035-134">Displays the names of all databases in the application and the servers on which they reside, as specified during configuration.</span></span>|  
  
5.  <span data-ttu-id="fd035-135">在**憑證**索引標籤上，執行下列工作，，然後按一下**確定**:</span><span class="sxs-lookup"><span data-stu-id="fd035-135">On the **Certificate** tab, do the following, and then click **OK**:</span></span>  
  
    |<span data-ttu-id="fd035-136">使用</span><span class="sxs-lookup"><span data-stu-id="fd035-136">Use this</span></span>|<span data-ttu-id="fd035-137">動作</span><span class="sxs-lookup"><span data-stu-id="fd035-137">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="fd035-138">**一般名稱**</span><span class="sxs-lookup"><span data-stu-id="fd035-138">**Common Name**</span></span>|<span data-ttu-id="fd035-139">顯示選取憑證的描述。</span><span class="sxs-lookup"><span data-stu-id="fd035-139">Displays a description of the selected certificate.</span></span>|  
    |<span data-ttu-id="fd035-140">**憑證指紋**</span><span class="sxs-lookup"><span data-stu-id="fd035-140">**Thumbprint**</span></span>|<span data-ttu-id="fd035-141">顯示私密金鑰憑證的指紋，此私密金鑰憑證是用以數位簽章來自此群組的輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="fd035-141">Displays the thumbprint of the private key certificate that is used to digitally sign outbound messages from this group.</span></span> <span data-ttu-id="fd035-142">憑證指紋的格式為 HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH，其中 H 是十六進位數字 (0 到 9 的數字或是 A 到 F 的字母)。</span><span class="sxs-lookup"><span data-stu-id="fd035-142">The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit (a number from 0 through 9 or a letter from A through F).</span></span>|  
    |<span data-ttu-id="fd035-143">**移除憑證**</span><span class="sxs-lookup"><span data-stu-id="fd035-143">**Remove certificate**</span></span>|<span data-ttu-id="fd035-144">按一下以移除顯示的憑證。</span><span class="sxs-lookup"><span data-stu-id="fd035-144">Click to remove the displayed certificate.</span></span>|  
    |<span data-ttu-id="fd035-145">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="fd035-145">**Browse**</span></span>|<span data-ttu-id="fd035-146">按一下即可顯示**選取憑證**對話方塊中，選取您想要使用與群組目前的使用者或個人存放區簽章憑證的位置。</span><span class="sxs-lookup"><span data-stu-id="fd035-146">Click to display the **Select Certificate** dialog box, where you select the signature certificate for the current user or personal store you want to use with the group.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fd035-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd035-147">See Also</span></span>  
 <span data-ttu-id="fd035-148">[管理群組](../core/managing-groups.md) </span><span class="sxs-lookup"><span data-stu-id="fd035-148">[Managing Groups](../core/managing-groups.md) </span></span>  
 <span data-ttu-id="fd035-149">[BizTalk 群組](../core/biztalk-groups.md) </span><span class="sxs-lookup"><span data-stu-id="fd035-149">[BizTalk Groups](../core/biztalk-groups.md) </span></span>  
 <span data-ttu-id="fd035-150">[如何將伺服器新增至群組](../core/how-to-add-a-server-to-a-group.md) </span><span class="sxs-lookup"><span data-stu-id="fd035-150">[How to Add a Server to a Group](../core/how-to-add-a-server-to-a-group.md) </span></span>  
 <span data-ttu-id="fd035-151">[如何將伺服器從一個群組移至另一個](../core/how-to-move-a-server-from-one-group-to-another.md) </span><span class="sxs-lookup"><span data-stu-id="fd035-151">[How to Move a Server from One Group to Another](../core/how-to-move-a-server-from-one-group-to-another.md) </span></span>  
 [<span data-ttu-id="fd035-152">如何從群組移除伺服器</span><span class="sxs-lookup"><span data-stu-id="fd035-152">How to Remove a Server from a Group</span></span>](../core/how-to-remove-a-server-from-a-group.md)