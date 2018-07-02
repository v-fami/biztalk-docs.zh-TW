---
title: MSH 覆寫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, MSH segments
- routing, messages
- subscriptions
- messages, routing
- routing, MSH segments
- send ports, subscriptions
- MSH segments
- send ports, multiple ports
ms.assetid: 4f5700bc-c8f4-40c9-9c9c-2220fa2627ba
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73508f573e4584ae841779301c426fa06bb78144
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974247"
---
# <a name="msh-override"></a><span data-ttu-id="27721-102">MSH 覆寫</span><span class="sxs-lookup"><span data-stu-id="27721-102">MSH Override</span></span>
<span data-ttu-id="27721-103">Microsoft BizTalk Accelerator for HL7 之前 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 將輸出 HL7 訊息路由至傳送埠，您可能想要取代 MSH 區段中的某些值。</span><span class="sxs-lookup"><span data-stu-id="27721-103">Before Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) routes an outbound HL7 message to a send port, you may want to replace certain values within the MSH segment.</span></span> <span data-ttu-id="27721-104">若要這樣做，當訊息的訂用帳戶包含多個傳送埠，以及每個傳送埠應該會看到不同的值，在接收應用程式 欄位。</span><span class="sxs-lookup"><span data-stu-id="27721-104">You may want to do this when the subscription for a message contains multiple send ports, and each send port should see a different value in the receiving-application field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27721-105">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27721-105">See Also</span></span>  
 <span data-ttu-id="27721-106">[MSH 欄位覆寫](../../adapters-and-accelerators/accelerator-hl7/msh-field-overrides.md) </span><span class="sxs-lookup"><span data-stu-id="27721-106">[MSH Field Overrides](../../adapters-and-accelerators/accelerator-hl7/msh-field-overrides.md) </span></span>  
 [<span data-ttu-id="27721-107">通知</span><span class="sxs-lookup"><span data-stu-id="27721-107">Acknowledgments</span></span>](../../adapters-and-accelerators/accelerator-hl7/acknowledgments.md)