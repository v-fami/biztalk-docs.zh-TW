---
title: BTARN 中的 SQL 處理 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- line-of-business applications (LOBs)
- LOBs
- SQL processing
- messages, message flow
- BTARN, SQL processing
ms.assetid: cfaf804f-3803-438e-a22e-50f487fe21c3
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21255c03a9a9c1f2a30eb7f716c5e1bf285a3c5b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000711"
---
# <a name="sql-processing-in-btarn"></a><span data-ttu-id="0f67d-102">BTARN 中的 SQL 處理</span><span class="sxs-lookup"><span data-stu-id="0f67d-102">SQL Processing in BTARN</span></span>
<span data-ttu-id="0f67d-103">Microsoft[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]使用 SQL 配接器從的營運 (LOB) 應用程式將訊息路由傳送。</span><span class="sxs-lookup"><span data-stu-id="0f67d-103">Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] uses a SQL adapter to route a message from the line-of-business (LOB) application.</span></span> <span data-ttu-id="0f67d-104">並使用 SQL 傳送埠將訊息傳送到 LOB 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0f67d-104">It uses a SQL send port to route a message to the LOB application.</span></span>  
  
## <a name="message-flow"></a><span data-ttu-id="0f67d-105">訊息流程</span><span class="sxs-lookup"><span data-stu-id="0f67d-105">Message Flow</span></span>  
 <span data-ttu-id="0f67d-106">起始端或回應者電腦上後, 端 LOB 應用程式將訊息路由至 MessagesFromLOB 資料表[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]資料[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]資料庫。</span><span class="sxs-lookup"><span data-stu-id="0f67d-106">On either the initiator or responder computer, the back-end LOB application routes a message to the MessagesFromLOB table of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="0f67d-107"> 使用 SQL 配接器將訊息從 MessagesFromLOB 資料表移到私用程序。</span><span class="sxs-lookup"><span data-stu-id="0f67d-107"> uses a SQL adapter to move the message from the MessagesFromLOB table to the private process.</span></span> <span data-ttu-id="0f67d-108">如需詳細資訊，請參閱 BizTalk Server 說明中的 「 SQL 配接器 」。</span><span class="sxs-lookup"><span data-stu-id="0f67d-108">For more information, see "SQL Adapter" in BizTalk Server Help.</span></span>  
  
 <span data-ttu-id="0f67d-109">您可以選擇使用檔案配接器提交服務內容到 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]，而不要使用預設的 SQL 配接器。</span><span class="sxs-lookup"><span data-stu-id="0f67d-109">You can choose to use a File adapter to submit service content to [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], instead of using the default SQL adapter.</span></span> <span data-ttu-id="0f67d-110">如果選擇使用檔案配接器，則 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 不支援附件。</span><span class="sxs-lookup"><span data-stu-id="0f67d-110">If you choose to use a File adapter, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not support attachments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f67d-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f67d-111">See Also</span></span>  
 [<span data-ttu-id="0f67d-112">BTARN 中的訊息處理</span><span class="sxs-lookup"><span data-stu-id="0f67d-112">Message Processing in BTARN</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md)