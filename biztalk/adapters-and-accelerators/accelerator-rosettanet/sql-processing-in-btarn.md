---
title: "BTARN 中的 SQL 處理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- line-of-business applications (LOBs)
- LOBs
- SQL processing
- messages, message flow
- BTARN, SQL processing
ms.assetid: cfaf804f-3803-438e-a22e-50f487fe21c3
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9cf1aba9f2d4d2ea77f369e76c277160739f7f17
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sql-processing-in-btarn"></a><span data-ttu-id="ce415-102">BTARN 中的 SQL 處理</span><span class="sxs-lookup"><span data-stu-id="ce415-102">SQL Processing in BTARN</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="ce415-103">[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]使用 SQL 配接器的特定業務 (LOB) 應用程式將訊息路由傳送。</span><span class="sxs-lookup"><span data-stu-id="ce415-103"> [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] uses a SQL adapter to route a message from the line-of-business (LOB) application.</span></span> <span data-ttu-id="ce415-104">並使用 SQL 傳送埠將訊息傳送到 LOB 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ce415-104">It uses a SQL send port to route a message to the LOB application.</span></span>  
  
## <a name="message-flow"></a><span data-ttu-id="ce415-105">訊息流程</span><span class="sxs-lookup"><span data-stu-id="ce415-105">Message Flow</span></span>  
 <span data-ttu-id="ce415-106">啟動器或回應者電腦上後, 端 LOB 應用程式將訊息路由至 MessagesFromLOB 資料表[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]資料[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]資料庫。</span><span class="sxs-lookup"><span data-stu-id="ce415-106">On either the initiator or responder computer, the back-end LOB application routes a message to the MessagesFromLOB table of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="ce415-107">使用 SQL 配接器將訊息從 MessagesFromLOB 資料表移到私用程序。</span><span class="sxs-lookup"><span data-stu-id="ce415-107"> uses a SQL adapter to move the message from the MessagesFromLOB table to the private process.</span></span> <span data-ttu-id="ce415-108">如需詳細資訊，請參閱「[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] 說明」中的＜SQL 配接器＞。</span><span class="sxs-lookup"><span data-stu-id="ce415-108">For more information, see "SQL Adapter" in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
 <span data-ttu-id="ce415-109">您可以選擇使用檔案配接器提交服務內容到 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]，而不要使用預設的 SQL 配接器。</span><span class="sxs-lookup"><span data-stu-id="ce415-109">You can choose to use a File adapter to submit service content to [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], instead of using the default SQL adapter.</span></span> <span data-ttu-id="ce415-110">如果選擇使用檔案配接器，則 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 不支援附件。</span><span class="sxs-lookup"><span data-stu-id="ce415-110">If you choose to use a File adapter, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not support attachments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce415-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce415-111">See Also</span></span>  
 [<span data-ttu-id="ce415-112">BTARN 中的訊息處理</span><span class="sxs-lookup"><span data-stu-id="ce415-112">Message Processing in BTARN</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md)