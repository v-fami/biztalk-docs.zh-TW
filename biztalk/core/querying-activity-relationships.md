---
title: 查詢活動關係 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAM, activity relationships
- queries [BAM], relationships
ms.assetid: e3d42b7c-cc11-4707-9095-cfc518902b26
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18cec34263598f50c9852ffe3f3a7d749914c977
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984015"
---
# <a name="querying-activity-relationships"></a><span data-ttu-id="e39ff-102">查詢活動關係</span><span class="sxs-lookup"><span data-stu-id="e39ff-102">Querying Activity Relationships</span></span>
<span data-ttu-id="e39ff-103">活動關係資訊可以在為每個活動動態建立的 SQL 檢視中取得。</span><span class="sxs-lookup"><span data-stu-id="e39ff-103">The activity relationship information is available in a dynamically created SQL view for each activity.</span></span> <span data-ttu-id="e39ff-104">這個檢視的名稱為</span><span class="sxs-lookup"><span data-stu-id="e39ff-104">The name of this view is</span></span>  
  
 <span data-ttu-id="e39ff-105">**bam_\<**  *活動*  **\>_AllRelationships**</span><span class="sxs-lookup"><span data-stu-id="e39ff-105">**bam_\<** *Activity* **\>_AllRelationships**</span></span>  
  
 <span data-ttu-id="e39ff-106">何處\<*活動*\>是 BAM 定義 XML 中 Activity 項目的 Name 屬性與輸入使用適用於 Excel 的 BAM 增益集的 Activity 名稱相同。</span><span class="sxs-lookup"><span data-stu-id="e39ff-106">Where \<*Activity*\> is the Name attribute of the Activity element in the BAM definition XML, which is the same as the Activity name entered using the BAM Add-in for Excel.</span></span>  
  
 <span data-ttu-id="e39ff-107">關係事件會發生在特定活動的環境中。</span><span class="sxs-lookup"><span data-stu-id="e39ff-107">The relationship events occur in the context of a specific activity.</span></span> <span data-ttu-id="e39ff-108">比方說，如果採購單和出貨之間的關係發生 Purchase Order 活動的內容中，關聯性記錄將會出現在**bam_PurchaseOrder_AllRelationships**，但無法顯示於**bam_Shipment_AllRelationships**。</span><span class="sxs-lookup"><span data-stu-id="e39ff-108">For example, if the relationship between Purchase Order and Shipment occurs in the context of the Purchase Order activity, the Relationship record will show up in **bam_PurchaseOrder_AllRelationships**, but not in **bam_Shipment_AllRelationships**.</span></span> <span data-ttu-id="e39ff-109">如需詳細資訊，請參閱 <<c0> [ 活動關係](../core/activity-relationships.md)。</span><span class="sxs-lookup"><span data-stu-id="e39ff-109">For more information, see [Activity Relationships](../core/activity-relationships.md).</span></span>  
  
 <span data-ttu-id="e39ff-110">若要尋找所有要購買的相關的活動可讓您排序您要查詢這兩個檢視**bam_PurchaseOrder_AllRelationships**以及 所有檢視**bam_\<**<em>OtherActivity</em>  **\>_AllRelationships**，其中\< *OtherActivity* \>是相同的 BAM 檢視中的活動。</span><span class="sxs-lookup"><span data-stu-id="e39ff-110">To find all the related activities to a purchase order you need to query both the view **bam_PurchaseOrder_AllRelationships** as well as all views **bam_\<**<em>OtherActivity</em>**\>_AllRelationships**, where \<*OtherActivity*\> is the activity in the same BAM view.</span></span>  
  
 <span data-ttu-id="e39ff-111">關係記錄屬於活動執行個體，以及它們保留的執行個體資料的同步處理中所述[活動資料儲存區](../core/activity-data-storage.md)。</span><span class="sxs-lookup"><span data-stu-id="e39ff-111">The relationship records are part of the activity instance and they are maintained in synchronization with the instance data as described in [Activity Data Storage](../core/activity-data-storage.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e39ff-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e39ff-112">See Also</span></span>  
 [<span data-ttu-id="e39ff-113">查詢 BAM 資料</span><span class="sxs-lookup"><span data-stu-id="e39ff-113">Querying BAM Data</span></span>](../core/querying-bam-data.md)