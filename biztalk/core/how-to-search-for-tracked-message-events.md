---
title: "如何搜尋追蹤的訊息事件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18df4cf7-c307-4175-926c-9be9f30b29ed
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6a3597d0d68dbd79de6c23e7b6d4b222b9c8376
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-search-for-tracked-message-events"></a><span data-ttu-id="02c81-102">如何搜尋追蹤的訊息事件</span><span class="sxs-lookup"><span data-stu-id="02c81-102">How to Search for Tracked Message Events</span></span>
<span data-ttu-id="02c81-103">您可以使用**新查詢**索引標籤中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台來搜尋追蹤訊息事件。</span><span class="sxs-lookup"><span data-stu-id="02c81-103">You can use the **New Query** tab in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to search for tracked message events.</span></span>  <span data-ttu-id="02c81-104">從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，您可以啟用訊息內文和追蹤訊息屬性。</span><span class="sxs-lookup"><span data-stu-id="02c81-104">From the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console you can enable message body and message property tracking.</span></span> <span data-ttu-id="02c81-105">在查詢結果 窗格中，您可以檢視訊息的事件，包括結構描述資訊、 事件類型、 服務執行個體識別碼，以及產生之訊息的升級的屬性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="02c81-105">In the Query Results pane you can view information about the message event, including schema information, event type, service instance ID, and all the promoted properties for the generated message.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="02c81-106">若要檢視實際的訊息內文，您可以叫用**訊息詳細資料**操作功能表，然後移至 「 訊息部分 」 索引標籤上，或儲存訊息從結果清單檢視叫用**儲存至檔案**從內容功能表。</span><span class="sxs-lookup"><span data-stu-id="02c81-106">In order to view the actual message body, you can invoke the **Message Details** context menu and go to the “Message Parts” tab, or save the message from the result list view by invoking **Save to File** from the context menu.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="02c81-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="02c81-107">Prerequisites</span></span>  
 <span data-ttu-id="02c81-108">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 操作員」群組成員的身分來登入，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="02c81-108">To perform this procedure, you must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Operators group.</span></span>  
  
### <a name="to-search-for-tracked-message-items"></a><span data-ttu-id="02c81-109">若要搜尋的項目追蹤的訊息</span><span class="sxs-lookup"><span data-stu-id="02c81-109">To search for tracked message items</span></span>  
  
1.  <span data-ttu-id="02c81-110">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="02c81-110">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span>  
  
2.  <span data-ttu-id="02c81-111">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，然後按一下 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="02c81-111">In the console tree, expand **BizTalk Server Administration**, and then click the BizTalk group.</span></span>  
  
3.  <span data-ttu-id="02c81-112">在 詳細資料 窗格中，按一下**新查詢** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="02c81-112">In the details pane, click the **New Query** tab.</span></span>  
  
4.  <span data-ttu-id="02c81-113">在**查詢運算式**群組中**值**欄中，選取**追蹤訊息事件**從下拉式清單方塊。</span><span class="sxs-lookup"><span data-stu-id="02c81-113">In the **Query Expression** group, in the **Value** column, select **Tracked Message Events** from the drop-down list box.</span></span>  
  
5.  <span data-ttu-id="02c81-114">在**欄位名稱**星號旁邊的空白下拉式清單方塊中的資料行 (**\***)，選取一個或多個項目：</span><span class="sxs-lookup"><span data-stu-id="02c81-114">In the **Field Name** column, in the empty drop-down list box next to the asterisk (**\***), select one or more of the following:</span></span>  
  
    |<span data-ttu-id="02c81-115">項目</span><span class="sxs-lookup"><span data-stu-id="02c81-115">Item</span></span>|<span data-ttu-id="02c81-116">Description</span><span class="sxs-lookup"><span data-stu-id="02c81-116">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="02c81-117">**建立時間**</span><span class="sxs-lookup"><span data-stu-id="02c81-117">**Creation Time**</span></span>|<span data-ttu-id="02c81-118">建立訊息的時間。</span><span class="sxs-lookup"><span data-stu-id="02c81-118">The time the message was created.</span></span>|  
    |<span data-ttu-id="02c81-119">**事件類型**</span><span class="sxs-lookup"><span data-stu-id="02c81-119">**Event Type**</span></span>|<span data-ttu-id="02c81-120">正在追蹤的事件類型。</span><span class="sxs-lookup"><span data-stu-id="02c81-120">The type of event being tracked.</span></span>|  
    |<span data-ttu-id="02c81-121">**最大相符項目**</span><span class="sxs-lookup"><span data-stu-id="02c81-121">**Maximum Matches**</span></span>|<span data-ttu-id="02c81-122">要顯示的相符記錄數目。</span><span class="sxs-lookup"><span data-stu-id="02c81-122">The number of matches to display.</span></span>|  
    |<span data-ttu-id="02c81-123">**合作對象**</span><span class="sxs-lookup"><span data-stu-id="02c81-123">**Party**</span></span>|<span data-ttu-id="02c81-124">組織傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="02c81-124">The organization that sent the message.</span></span>|  
    |<span data-ttu-id="02c81-125">**[通訊埠]**</span><span class="sxs-lookup"><span data-stu-id="02c81-125">**Port**</span></span>|<span data-ttu-id="02c81-126">用於處理訊息的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="02c81-126">The port used to process the message.</span></span>|  
    |<span data-ttu-id="02c81-127">**結構描述名稱**</span><span class="sxs-lookup"><span data-stu-id="02c81-127">**Schema Name**</span></span>|<span data-ttu-id="02c81-128">使用訊息的結構描述的名稱。</span><span class="sxs-lookup"><span data-stu-id="02c81-128">Name of the schema used by the message.</span></span>|  
    |<span data-ttu-id="02c81-129">**服務執行個體識別碼**</span><span class="sxs-lookup"><span data-stu-id="02c81-129">**Service Instance ID**</span></span>|<span data-ttu-id="02c81-130">用於訊息的服務執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="02c81-130">The service instance ID used for the message.</span></span>|  
    |<span data-ttu-id="02c81-131">**URI**</span><span class="sxs-lookup"><span data-stu-id="02c81-131">**URI**</span></span>|<span data-ttu-id="02c81-132">用於訊息的 URI。</span><span class="sxs-lookup"><span data-stu-id="02c81-132">The URI used for the message.</span></span>|  
    |<span data-ttu-id="02c81-133">**\<選取追蹤的屬性結構描述名稱\>**</span><span class="sxs-lookup"><span data-stu-id="02c81-133">**\<Select a Schema Name for Tracked Properties\>**</span></span>|<span data-ttu-id="02c81-134">當您選取的結構描述時，該結構描述中任何升級的屬性是適合用來在查詢中。</span><span class="sxs-lookup"><span data-stu-id="02c81-134">When you select a schema, any promoted properties in that schema are eligible to be used in the query.</span></span>|  
  
6.  <span data-ttu-id="02c81-135">完成**值**適用於選取項目所做的資料行**欄位名稱**資料行。</span><span class="sxs-lookup"><span data-stu-id="02c81-135">Complete the **Value** column as appropriate for the selection you made in the **Field Name** column.</span></span>  
  
7.  <span data-ttu-id="02c81-136">繼續新增其他行至適當的查詢中，藉由完成**欄位名稱**，**運算子**，和**值**資料行，然後再按一下**執行查詢**。</span><span class="sxs-lookup"><span data-stu-id="02c81-136">Continue adding additional lines to the query as appropriate by completing the **Field Name**, **Operator**, and **Values** columns, and then click **Run Query**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02c81-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="02c81-137">See Also</span></span>  
 [<span data-ttu-id="02c81-138">使用管理主控台查詢索引標籤</span><span class="sxs-lookup"><span data-stu-id="02c81-138">Using the Administration Console Query Tab</span></span>](../core/using-the-administration-console-query-tab.md)