---
title: 如何搜尋追蹤的訊息事件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18df4cf7-c307-4175-926c-9be9f30b29ed
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a49ae9793c38746d965c75dc9da902cfe6b6da3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989287"
---
# <a name="how-to-search-for-tracked-message-events"></a><span data-ttu-id="e0c2e-102">如何搜尋追蹤的訊息事件</span><span class="sxs-lookup"><span data-stu-id="e0c2e-102">How to Search for Tracked Message Events</span></span>
<span data-ttu-id="e0c2e-103">您可以使用**新的查詢**索引標籤中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]来搜尋的管理主控台追蹤訊息事件。</span><span class="sxs-lookup"><span data-stu-id="e0c2e-103">You can use the **New Query** tab in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to search for tracked message events.</span></span>  <span data-ttu-id="e0c2e-104">從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，您可以啟用訊息內文和訊息屬性追蹤。</span><span class="sxs-lookup"><span data-stu-id="e0c2e-104">From the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console you can enable message body and message property tracking.</span></span> <span data-ttu-id="e0c2e-105">在查詢結果 窗格中，您可以檢視訊息事件，包括結構描述資訊、 事件類型、 服務執行個體識別碼和所有產生之訊息的升級的屬性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e0c2e-105">In the Query Results pane you can view information about the message event, including schema information, event type, service instance ID, and all the promoted properties for the generated message.</span></span>  

> [!NOTE]
>  <span data-ttu-id="e0c2e-106">若要檢視實際的訊息本文，您可以叫用**訊息的詳細資料**操作功能表，然後移至 「 訊息組件 」 索引標籤上，或將訊息儲存從結果清單檢視叫用**儲存至檔案**從操作功能表。</span><span class="sxs-lookup"><span data-stu-id="e0c2e-106">In order to view the actual message body, you can invoke the **Message Details** context menu and go to the “Message Parts” tab, or save the message from the result list view by invoking **Save to File** from the context menu.</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="e0c2e-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="e0c2e-107">Prerequisites</span></span>  
 <span data-ttu-id="e0c2e-108">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 操作員」群組成員的身分來登入，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="e0c2e-108">To perform this procedure, you must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Operators group.</span></span>  

### <a name="to-search-for-tracked-message-items"></a><span data-ttu-id="e0c2e-109">搜尋追蹤的訊息項目</span><span class="sxs-lookup"><span data-stu-id="e0c2e-109">To search for tracked message items</span></span>  

1. <span data-ttu-id="e0c2e-110">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e0c2e-110">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span>  

2. <span data-ttu-id="e0c2e-111">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，然後按一下 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="e0c2e-111">In the console tree, expand **BizTalk Server Administration**, and then click the BizTalk group.</span></span>  

3. <span data-ttu-id="e0c2e-112">在 詳細資料 窗格中，按一下**新的查詢** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e0c2e-112">In the details pane, click the **New Query** tab.</span></span>  

4. <span data-ttu-id="e0c2e-113">在 **查詢運算式**群組中**值**欄中，選取**追蹤的訊息事件**從下拉式清單方塊。</span><span class="sxs-lookup"><span data-stu-id="e0c2e-113">In the **Query Expression** group, in the **Value** column, select **Tracked Message Events** from the drop-down list box.</span></span>  

5. <span data-ttu-id="e0c2e-114">在 **欄位名稱**星號旁邊的空白下拉式清單方塊中的資料行 (\* *\\* \* \*)，選取一或多個項目：</span><span class="sxs-lookup"><span data-stu-id="e0c2e-114">In the **Field Name** column, in the empty drop-down list box next to the asterisk (\*\*\\*\*\*), select one or more of the following:</span></span>  


   |                        <span data-ttu-id="e0c2e-115">項目</span><span class="sxs-lookup"><span data-stu-id="e0c2e-115">Item</span></span>                         |                                              <span data-ttu-id="e0c2e-116">描述</span><span class="sxs-lookup"><span data-stu-id="e0c2e-116">Description</span></span>                                               |
   |-----------------------------------------------------|--------------------------------------------------------------------------------------------------------|
   |                  <span data-ttu-id="e0c2e-117">**建立時間**</span><span class="sxs-lookup"><span data-stu-id="e0c2e-117">**Creation Time**</span></span>                  |                                   <span data-ttu-id="e0c2e-118">建立訊息的時間。</span><span class="sxs-lookup"><span data-stu-id="e0c2e-118">The time the message was created.</span></span>                                    |
   |                   <span data-ttu-id="e0c2e-119">**事件類型**</span><span class="sxs-lookup"><span data-stu-id="e0c2e-119">**Event Type**</span></span>                    |                                    <span data-ttu-id="e0c2e-120">正在追蹤的事件類型。</span><span class="sxs-lookup"><span data-stu-id="e0c2e-120">The type of event being tracked.</span></span>                                    |
   |                 <span data-ttu-id="e0c2e-121">**最大相符項目**</span><span class="sxs-lookup"><span data-stu-id="e0c2e-121">**Maximum Matches**</span></span>                 |                                   <span data-ttu-id="e0c2e-122">要顯示的相符記錄數目。</span><span class="sxs-lookup"><span data-stu-id="e0c2e-122">The number of matches to display.</span></span>                                    |
   |                      <span data-ttu-id="e0c2e-123">**合作對象**</span><span class="sxs-lookup"><span data-stu-id="e0c2e-123">**Party**</span></span>                      |                                <span data-ttu-id="e0c2e-124">傳送訊息的組織。</span><span class="sxs-lookup"><span data-stu-id="e0c2e-124">The organization that sent the message.</span></span>                                 |
   |                      <span data-ttu-id="e0c2e-125">**通訊埠**</span><span class="sxs-lookup"><span data-stu-id="e0c2e-125">**Port**</span></span>                       |                                 <span data-ttu-id="e0c2e-126">用來處理訊息的連接埠。</span><span class="sxs-lookup"><span data-stu-id="e0c2e-126">The port used to process the message.</span></span>                                  |
   |                   <span data-ttu-id="e0c2e-127">**結構描述名稱**</span><span class="sxs-lookup"><span data-stu-id="e0c2e-127">**Schema Name**</span></span>                   |                                <span data-ttu-id="e0c2e-128">訊息使用的結構描述名稱。</span><span class="sxs-lookup"><span data-stu-id="e0c2e-128">Name of the schema used by the message.</span></span>                                 |
   |               <span data-ttu-id="e0c2e-129">**服務執行個體識別碼**</span><span class="sxs-lookup"><span data-stu-id="e0c2e-129">**Service Instance ID**</span></span>               |                             <span data-ttu-id="e0c2e-130">訊息所用的服務執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="e0c2e-130">The service instance ID used for the message.</span></span>                              |
   |                       <span data-ttu-id="e0c2e-131">**URI**</span><span class="sxs-lookup"><span data-stu-id="e0c2e-131">**URI**</span></span>                       |                                     <span data-ttu-id="e0c2e-132">用來將訊息的 URI。</span><span class="sxs-lookup"><span data-stu-id="e0c2e-132">The URI used for the message.</span></span>                                      |
   | <span data-ttu-id="e0c2e-133">**\<選取 追蹤屬性的結構描述名稱\>**</span><span class="sxs-lookup"><span data-stu-id="e0c2e-133">**\<Select a Schema Name for Tracked Properties\>**</span></span> | <span data-ttu-id="e0c2e-134">當您選取的結構描述時，該結構描述中任何升級的屬性是適合用來在查詢中。</span><span class="sxs-lookup"><span data-stu-id="e0c2e-134">When you select a schema, any promoted properties in that schema are eligible to be used in the query.</span></span> |


6. <span data-ttu-id="e0c2e-135">完成**值**適當選取您在中所做的資料行**欄位名**資料行。</span><span class="sxs-lookup"><span data-stu-id="e0c2e-135">Complete the **Value** column as appropriate for the selection you made in the **Field Name** column.</span></span>  

7. <span data-ttu-id="e0c2e-136">繼續新增其他行至適當的查詢中，藉由完成**欄位名**，**運算子**，並**值**資料行，然後再按一下**執行查詢**。</span><span class="sxs-lookup"><span data-stu-id="e0c2e-136">Continue adding additional lines to the query as appropriate by completing the **Field Name**, **Operator**, and **Values** columns, and then click **Run Query**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="e0c2e-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0c2e-137">See Also</span></span>  
 [<span data-ttu-id="e0c2e-138">使用管理主控台查詢索引標籤</span><span class="sxs-lookup"><span data-stu-id="e0c2e-138">Using the Administration Console Query Tab</span></span>](../core/using-the-administration-console-query-tab.md)