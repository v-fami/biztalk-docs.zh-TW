---
title: 調整大小以追蹤訊息內文追蹤資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tracking database, database size
- message variables [Tracking database], MsgNum
- HAT, ports
- Tracking database, messages
- tracking, orchestrations
- tracking, messages
- HAT, orchestrations
- tracking, ports
ms.assetid: ee75e530-f15d-4ceb-ba67-0b0b24d9df6b
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b5abc3f2a48f2baea5d158e1a0268a7eede51c2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277918"
---
# <a name="sizing-the-tracking-database-to-track-message-bodies"></a><span data-ttu-id="1998c-102">將追蹤資料庫的大小調整為追蹤訊息內文</span><span class="sxs-lookup"><span data-stu-id="1998c-102">Sizing the Tracking Database to Track Message Bodies</span></span>
<span data-ttu-id="1998c-103">若您計劃追蹤 BizTalk 追蹤資料庫中的訊息內文，也需要將這些內文的大小納入計算。</span><span class="sxs-lookup"><span data-stu-id="1998c-103">If you plan to track the message bodies in the BizTalk Tracking database, then you will also need to account for the size of these bodies in your calculation.</span></span> <span data-ttu-id="1998c-104">使用以下方程式：</span><span class="sxs-lookup"><span data-stu-id="1998c-104">Use the following equation:</span></span>  
  
```  
[Msgs * MsgNum * (MsgSize)]/1024 = Data size in MB  
```  
  
 <span data-ttu-id="1998c-105">若與訊息大小比起來相差很多，請考慮將訊息內容的平均大小加到上述的 MsgSize。</span><span class="sxs-lookup"><span data-stu-id="1998c-105">Consider adding the average size of the message context to MsgSize above if it is significant compared to the message size.</span></span>  
  
 <span data-ttu-id="1998c-106">MsgNum 變數取決於開啟連接埠層級或使用訊息事件和服務執行個體追蹤在 [群組中樞] 頁面中的協調流程層級的追蹤功能。</span><span class="sxs-lookup"><span data-stu-id="1998c-106">The MsgNum variable is determined by turning on the tracking features at the port level or at the orchestration level using the message event and service instance tracking in the Group Hub page.</span></span> <span data-ttu-id="1998c-107">您也必須將此公式套用到每個訊息處理。</span><span class="sxs-lookup"><span data-stu-id="1998c-107">You must apply this formula to each message process as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1998c-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1998c-108">See Also</span></span>  
 <span data-ttu-id="1998c-109">[使用訊息變數調整追蹤資料庫的大小](../core/using-message-variables-to-size-the-tracking-database.md) </span><span class="sxs-lookup"><span data-stu-id="1998c-109">[Using Message Variables to Size the Tracking Database](../core/using-message-variables-to-size-the-tracking-database.md) </span></span>  
 <span data-ttu-id="1998c-110">[案例 1： 針對簡單 BizTalk 訊息調整追蹤資料庫](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md) </span><span class="sxs-lookup"><span data-stu-id="1998c-110">[Scenario 1: Sizing the Tracking Database  for Simple BizTalk Messages](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md) </span></span>  
 <span data-ttu-id="1998c-111">[案例 2： 在協調流程中的訊息調整追蹤資料庫](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="1998c-111">[Scenario 2: Sizing the Tracking Database  for Messages in Orchestrations](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md) </span></span>  
 <span data-ttu-id="1998c-112">[案例 4： 所有訊息調整追蹤資料庫](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md) </span><span class="sxs-lookup"><span data-stu-id="1998c-112">[Scenario 4: Sizing the Tracking Database for all Messages](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md) </span></span>  
 [<span data-ttu-id="1998c-113">案例 3： 調整追蹤資料庫外送到通訊群組清單之訊息的大小</span><span class="sxs-lookup"><span data-stu-id="1998c-113">Scenario 3: Sizing the Tracking Database  for Messages Sent Out to Distribution Lists</span></span>](../core/scenario-3-size-the-tracking-database-for-messages-sent-to-distribution-lists.md)