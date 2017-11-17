---
title: "如何搜尋訂閱 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Query tab [Administration Console], subscriptions
- Query tab [Administration Console], searching
- subscriptions, viewing
- subscriptions, searching
ms.assetid: 95f8fd20-2750-412b-a67b-18976e7706e2
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f1830a4c1dddfa3dcfc2a1177b69410dd8ee0ac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-search-for-subscriptions"></a><span data-ttu-id="ea32e-102">如何搜尋訂閱</span><span class="sxs-lookup"><span data-stu-id="ea32e-102">How to Search for Subscriptions</span></span>
<span data-ttu-id="ea32e-103">您可以使用**查詢** 索引標籤，在 BizTalk Server 管理主控台，來搜尋訂閱。</span><span class="sxs-lookup"><span data-stu-id="ea32e-103">You can use the **Query** tab in the BizTalk Server Administration Console to search for subscriptions.</span></span> <span data-ttu-id="ea32e-104">當您要檢視系統中所定義的所有訂閱時，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="ea32e-104">This is useful when you want to review all of the subscriptions defined in the system.</span></span> <span data-ttu-id="ea32e-105">在疑難排解路由失敗時，您可以檢視訂閱以查看是否有任何訂閱設定不當，因此導致路由失敗。</span><span class="sxs-lookup"><span data-stu-id="ea32e-105">When troubleshooting routing failures, you can review subscriptions to see if any of them are improperly configured, thereby causing the routing failure.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ea32e-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="ea32e-106">Prerequisites</span></span>  
 <span data-ttu-id="ea32e-107">若要執行此程序，您必須以「BizTalk Server 操作員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="ea32e-107">To perform this procedure, you must be logged on as a member of the BizTalk Server Operators group.</span></span>  
  
### <a name="to-search-for-subscriptions"></a><span data-ttu-id="ea32e-108">搜尋訂閱</span><span class="sxs-lookup"><span data-stu-id="ea32e-108">To search for subscriptions</span></span>  
  
1.  <span data-ttu-id="ea32e-109">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ea32e-109">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span>  
  
2.  <span data-ttu-id="ea32e-110">在主控台樹狀目錄中展開 [[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]]，然後按一下 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="ea32e-110">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then click the BizTalk group.</span></span>  
  
3.  <span data-ttu-id="ea32e-111">在 詳細資料 窗格中，按一下**新查詢** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ea32e-111">In the details pane, click the **New Query** tab.</span></span>  
  
4.  <span data-ttu-id="ea32e-112">在**查詢運算式**群組中**值**欄中，選取**訂閱**從下拉式清單方塊。</span><span class="sxs-lookup"><span data-stu-id="ea32e-112">In the **Query Expression** group, in the **Value** column, select **Subscriptions** from the drop-down list box.</span></span>  
  
5.  <span data-ttu-id="ea32e-113">在**欄位名稱**星號旁邊的空白下拉式清單方塊中的資料行 (**\***)，選取一個或多個項目：</span><span class="sxs-lookup"><span data-stu-id="ea32e-113">In the **Field Name** column, in the empty drop-down list box next to the asterisk (**\***), select one or more of the following:</span></span>  
  
    |<span data-ttu-id="ea32e-114">項目</span><span class="sxs-lookup"><span data-stu-id="ea32e-114">Item</span></span>|<span data-ttu-id="ea32e-115">Description</span><span class="sxs-lookup"><span data-stu-id="ea32e-115">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="ea32e-116">**最大相符項目**</span><span class="sxs-lookup"><span data-stu-id="ea32e-116">**Maximum Matches**</span></span>|<span data-ttu-id="ea32e-117">要顯示的相符記錄數目。</span><span class="sxs-lookup"><span data-stu-id="ea32e-117">The number of matches to display.</span></span>|  
    |<span data-ttu-id="ea32e-118">**服務執行個體識別碼**</span><span class="sxs-lookup"><span data-stu-id="ea32e-118">**Service Instance ID**</span></span>|<span data-ttu-id="ea32e-119">您可以依據服務執行個體識別碼篩選訂閱。</span><span class="sxs-lookup"><span data-stu-id="ea32e-119">You can filter subscriptions by service instance ID.</span></span>|  
    |<span data-ttu-id="ea32e-120">**服務名稱**</span><span class="sxs-lookup"><span data-stu-id="ea32e-120">**Service Name**</span></span>|<span data-ttu-id="ea32e-121">您可以依據服務名稱篩選訂閱。</span><span class="sxs-lookup"><span data-stu-id="ea32e-121">You can filter subscriptions by service name.</span></span>|  
    |<span data-ttu-id="ea32e-122">**訂閱類型**</span><span class="sxs-lookup"><span data-stu-id="ea32e-122">**Subscription Type**</span></span>|<span data-ttu-id="ea32e-123">您可以依據「啟動訂閱」或「執行個體訂閱」篩選訂閱。</span><span class="sxs-lookup"><span data-stu-id="ea32e-123">You can filter subscriptions by Activation Subscription or Instance Subscription.</span></span>|  
  
6.  <span data-ttu-id="ea32e-124">完成**值**適用於選取項目所做的資料行**欄位名稱**資料行。</span><span class="sxs-lookup"><span data-stu-id="ea32e-124">Complete the **Value** column as appropriate for the selection you made in the **Field Name** column.</span></span>  
  
7.  <span data-ttu-id="ea32e-125">繼續新增其他行至視需要查詢，藉由完成**欄位名稱**，**運算子**，和**值**資料行，然後再按一下**執行查詢**。</span><span class="sxs-lookup"><span data-stu-id="ea32e-125">Continue adding additional lines to the query as appropriate, by completing the **Field Name**, **Operator**, and **Values** columns, and then click **Run Query**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea32e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea32e-126">See Also</span></span>  
 [<span data-ttu-id="ea32e-127">使用管理主控台查詢索引標籤</span><span class="sxs-lookup"><span data-stu-id="ea32e-127">Using the Administration Console Query Tab</span></span>](../core/using-the-administration-console-query-tab.md)