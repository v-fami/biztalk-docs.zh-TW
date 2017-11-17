---
title: "使用管理主控台查詢索引標籤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Administration Console [BizTalk Server], Query tab
- Query tab [Administration Console]
ms.assetid: 7655f0b6-9217-46c4-88e0-ca2e661ce7a6
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f20046580913ee8ea3ccb4a742ab693bcaa08d38
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-administration-console-query-tab"></a><span data-ttu-id="d70ac-102">使用管理主控台查詢索引標籤</span><span class="sxs-lookup"><span data-stu-id="d70ac-102">Using the Administration Console Query Tab</span></span>
<span data-ttu-id="d70ac-103">您可使用 BizTalk Server 管理主控台中 [群組中樞] 頁面的 [查詢] 索引標籤，搜尋並找出特定正在執行或已擱置的服務執行個體、訊息或訂閱。</span><span class="sxs-lookup"><span data-stu-id="d70ac-103">You can use the Query tab on the Group Hub page in the BizTalk Server Administration Console to search for and locate specific running and suspended service instances, messages, or subscriptions.</span></span> <span data-ttu-id="d70ac-104">使用「管理主控台」執行的查詢，可找到儲存在 MessageBox 資料庫的即時項目。</span><span class="sxs-lookup"><span data-stu-id="d70ac-104">Queries performed using the Administration Console locate live items, which are stored in the MessageBox database.</span></span> <span data-ttu-id="d70ac-105">每次執行新查詢時，會顯示新查詢索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d70ac-105">A new query tab appears each time you run a new query.</span></span>  
  
 <span data-ttu-id="d70ac-106">若要找到追蹤或封存的訊息或服務執行個體，您可以使用訊息事件和服務執行個體的追蹤。</span><span class="sxs-lookup"><span data-stu-id="d70ac-106">To locate tracked or archived messages or service instances, you use message event and service instance tracking.</span></span> <span data-ttu-id="d70ac-107">如需詳細資訊，請參閱[檢視追蹤的訊息和執行個體資料](../core/viewing-tracked-message-and-instance-data.md)。</span><span class="sxs-lookup"><span data-stu-id="d70ac-107">For more information, see [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d70ac-108">當您執行的服務執行個體的查詢時，會傳回結果集將會顯示值為**\<名稱不是使用 >**的**ServiceName**欄位的服務執行個體，如果對應的傳送埠，接收位置或協調流程已被刪除。</span><span class="sxs-lookup"><span data-stu-id="d70ac-108">When you execute a query for service instances, the result set that is returned will display a value of **\<Name is not available>** for the **ServiceName** field of a service instance if the corresponding send port, receive location, or orchestration has been deleted.</span></span>  <span data-ttu-id="d70ac-109">**ServiceName**服務執行個體的欄位會填入對應到 BizTalk 管理資料庫中的傳送埠的易記名稱、 接收位置或協調流程。</span><span class="sxs-lookup"><span data-stu-id="d70ac-109">The **ServiceName** field of a service instance is populated by a lookup into the BizTalk management database for the friendly name of the send port, receive location, or orchestration.</span></span>  <span data-ttu-id="d70ac-110">如果傳送埠，接收位置或協調流程刪除然後好記的名稱查閱失敗和**\<沒有名稱 >**隨即出現。</span><span class="sxs-lookup"><span data-stu-id="d70ac-110">If the send port, receive location, or orchestration is deleted then the lookup for the friendly name fails and **\<Name is not available>** is displayed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d70ac-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="d70ac-111">In This Section</span></span>  
  
-   [<span data-ttu-id="d70ac-112">如何開啟已儲存的查詢</span><span class="sxs-lookup"><span data-stu-id="d70ac-112">How to Open a Saved Query</span></span>](../core/how-to-open-a-saved-query.md)  
  
-   [<span data-ttu-id="d70ac-113">如何搜尋所有服務執行個體</span><span class="sxs-lookup"><span data-stu-id="d70ac-113">How to Search for All Service Instances</span></span>](../core/how-to-search-for-all-service-instances.md)  
  
-   [<span data-ttu-id="d70ac-114">如何搜尋執行中服務執行個體</span><span class="sxs-lookup"><span data-stu-id="d70ac-114">How to Search for Running Service Instances</span></span>](../core/how-to-search-for-running-service-instances.md)  
  
-   [<span data-ttu-id="d70ac-115">如何搜尋已擱置的服務執行個體</span><span class="sxs-lookup"><span data-stu-id="d70ac-115">How to Search for Suspended Service Instances</span></span>](../core/how-to-search-for-suspended-service-instances.md)  
  
-   [<span data-ttu-id="d70ac-116">如何搜尋訊息</span><span class="sxs-lookup"><span data-stu-id="d70ac-116">How to Search for Messages</span></span>](../core/how-to-search-for-messages.md)  
  
-   [<span data-ttu-id="d70ac-117">如何搜尋訂閱</span><span class="sxs-lookup"><span data-stu-id="d70ac-117">How to Search for Subscriptions</span></span>](../core/how-to-search-for-subscriptions.md)  
  
-   [<span data-ttu-id="d70ac-118">如何儲存查詢</span><span class="sxs-lookup"><span data-stu-id="d70ac-118">How to Save a Query</span></span>](../core/how-to-save-a-query.md)  
  
-   [<span data-ttu-id="d70ac-119">如何搜尋追蹤的訊息事件</span><span class="sxs-lookup"><span data-stu-id="d70ac-119">How to Search for Tracked Message Events</span></span>](../core/how-to-search-for-tracked-message-events.md)  
  
-   [<span data-ttu-id="d70ac-120">如何搜尋受到追蹤的服務執行個體</span><span class="sxs-lookup"><span data-stu-id="d70ac-120">How to Search for Tracked Service Instances</span></span>](../core/how-to-search-for-tracked-service-instances.md)