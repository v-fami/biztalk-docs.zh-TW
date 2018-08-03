---
title: 如何搜尋訂用帳戶 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Query tab [Administration Console], subscriptions
- Query tab [Administration Console], searching
- subscriptions, viewing
- subscriptions, searching
ms.assetid: 95f8fd20-2750-412b-a67b-18976e7706e2
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07230ace1e097d71e728110b8f2280e903ea67b8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023244"
---
# <a name="how-to-search-for-subscriptions"></a><span data-ttu-id="13a44-102">如何搜尋訂閱</span><span class="sxs-lookup"><span data-stu-id="13a44-102">How to Search for Subscriptions</span></span>
<span data-ttu-id="13a44-103">您可以使用**查詢**在 BizTalk Server 管理主控台，來搜尋訂用帳戶 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="13a44-103">You can use the **Query** tab in the BizTalk Server Administration Console to search for subscriptions.</span></span> <span data-ttu-id="13a44-104">當您要檢視系統中所定義的所有訂閱時，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="13a44-104">This is useful when you want to review all of the subscriptions defined in the system.</span></span> <span data-ttu-id="13a44-105">在疑難排解路由失敗時，您可以檢視訂閱以查看是否有任何訂閱設定不當，因此導致路由失敗。</span><span class="sxs-lookup"><span data-stu-id="13a44-105">When troubleshooting routing failures, you can review subscriptions to see if any of them are improperly configured, thereby causing the routing failure.</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="13a44-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="13a44-106">Prerequisites</span></span>  
 <span data-ttu-id="13a44-107">若要執行此程序，您必須以「BizTalk Server 操作員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="13a44-107">To perform this procedure, you must be logged on as a member of the BizTalk Server Operators group.</span></span>  

### <a name="to-search-for-subscriptions"></a><span data-ttu-id="13a44-108">搜尋訂閱</span><span class="sxs-lookup"><span data-stu-id="13a44-108">To search for subscriptions</span></span>  

1. <span data-ttu-id="13a44-109">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="13a44-109">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span>  

2. <span data-ttu-id="13a44-110">在主控台樹狀目錄中展開 [[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]]，然後按一下 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="13a44-110">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then click the BizTalk group.</span></span>  

3. <span data-ttu-id="13a44-111">在 詳細資料 窗格中，按一下**新的查詢** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="13a44-111">In the details pane, click the **New Query** tab.</span></span>  

4. <span data-ttu-id="13a44-112">在 **查詢運算式**群組中**值**欄中，選取**訂用帳戶**從下拉式清單方塊。</span><span class="sxs-lookup"><span data-stu-id="13a44-112">In the **Query Expression** group, in the **Value** column, select **Subscriptions** from the drop-down list box.</span></span>  

5. <span data-ttu-id="13a44-113">在 **欄位名稱**星號旁邊的空白下拉式清單方塊中的資料行 (\* *\\* \* \*)，選取一或多個項目：</span><span class="sxs-lookup"><span data-stu-id="13a44-113">In the **Field Name** column, in the empty drop-down list box next to the asterisk (\*\*\\*\*\*), select one or more of the following:</span></span>  


   |          <span data-ttu-id="13a44-114">項目</span><span class="sxs-lookup"><span data-stu-id="13a44-114">Item</span></span>           |                                    <span data-ttu-id="13a44-115">描述</span><span class="sxs-lookup"><span data-stu-id="13a44-115">Description</span></span>                                    |
   |-------------------------|-----------------------------------------------------------------------------------|
   |   <span data-ttu-id="13a44-116">**最大相符項目**</span><span class="sxs-lookup"><span data-stu-id="13a44-116">**Maximum Matches**</span></span>   |                         <span data-ttu-id="13a44-117">要顯示的相符記錄數目。</span><span class="sxs-lookup"><span data-stu-id="13a44-117">The number of matches to display.</span></span>                         |
   | <span data-ttu-id="13a44-118">**服務執行個體識別碼**</span><span class="sxs-lookup"><span data-stu-id="13a44-118">**Service Instance ID**</span></span> |               <span data-ttu-id="13a44-119">您可以依據服務執行個體識別碼篩選訂閱。</span><span class="sxs-lookup"><span data-stu-id="13a44-119">You can filter subscriptions by service instance ID.</span></span>                |
   |    <span data-ttu-id="13a44-120">**服務名稱**</span><span class="sxs-lookup"><span data-stu-id="13a44-120">**Service Name**</span></span>     |                   <span data-ttu-id="13a44-121">您可以依據服務名稱篩選訂閱。</span><span class="sxs-lookup"><span data-stu-id="13a44-121">You can filter subscriptions by service name.</span></span>                   |
   |  <span data-ttu-id="13a44-122">**訂閱類型**</span><span class="sxs-lookup"><span data-stu-id="13a44-122">**Subscription Type**</span></span>  | <span data-ttu-id="13a44-123">您可以依據「啟動訂閱」或「執行個體訂閱」篩選訂閱。</span><span class="sxs-lookup"><span data-stu-id="13a44-123">You can filter subscriptions by Activation Subscription or Instance Subscription.</span></span> |


6. <span data-ttu-id="13a44-124">完成**值**適當選取您在中所做的資料行**欄位名**資料行。</span><span class="sxs-lookup"><span data-stu-id="13a44-124">Complete the **Value** column as appropriate for the selection you made in the **Field Name** column.</span></span>  

7. <span data-ttu-id="13a44-125">繼續新增其他行至視需要查詢中，藉由完成**欄位名**，**運算子**，和**值**資料行，然後再按一下**執行查詢**。</span><span class="sxs-lookup"><span data-stu-id="13a44-125">Continue adding additional lines to the query as appropriate, by completing the **Field Name**, **Operator**, and **Values** columns, and then click **Run Query**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="13a44-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13a44-126">See Also</span></span>  
 [<span data-ttu-id="13a44-127">使用管理主控台查詢索引標籤</span><span class="sxs-lookup"><span data-stu-id="13a44-127">Using the Administration Console Query Tab</span></span>](../core/using-the-administration-console-query-tab.md)