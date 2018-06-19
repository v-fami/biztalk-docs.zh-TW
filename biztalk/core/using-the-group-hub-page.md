---
title: 使用 [群組中樞] 頁面 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50693ccc-a3b2-4ad0-9a05-d60dab404a07
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e035a363b71b70db390d88a8b0e32e2e9b531d92
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288086"
---
# <a name="using-the-group-hub-page"></a><span data-ttu-id="27d75-102">使用群組中樞頁面</span><span class="sxs-lookup"><span data-stu-id="27d75-102">Using the Group Hub Page</span></span>
<span data-ttu-id="27d75-103">選取**BizTalk 群組**在 BizTalk Server 管理主控台中，節點會顯示 [BizTalk Server 群組中樞] 頁面詳細資料窗格中。</span><span class="sxs-lookup"><span data-stu-id="27d75-103">Selecting the **BizTalk Group** node in the BizTalk Server Administration Console, displays the BizTalk Server Group Hub page in the details pane.</span></span> <span data-ttu-id="27d75-104">[BizTalk Server 群組中樞] 頁面分為三個區段，會提供 BizTalk Server 系統狀況的整體檢視。</span><span class="sxs-lookup"><span data-stu-id="27d75-104">The BizTalk Server Group Hub page is divided into three sections that provide an overall view of the health of your BizTalk Server system:</span></span>  
  
-   <span data-ttu-id="27d75-105">**設定概觀**區段中，位於 [群組中樞] 頁面的上半部顯示主控件執行個體，應用程式的狀態，表示 BizTalk 群組的整體健全狀況和配接器處理常式中設定此群組中。</span><span class="sxs-lookup"><span data-stu-id="27d75-105">The **Configuration Overview** section, located in the upper part of the Group Hub page, indicates the overall health of the BizTalk group by displaying the state of the applications, host instances, and adapter handlers configured in this group.</span></span>  
  
-   <span data-ttu-id="27d75-106">**進行中的工作**和**擱置的項目**區段則位於 [群組中樞] 頁面的中間。</span><span class="sxs-lookup"><span data-stu-id="27d75-106">The **Work in Progress**  and **Suspended Items** sections are located in the middle of the Group Hub page.</span></span>  
  
    -   <span data-ttu-id="27d75-107">**進行中的工作**區段會顯示執行中服務執行個體、 凍結的協調流程、 正在重試與閒置的連接埠、 準備就緒的服務執行個體和已排程的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="27d75-107">The **Work in Progress** section displays running service instances, dehydrated orchestrations, retrying and idle ports, ready service instances, and scheduled service instances.</span></span>  
  
    -   <span data-ttu-id="27d75-108">**擱置的項目**區段會顯示已擱置的服務執行個體，並可繼續和不可繼續的執行個體的數目。</span><span class="sxs-lookup"><span data-stu-id="27d75-108">The **Suspended Items** section displays the number of suspended service instances, and resumable and non-resumable instances.</span></span>  
  
-   <span data-ttu-id="27d75-109">**分組已擱置服務執行個體**區段會顯示依應用程式、 服務名稱、 錯誤碼和 URI 分組的已擱置的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="27d75-109">The **Grouped Suspended Service Instances** section displays suspended service instances grouped by application, service name, error code, and URI.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="27d75-110">在 [群組中樞] 頁面中列出的數字只是近似的計數。</span><span class="sxs-lookup"><span data-stu-id="27d75-110">The numbers listed on the Group Hub page are approximate counts only.</span></span> <span data-ttu-id="27d75-111">例如下, 顯示的數字**執行服務執行個體**或**已擱置服務執行個體**可能不等於執行中服務執行個體或已擱置的服務執行個體的總數因為正在產生 [中樞] 頁面上的各種統計資料時，無法變更系統的狀態。</span><span class="sxs-lookup"><span data-stu-id="27d75-111">For example, the numbers displayed under **Running service instances** or **Suspended service instances** might not equal the total number of running service instances or suspended service instances because the state of the system could change while the various statistics on the Hub page are being generated.</span></span>  
  
-   <span data-ttu-id="27d75-112">**追蹤服務執行個體**和**追蹤訊息事件**區段訊息事件和狀態的服務執行個體的最大相符項目上執行查詢 = 50。</span><span class="sxs-lookup"><span data-stu-id="27d75-112">The **Tracked Service Instances** and **Tracked Message Events** sections execute queries on message events and the state of service instances with a maximum match = 50.</span></span>  
  
    -   <span data-ttu-id="27d75-113">**追蹤服務執行個體**查詢會搜尋搜尋受到追蹤的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="27d75-113">**Tracked service instances** query searches for tracked service instances.</span></span>  
  
    -   <span data-ttu-id="27d75-114">**已完成執行個體**查詢會搜尋搜尋受到追蹤的服務執行個體等於完成狀態。</span><span class="sxs-lookup"><span data-stu-id="27d75-114">**Completed instances** query searches for tracked service instances with state equal to completed.</span></span>  
  
    -   <span data-ttu-id="27d75-115">**終止執行個體**查詢會搜尋搜尋受到追蹤的服務執行個體的狀態等於終止。</span><span class="sxs-lookup"><span data-stu-id="27d75-115">**Terminated instances** query searches for tracked service instances with state equal to terminated.</span></span>  
  
    -   <span data-ttu-id="27d75-116">**追蹤訊息事件**查詢搜尋的追蹤的訊息事件。</span><span class="sxs-lookup"><span data-stu-id="27d75-116">**Tracked message events** query searches for tracked message events.</span></span>  
  
    -   <span data-ttu-id="27d75-117">**傳輸失敗事件**查詢搜尋的傳輸失敗的事件類型的追蹤的訊息事件。</span><span class="sxs-lookup"><span data-stu-id="27d75-117">**Transmission failure events** query searches for tracked message events with an event type of transmission failure.</span></span>  
  
-   <span data-ttu-id="27d75-118">**EDI 狀態報告**和**EDIINT 狀態報告**區段，位於 群組中樞 頁面底部會顯示有關 EDI 交換的四個報表和相關 AS2 交換的其中一個： EDI 交換和相互關聯的 ACK 狀態報表、 批次狀態報告中，交換彙總報告、 交易集彙總報告和 AS2 訊息和相互關聯的 MDN 狀態報告。</span><span class="sxs-lookup"><span data-stu-id="27d75-118">The **EDI Status Reports** and **EDIINT Status Reports** sections, located at the bottom of the Group Hub page, displays four reports about EDI interchanges and one about AS2 interchanges: the EDI Interchange and Correlated ACK Status reports, the Batch Status report, the Interchange Aggregation Report, the Transaction Set Aggregation Report, and the AS2 Message and Correlated MDN Status report.</span></span> <span data-ttu-id="27d75-119">如需有關這些報表的詳細資訊，請參閱[EDI 和 AS2 狀態報告](../core/edi-and-as2-status-reporting.md)。</span><span class="sxs-lookup"><span data-stu-id="27d75-119">For more information about these reports, see [EDI and AS2 Status Reporting](../core/edi-and-as2-status-reporting.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="27d75-120">如果此 BizTalk 群組設定 EDI/AS2 功能，則只會顯示 EDI 和 EDIINT 狀態報告的區段。</span><span class="sxs-lookup"><span data-stu-id="27d75-120">The EDI and EDIINT Status Report sections will only be displayed if the EDI/AS2 features are configured for this BizTalk group.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27d75-121">本節內容</span><span class="sxs-lookup"><span data-stu-id="27d75-121">In This Section</span></span>  
  
-   [<span data-ttu-id="27d75-122">服務執行個體狀態</span><span class="sxs-lookup"><span data-stu-id="27d75-122">Service Instance States</span></span>](../core/service-instance-states.md)  
  
-   [<span data-ttu-id="27d75-123">調查協調流程、 連接埠和訊息失敗</span><span class="sxs-lookup"><span data-stu-id="27d75-123">Investigating Orchestration, Port, and Message Failures</span></span>](../core/investigating-orchestration-port-and-message-failures.md)  
  
-   [<span data-ttu-id="27d75-124">使用管理主控台查詢索引標籤</span><span class="sxs-lookup"><span data-stu-id="27d75-124">Using the Administration Console Query Tab</span></span>](../core/using-the-administration-console-query-tab.md)  
  
-   [<span data-ttu-id="27d75-125">檢視追蹤的訊息和執行個體資料</span><span class="sxs-lookup"><span data-stu-id="27d75-125">Viewing Tracked Message and Instance Data</span></span>](../core/viewing-tracked-message-and-instance-data.md)  
  
-   [<span data-ttu-id="27d75-126">健全狀況與活動追蹤</span><span class="sxs-lookup"><span data-stu-id="27d75-126">Health and Activity Tracking</span></span>](../core/health-and-activity-tracking.md)