---
title: 如何關閉全域追蹤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae3059a-cbdd-47c4-84cd-edfb5480b9fa
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c143d19e6071ca4f9ce488ae936082db86dc84dc
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26007095"
---
# <a name="how-to-turn-off-global-tracking"></a><span data-ttu-id="46879-102">如何關閉全域追蹤</span><span class="sxs-lookup"><span data-stu-id="46879-102">How to Turn Off Global Tracking</span></span>
<span data-ttu-id="46879-103">根據預設，當您安裝 BizTalk Server 時，會啟用全域追蹤。</span><span class="sxs-lookup"><span data-stu-id="46879-103">By default, global tracking is enabled when you install BizTalk Server.</span></span> <span data-ttu-id="46879-104">BizTalk 追蹤 (BizTalkDTADb) 資料庫成長的大小為[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]處理您的系統上的資料。</span><span class="sxs-lookup"><span data-stu-id="46879-104">The BizTalk Tracking (BizTalkDTADb) database grows in size as [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes data on your system.</span></span> <span data-ttu-id="46879-105">如果 BizTalk 追蹤資料庫導致磁碟效能低落，您可以從追蹤資料庫清除資料。</span><span class="sxs-lookup"><span data-stu-id="46879-105">If the size of the BizTalk Tracking database causes poor disk performance, you can purge the data from the Tracking database.</span></span> <span data-ttu-id="46879-106">如果效能問題是藉由清除 BizTalk 追蹤資料庫而暫時解決，而您想要將 BizTalk 設定為不再收集追蹤資訊，則您可以考慮關閉全域追蹤。</span><span class="sxs-lookup"><span data-stu-id="46879-106">If you are having performance issues that are momentarily addressed by purging the BizTalk tracking database, and you want to configure BizTalk to no longer collect tracking information, you may want to consider turning off global tracking.</span></span>  
  
 <span data-ttu-id="46879-107">請務必了解，關閉全域追蹤會停用整個的追蹤攔截器[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。</span><span class="sxs-lookup"><span data-stu-id="46879-107">It is important to understand that turning off global tracking disables the tracking interceptors for the entire [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group.</span></span> <span data-ttu-id="46879-108">這代表 BizTalk 無法在其追蹤表格中追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="46879-108">This means that BizTalk will not track events in its tracking tables.</span></span> <span data-ttu-id="46879-109">或者，您可以關閉個別事件的追蹤。</span><span class="sxs-lookup"><span data-stu-id="46879-109">Alternatively, you can turn off tracking for individual events.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46879-110">如果要使用「商務活動監控」(BAM)，則應該維護專用的追蹤主控件，即使已停用全域追蹤。</span><span class="sxs-lookup"><span data-stu-id="46879-110">If you are using Business Activity Monitoring (BAM), you should maintain a dedicated tracking host, even if you disable global tracking.</span></span> <span data-ttu-id="46879-111">這是因為 BAM 事件會使用「追蹤資料解碼服務」(TDDS)。</span><span class="sxs-lookup"><span data-stu-id="46879-111">This is because BAM events use the Tracking Data Decode Service (TDDS).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="46879-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="46879-112">Prerequisites</span></span>  
 <span data-ttu-id="46879-113">您必須以 SQL Server 系統管理員 (sysadmin) 固定伺服器角色成員的帳戶登入來執行這個程序。</span><span class="sxs-lookup"><span data-stu-id="46879-113">You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.</span></span>  
  
### <a name="to-turn-off-global-tracking-sql-server-2008"></a><span data-ttu-id="46879-114">若要關閉全域追蹤 (SQL Server 2008)</span><span class="sxs-lookup"><span data-stu-id="46879-114">To turn off global tracking (SQL Server 2008)</span></span>  
  
1.  <span data-ttu-id="46879-115">在裝載 「 BizTalk 追蹤 (BizTalkDTADb) 資料庫的 SQL server 中，按一下 **啟動**，按一下 **程式**，按一下  **Microsoft SQL Server 2008 R2**，然後按一下  **SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="46879-115">On the SQL server that hosts the BizTalk Tracking (BizTalkDTADb) database, click **Start**, click **Programs**, click **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="46879-116">在**連接到伺服器**對話方塊中，確認伺服器名稱和驗證，然後按一下**連接**。</span><span class="sxs-lookup"><span data-stu-id="46879-116">In the **Connect to Server** dialog box, verify the server name and authentication, and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="46879-117">在 Microsoft SQL Server Management Studio 中**物件總管] 中**，依序展開\<*電腦名稱*\>，依序展開**資料庫**，展開**BizTalkMgmtDb**，依序展開**資料表**，以滑鼠右鍵按一下 **[adm_group]**，然後按一下 [**開啟資料表**。</span><span class="sxs-lookup"><span data-stu-id="46879-117">In Microsoft SQL Server Management Studio, in **Object Explorer**, expand \<*computer name*\>, expand **Databases**, expand **BizTalkMgmtDb**, expand **Tables**, right-click **adm_Group**, and then click **Open Table**.</span></span>  
  
4.  <span data-ttu-id="46879-118">在資料表檢視器中水平捲動，直到您找到 **[globaltrackingoption]**。</span><span class="sxs-lookup"><span data-stu-id="46879-118">In the table viewer, scroll horizontally until you find **GlobalTrackingOption**.</span></span>  
  
5.  <span data-ttu-id="46879-119">在 **[globaltrackingoption]** 資料行，將值從 1 變更為 0 時，若要關閉此功能，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="46879-119">In the **GlobalTrackingOption** column, change the value from 1 to 0, to turn off this feature, and then press ENTER.</span></span>  
  
6.  <span data-ttu-id="46879-120">關閉 Microsoft SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="46879-120">Close Microsoft SQL Server Management Studio.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="46879-121">您必須重新啟動 BizTalk 主控件以使變更生效。</span><span class="sxs-lookup"><span data-stu-id="46879-121">You must restart your BizTalk hosts for the change to take effect.</span></span>  
  
7.  <span data-ttu-id="46879-122">按一下**啟動**，按一下 **程式**，指向  **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="46879-122">Click **Start**, click **Programs**, point to **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
8.  <span data-ttu-id="46879-123">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後按一下  **主控件執行個體**。</span><span class="sxs-lookup"><span data-stu-id="46879-123">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then click **Host Instances**.</span></span>  
  
9. <span data-ttu-id="46879-124">在詳細資料窗格中，以滑鼠右鍵按一下每個主機，然後**重新啟動**。</span><span class="sxs-lookup"><span data-stu-id="46879-124">In the details pane, right-click each host, and then click **Restart**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46879-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="46879-125">See Also</span></span>  
 <span data-ttu-id="46879-126">[封存和清除 BizTalk 追蹤資料庫](../core/archiving-and-purging-the-biztalk-tracking-database.md) </span><span class="sxs-lookup"><span data-stu-id="46879-126">[Archiving and Purging the BizTalk Tracking Database](../core/archiving-and-purging-the-biztalk-tracking-database.md) </span></span>  
 <span data-ttu-id="46879-127">[如何從 BizTalk 追蹤資料庫清除資料](../core/how-to-purge-data-from-the-biztalk-tracking-database.md) </span><span class="sxs-lookup"><span data-stu-id="46879-127">[How to Purge Data from the BizTalk Tracking Database](../core/how-to-purge-data-from-the-biztalk-tracking-database.md) </span></span>  
 [<span data-ttu-id="46879-128">如何從 BizTalk 追蹤資料庫手動清除資料</span><span class="sxs-lookup"><span data-stu-id="46879-128">How to Manually Purge Data from the BizTalk Tracking Database</span></span>](../core/how-to-manually-purge-data-from-the-biztalk-tracking-database.md)