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
ms.openlocfilehash: 24798038ef7110a87efef2850c7787c066ae9511
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="sql-processing-in-btarn"></a><span data-ttu-id="38155-102">BTARN 中的 SQL 處理</span><span class="sxs-lookup"><span data-stu-id="38155-102">SQL Processing in BTARN</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="38155-103">[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]使用 SQL 配接器的特定業務 (LOB) 應用程式將訊息路由傳送。</span><span class="sxs-lookup"><span data-stu-id="38155-103"> [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] uses a SQL adapter to route a message from the line-of-business (LOB) application.</span></span> <span data-ttu-id="38155-104">並使用 SQL 傳送埠將訊息傳送到 LOB 應用程式。</span><span class="sxs-lookup"><span data-stu-id="38155-104">It uses a SQL send port to route a message to the LOB application.</span></span>  
  
## <a name="message-flow"></a><span data-ttu-id="38155-105">訊息流程</span><span class="sxs-lookup"><span data-stu-id="38155-105">Message Flow</span></span>  
 <span data-ttu-id="38155-106">啟動器或回應者電腦上後, 端 LOB 應用程式將訊息路由至 MessagesFromLOB 資料表[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]資料[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]資料庫。</span><span class="sxs-lookup"><span data-stu-id="38155-106">On either the initiator or responder computer, the back-end LOB application routes a message to the MessagesFromLOB table of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="38155-107">使用 SQL 配接器將訊息從 MessagesFromLOB 資料表移到私用程序。</span><span class="sxs-lookup"><span data-stu-id="38155-107"> uses a SQL adapter to move the message from the MessagesFromLOB table to the private process.</span></span> <span data-ttu-id="38155-108">如需詳細資訊，請參閱 BizTalk Server 說明中的 「 SQL 配接器 >。</span><span class="sxs-lookup"><span data-stu-id="38155-108">For more information, see "SQL Adapter" in BizTalk Server Help.</span></span>  
  
 <span data-ttu-id="38155-109">您可以選擇使用檔案配接器提交服務內容到 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]，而不要使用預設的 SQL 配接器。</span><span class="sxs-lookup"><span data-stu-id="38155-109">You can choose to use a File adapter to submit service content to [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], instead of using the default SQL adapter.</span></span> <span data-ttu-id="38155-110">如果選擇使用檔案配接器，則 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 不支援附件。</span><span class="sxs-lookup"><span data-stu-id="38155-110">If you choose to use a File adapter, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not support attachments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38155-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="38155-111">See Also</span></span>  
 [<span data-ttu-id="38155-112">BTARN 中的訊息處理</span><span class="sxs-lookup"><span data-stu-id="38155-112">Message Processing in BTARN</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md)