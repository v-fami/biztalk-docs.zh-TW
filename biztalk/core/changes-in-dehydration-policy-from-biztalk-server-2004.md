---
title: "從 BizTalk Server 2004 的凍結原則變更 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c760bffe-5f64-4eb2-bc23-89d7c9310f39
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 167c53d953369d7b35138995b4f38ad8994c18cb
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="changes-in-dehydration-policy-from-biztalk-server-2004"></a><span data-ttu-id="a6731-102">BizTalk Server 2004 中的凍結原則變更</span><span class="sxs-lookup"><span data-stu-id="a6731-102">Changes in Dehydration Policy from BizTalk Server 2004</span></span>
<span data-ttu-id="a6731-103">BizTalk Server 凍結原則已經從[!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)]至 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="a6731-103">BizTalk Server dehydration policy has changed from [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] to BizTalk Server.</span></span> <span data-ttu-id="a6731-104">間之差異的說明[!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)]和 BizTalk Server 可以由下列的布林值，判斷中的凍結摘要[!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)](true = 凍結)</span><span class="sxs-lookup"><span data-stu-id="a6731-104">The explanation for the difference between [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] and BizTalk Server can be summarized by the following Boolean that determines dehydration in [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] (true = dehydrate)</span></span>  
  
```  
Dehydrate = (WaitingHistory == -1 OR WaitingHistory > TestThreshold)  
```  
  
 <span data-ttu-id="a6731-105">BizTalk Server 凍結原則已變更此次要的方式。</span><span class="sxs-lookup"><span data-stu-id="a6731-105">Dehydration policy for BizTalk Server has changed in this minor way.</span></span> <span data-ttu-id="a6731-106">BizTalk Server 一律會凍結在接收/延遲/接聽如果等待時間超過 2 ***MaxThreshold**。</span><span class="sxs-lookup"><span data-stu-id="a6731-106">BizTalk Server always dehydrates at a receive/delay/listen if there is a wait longer than 2***MaxThreshold**.</span></span>