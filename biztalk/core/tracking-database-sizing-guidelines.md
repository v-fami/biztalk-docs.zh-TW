---
title: "追蹤資料庫大小的指導方針 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking database, performance
- Tracking database, size
- Tracking Analysis Server database [BAM]
- performance, Tracking database
ms.assetid: 2188bee5-c0dd-4448-bd4a-4ffb2a0c79f1
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c0293ff0a03583e51ee447ec1bd6283f1b02164
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tracking-database-sizing-guidelines"></a><span data-ttu-id="5f5f9-102">調整追蹤資料庫大小的指導方針</span><span class="sxs-lookup"><span data-stu-id="5f5f9-102">Tracking Database Sizing Guidelines</span></span>
<span data-ttu-id="5f5f9-103">本節描述調整 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中 BizTalk 追蹤 (BizTalkDTADb) 資料庫大小的考量。</span><span class="sxs-lookup"><span data-stu-id="5f5f9-103">This section describes sizing considerations for the BizTalk Tracking (BizTalkDTADb) database in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="5f5f9-104">它說明如何使用方程式與訊息變數來決定 BizTalk 追蹤資料庫在經過一段指定時間後的大小，並提供如何套用方程式的特定範例。</span><span class="sxs-lookup"><span data-stu-id="5f5f9-104">It explains how to use equations and message variables to determine how large the BizTalk Tracking database will become over a given period of time, and provides specific examples of how to apply the equations.</span></span> <span data-ttu-id="5f5f9-105">如此概略提供了 BizTalk 訊息、追蹤設定及追蹤資料庫大小之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="5f5f9-105">This provides the rough co-relation between BizTalk messages, tracking settings and the tracking database size.</span></span> <span data-ttu-id="5f5f9-106">它並未考慮其他 SQL Server 因數，像是追蹤資料表中的索引大小，您可能需要針對這些因數考慮合理的倍數。</span><span class="sxs-lookup"><span data-stu-id="5f5f9-106">It does not take into account other SQL Server factors such as index size in the tracking tables; you may want to consider reasonable multipliers to account for those factors.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5f5f9-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="5f5f9-107">In This Section</span></span>  
  
-   [<span data-ttu-id="5f5f9-108">使用訊息變數調整追蹤資料庫的大小</span><span class="sxs-lookup"><span data-stu-id="5f5f9-108">Using Message Variables to Size the Tracking Database</span></span>](../core/using-message-variables-to-size-the-tracking-database.md)  
  
-   [<span data-ttu-id="5f5f9-109">追蹤訊息內文追蹤資料庫設定大小</span><span class="sxs-lookup"><span data-stu-id="5f5f9-109">Sizing the Tracking Database to Track Message Bodies</span></span>](../core/sizing-the-tracking-database-to-track-message-bodies.md)  
  
-   [<span data-ttu-id="5f5f9-110">案例 1： 針對簡單 BizTalk 訊息調整追蹤資料庫</span><span class="sxs-lookup"><span data-stu-id="5f5f9-110">Scenario 1: Sizing the Tracking Database  for Simple BizTalk Messages</span></span>](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md)  
  
-   [<span data-ttu-id="5f5f9-111">案例 2： 在協調流程中的訊息調整追蹤資料庫</span><span class="sxs-lookup"><span data-stu-id="5f5f9-111">Scenario 2: Sizing the Tracking Database  for Messages in Orchestrations</span></span>](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md)  
  
-   [<span data-ttu-id="5f5f9-112">案例 3： 調整追蹤資料庫外送到通訊群組清單之訊息的大小</span><span class="sxs-lookup"><span data-stu-id="5f5f9-112">Scenario 3: Sizing the Tracking Database  for Messages Sent Out to Distribution Lists</span></span>](../core/scenario-3-size-the-tracking-database-for-messages-sent-to-distribution-lists.md)  
  
-   [<span data-ttu-id="5f5f9-113">案例 4： 所有訊息調整追蹤資料庫</span><span class="sxs-lookup"><span data-stu-id="5f5f9-113">Scenario 4: Sizing the Tracking Database for all Messages</span></span>](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md)  
  
## <a name="see-also"></a><span data-ttu-id="5f5f9-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f5f9-114">See Also</span></span>  
 <span data-ttu-id="5f5f9-115">[追蹤資料庫中的記錄大小](../core/record-size-in-tracking-databases.md) </span><span class="sxs-lookup"><span data-stu-id="5f5f9-115">[Record Size in Tracking Databases](../core/record-size-in-tracking-databases.md) </span></span>  
 [<span data-ttu-id="5f5f9-116">備份和還原 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="5f5f9-116">Backing Up and Restoring BizTalk Server Databases</span></span>](../core/backing-up-and-restoring-biztalk-server-databases.md)