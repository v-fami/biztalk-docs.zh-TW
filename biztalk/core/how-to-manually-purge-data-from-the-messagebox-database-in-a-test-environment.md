---
title: 如何手動從測試環境中的 MessageBox 資料庫清除資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 398991a9-344a-487a-a817-dfc97d48ebe6
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5282ad864e5c2d4f47b541b59d608087f090f935
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979731"
---
# <a name="how-to-manually-purge-data-from-the-messagebox-database-in-a-test-environment"></a><span data-ttu-id="1435e-102">如何手動從測試環境中的 MessageBox 資料庫清除資料</span><span class="sxs-lookup"><span data-stu-id="1435e-102">How to Manually Purge Data from the MessageBox Database in a Test Environment</span></span>
<span data-ttu-id="1435e-103">在開發或測試環境中執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時，儲存在 MessageBox 資料庫中的資料通常不是重要的即時商務資料，因此可被刪除。</span><span class="sxs-lookup"><span data-stu-id="1435e-103">When running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a development or test environment, data that is stored in the MessageBox database is not usually business critical "live" data and therefore may be deleted.</span></span> <span data-ttu-id="1435e-104">在這些實例中，您可能需要應急的方法來清除 MessageBox 資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="1435e-104">In these scenarios, you may need a "quick and dirty" method for purging data from the MessageBox database.</span></span> <span data-ttu-id="1435e-105">請依照本主題中的程序，使用 bts_CleanupMsgbox 預存程序手動清除 MessageBox 資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="1435e-105">Follow the procedures in this topic to manually purge data from the MessageBox database using the bts_CleanupMsgbox stored procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1435e-106">您應該只在測試環境中執行這些步驟。</span><span class="sxs-lookup"><span data-stu-id="1435e-106">You should only perform these steps in a test environment.</span></span> <span data-ttu-id="1435e-107">不支援在實際執行環境中手動清除 BizTalk MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="1435e-107">Manually purging the BizTalk MessageBox database in a production environment is not supported.</span></span>  
  
### <a name="to-stop-biztalk-services"></a><span data-ttu-id="1435e-108">停止 BizTalk 服務</span><span class="sxs-lookup"><span data-stu-id="1435e-108">To stop BizTalk services</span></span>  
  
1.  <span data-ttu-id="1435e-109">從 [服務] 主控台停止 BizTalk 服務的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="1435e-109">Stop any instances of the BizTalk service from the Services console.</span></span>  
  
2.  <span data-ttu-id="1435e-110">如果外掛式主控件有任何執行中的配接器 (例如 HTTP、SOAP 或 WCF)，請從命令提示字元執行 IISRESET 以重新啟動 IIS。</span><span class="sxs-lookup"><span data-stu-id="1435e-110">If you are running any adapters in isolated hosts (for example HTTP, SOAP, or WCF), restart IIS by running the IISRESET from a command prompt.</span></span>  
  
3.  <span data-ttu-id="1435e-111">關閉所有正在執行的自訂外掛式配接器。</span><span class="sxs-lookup"><span data-stu-id="1435e-111">Shut down any custom Isolated Adapters that are running.</span></span>  
  
### <a name="to-create-and-execute-the-btscleanupmsgbox-stored-procedure-using-sql-server-2008"></a><span data-ttu-id="1435e-112">使用 SQL Server 2008 建立並執行 bts_CleanupMsgbox 預存程序</span><span class="sxs-lookup"><span data-stu-id="1435e-112">To create and execute the bts_CleanupMsgbox stored procedure using SQL Server 2008</span></span>  
  
1. <span data-ttu-id="1435e-113">按一下 **開始**，按一下**所有程式**，按一下  **Microsoft SQL Server 2008 R2**，然後按一下**SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="1435e-113">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
2. <span data-ttu-id="1435e-114">在 **連接到 SQL Server**  對話方塊中，選取 SQL server 和適當的驗證方法，然後按一下**Connect**。</span><span class="sxs-lookup"><span data-stu-id="1435e-114">In the **Connect to SQL Server** dialog box, select the SQL server and the appropriate authentication method, and then click **Connect**.</span></span>  
  
3. <span data-ttu-id="1435e-115">在 **可用的資料庫**下拉式清單中，選取 BizTalk Messagebox 資料庫 (**BizTalkMsgBoxDB**預設情況下)。</span><span class="sxs-lookup"><span data-stu-id="1435e-115">In the **Available databases** drop-down list, select the BizTalk Messagebox database (**BizTalkMsgBoxDB** by default).</span></span>  
  
4. <span data-ttu-id="1435e-116">按一下 **新的查詢**工具列上的圖示。</span><span class="sxs-lookup"><span data-stu-id="1435e-116">Click the **New Query** icon on the toolbar.</span></span>  
  
5. <span data-ttu-id="1435e-117">開啟**msgbox_cleanup_logic.sql**檔案從 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="1435e-117">Open the **msgbox_cleanup_logic.sql** file from SQL Server Management Studio.</span></span> <span data-ttu-id="1435e-118">msgbox_cleanup_logic.sql 檔案位於 BizTalk Server 電腦的 [[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Schema\] 目錄中。</span><span class="sxs-lookup"><span data-stu-id="1435e-118">The msgbox_cleanup_logic.sql file is located in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Schema\ directory of the BizTalk Server computer.</span></span>  
  
6. <span data-ttu-id="1435e-119">按一下 **執行查詢**圖示以執行指令碼，以建立 bts_CleanupMsgbox 預存程序。</span><span class="sxs-lookup"><span data-stu-id="1435e-119">Click the **Execute Query** icon on the toolbar to run the script to create the bts_CleanupMsgbox stored procedure.</span></span> <span data-ttu-id="1435e-120">就可以在預存程序清單中看到代表 bts_CleanupMsgbox 預存程序的 dbo.bts_CleanupMsgbox。</span><span class="sxs-lookup"><span data-stu-id="1435e-120">The bts_CleanupMsgbox stored procedure can then be viewed in the list of stored procedures as dbo.bts_CleanupMsgbox.</span></span>  
  
7. <span data-ttu-id="1435e-121">按一下 **新的查詢**工具列上的圖示。</span><span class="sxs-lookup"><span data-stu-id="1435e-121">Click the **New Query** icon on the toolbar.</span></span>  
  
8. <span data-ttu-id="1435e-122">將下列命令貼到新的查詢視窗：</span><span class="sxs-lookup"><span data-stu-id="1435e-122">Paste the following command into the new query window:</span></span>  
  
   ```  
   exec bts_CleanupMsgbox  
   ```  
  
9. <span data-ttu-id="1435e-123">按一下 **執行查詢**圖示以執行 bts_CleanupMsgbox 預存程序。</span><span class="sxs-lookup"><span data-stu-id="1435e-123">Click the **Execute Query** icon on the toolbar to run the bts_CleanupMsgbox stored procedure.</span></span>  
  
   > [!IMPORTANT]
   >  <span data-ttu-id="1435e-124">請勿在執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的實際執行伺服器上執行 bts_CleanupMsgbox 預存程序。</span><span class="sxs-lookup"><span data-stu-id="1435e-124">Do not run the bts_CleanupMsgbox stored procedure on a production server that is running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="1435e-125">您應該只在測試環境中執行 bts_CleanupMsgbox 預存程序。</span><span class="sxs-lookup"><span data-stu-id="1435e-125">You should only run the bts_CleanupMsgbox stored procedure in a test environment.</span></span> <span data-ttu-id="1435e-126">不支援在實際執行環境中執行 bts_CleanupMsgbox 預存程序。</span><span class="sxs-lookup"><span data-stu-id="1435e-126">Running the bts_CleanupMsgbox stored procedure in a production environment is not supported.</span></span>  
  
10. <span data-ttu-id="1435e-127">視需要重新啟動 BizTalk 服務。</span><span class="sxs-lookup"><span data-stu-id="1435e-127">Restart BizTalk services as needed.</span></span>  
  
## <a name="considerations-when-running-the-btscleanupmsgbox-stored-procedure"></a><span data-ttu-id="1435e-128">執行 bts_CleanupMsgbox 預存程序時的考量</span><span class="sxs-lookup"><span data-stu-id="1435e-128">Considerations when running the bts_CleanupMsgbox stored procedure</span></span>  
 <span data-ttu-id="1435e-129">執行 bts_CleanupMsgbox 預存程序時有下列考量：</span><span class="sxs-lookup"><span data-stu-id="1435e-129">The following considerations apply when running the bts_CleanupMsgbox stored procedure:</span></span>  
  
1.  <span data-ttu-id="1435e-130">如果您在測試系統上安裝更新 BizTalk 資料庫結構描述的 Hotfix，該 Hotfix 可能會將 bts_CleanupMsgbox 預存程序覆寫成空的版本。</span><span class="sxs-lookup"><span data-stu-id="1435e-130">If you install a hot fix onto your test system that updates the BizTalk database schemas, the hot fix may overwrite the bts_CleanupMsgbox stored procedure with an empty version of this stored procedure.</span></span> <span data-ttu-id="1435e-131">在此情況下，您必須依照本主題中的程序來重新建立 bts_CleanupMsgbox 預存程序。</span><span class="sxs-lookup"><span data-stu-id="1435e-131">In this case, you will need to follow the procedures outlined in this topic to recreate the bts_CleanupMsgbox stored procedure.</span></span>  
  
2.  <span data-ttu-id="1435e-132">如果您建立新的 MessageBox 資料庫，bts_CleanupMsgbox 預存程序將是空白的，您必須依照本主題中的程序重新建立 bts_CleanupMsgbox 預存程序。</span><span class="sxs-lookup"><span data-stu-id="1435e-132">If you create a new MessageBox database, the bts_CleanupMsgbox stored procedure will be empty and you will need to follow the procedures outlined in this topic to recreate the bts_CleanupMsgbox stored procedure.</span></span>  
  
3.  <span data-ttu-id="1435e-133">使用 bts_CleanupMsgbox 預存程序會**不支援**生產系統上。</span><span class="sxs-lookup"><span data-stu-id="1435e-133">Use of the bts_CleanupMsgbox stored procedure is **not supported** on a production system.</span></span> <span data-ttu-id="1435e-134">此預存程序將會刪除 MessageBox 資料庫中的所有資料。</span><span class="sxs-lookup"><span data-stu-id="1435e-134">This stored procedure will delete all of the data in your MessageBox database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1435e-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1435e-135">See Also</span></span>  
 [<span data-ttu-id="1435e-136">如何從 BizTalk 追蹤資料庫清除資料</span><span class="sxs-lookup"><span data-stu-id="1435e-136">How to Purge Data from the BizTalk Tracking Database</span></span>](../core/how-to-purge-data-from-the-biztalk-tracking-database.md)