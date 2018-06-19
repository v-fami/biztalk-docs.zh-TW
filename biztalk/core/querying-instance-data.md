---
title: 查詢執行個體資料 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAM, instance data
- queries [BAM], instance data
ms.assetid: ae4a8854-d5c2-4b36-a0ef-3f74e138306e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e43310756cf12c0c2a48eb6716221afc5395ecb0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25971828"
---
# <a name="querying-instance-data"></a><span data-ttu-id="920a8-102">查詢執行個體資料</span><span class="sxs-lookup"><span data-stu-id="920a8-102">Querying Instance Data</span></span>
<span data-ttu-id="920a8-103">透過 BAM 主要匯入資料庫中動態建立的 SQL 檢視，可以查詢有關個別活動執行個體的資料。</span><span class="sxs-lookup"><span data-stu-id="920a8-103">The data about individual activity instances is available for queries in a dynamically created SQL View in the BAM Primary Import Database.</span></span>  
  
 <span data-ttu-id="920a8-104">這個檢視的名稱為</span><span class="sxs-lookup"><span data-stu-id="920a8-104">The name of this view is</span></span>  
  
 <span data-ttu-id="920a8-105">**bam_\<**  *ViewName*  **\>_\<**  *ActivityName* **\>檢視 （_v)**</span><span class="sxs-lookup"><span data-stu-id="920a8-105">**bam_\<** *ViewName* **\>_\<** *ActivityName* **\>_View**</span></span>  
  
 <span data-ttu-id="920a8-106">位置</span><span class="sxs-lookup"><span data-stu-id="920a8-106">Where</span></span>  
  
 <span data-ttu-id="920a8-107">**\<***ViewName*  **\>** 是 BAM 定義 XML 中 View 項目的 Name 屬性相同相關 Microsoft Excel 精靈中輸入的檢視名稱。</span><span class="sxs-lookup"><span data-stu-id="920a8-107">**\<** *ViewName* **\>** is the Name Attribute of the View element in the BAM Definition XML, which is the same as the View Name entered in the related Microsoft Excel wizards.</span></span>  
  
 <span data-ttu-id="920a8-108">**\<***ActivityName*  **\>** 是 BAM 定義 XML 中 Activity 項目的 Name 屬性相同 Excel 精靈中輸入的活動名稱。</span><span class="sxs-lookup"><span data-stu-id="920a8-108">**\<** *ActivityName* **\>** is the Name Attribute of the Activity element in the BAM Definition XML, which is the same as the Activity Name entered in the Excel wizards.</span></span>  
  
 <span data-ttu-id="920a8-109">在查詢執行個體資料時，請特別注意下列條件：</span><span class="sxs-lookup"><span data-stu-id="920a8-109">It is important to note the following conditions when querying instance data:</span></span>  
  
-   <span data-ttu-id="920a8-110">如果您透過 DirectEventStream 將活動資料傳送至 BAM，執行個體資料便不會延遲，這表示只要呼叫應用程式中的交易一經過認可，執行個體資料就會立即顯示出來。</span><span class="sxs-lookup"><span data-stu-id="920a8-110">If you send activity data to BAM via the DirectEventStream, the instance data has no latency, meaning that it appears instantaneously when the transaction in the calling application commits.</span></span>  
  
-   <span data-ttu-id="920a8-111">如果透過 BufferedEventStream 將活動資料傳送至 BAM，將會根據 BAM 事件匯流排服務的負載，以及裝載 BAM 主要匯入資料庫的 SQL Server，在幾秒鐘後顯示查詢的執行個體資料。</span><span class="sxs-lookup"><span data-stu-id="920a8-111">If the activity data is sent to BAM via the BufferedEventStream, the instance data will show up for queries a few seconds later, depending on the load of the BAM Event Bus service and the SQL server that hosts the BAM Primary Import Database.</span></span>  
  
-   <span data-ttu-id="920a8-112">此檢視背後的資料表實際結構更為複雜，這都是為了確保目前或最近活動的資料可供查詢使用，至於已經完成且使用中查詢也不再需要的活動資料，就會封存起來或清除，而不需要讓系統離線。</span><span class="sxs-lookup"><span data-stu-id="920a8-112">The actual structure of tables behind this view is more complex to ensure that the data for the current or recent activities is available for queries, while data for activities that have completed and is no longer required for active queries is archived or purged without taking the system offline.</span></span> <span data-ttu-id="920a8-113">如需詳細資訊，請參閱[活動資料儲存區](../core/activity-data-storage.md)。</span><span class="sxs-lookup"><span data-stu-id="920a8-113">For more information, see [Activity Data Storage](../core/activity-data-storage.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="920a8-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="920a8-114">See Also</span></span>  
 <span data-ttu-id="920a8-115">[活動資料儲存區](../core/activity-data-storage.md) </span><span class="sxs-lookup"><span data-stu-id="920a8-115">[Activity Data Storage](../core/activity-data-storage.md) </span></span>  
 [<span data-ttu-id="920a8-116">查詢 BAM 資料</span><span class="sxs-lookup"><span data-stu-id="920a8-116">Querying BAM Data</span></span>](../core/querying-bam-data.md)