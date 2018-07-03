---
title: 訊息至 SWIFT 的 FRR 傳送埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FRR, send ports
- send ports, FRR
ms.assetid: 905c69a3-dff3-4a60-803d-dd617ffb6896
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a1732e5e41cd60f6c98f435197e2e9c6284e4dd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991735"
---
# <a name="frr-send-port-for-messages-to-swift"></a><span data-ttu-id="d6ad2-102">訊息至 SWIFT 的 FRR 傳送埠</span><span class="sxs-lookup"><span data-stu-id="d6ad2-102">FRR Send Port for Messages to SWIFT</span></span>
<span data-ttu-id="d6ad2-103">若要啟用 FIN 回應對帳 (FRR)，您必須設定將 SAA 透過 BizTalk Adapter for MQSeries 訊息的 FRR 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="d6ad2-103">To enable FIN response reconciliation (FRR), you must set up an FRR send port that sends a message to SAA through the BizTalk Adapter for MQSeries.</span></span> <span data-ttu-id="d6ad2-104">此傳送連接埠路由訊息，以透過自訂的 FRR 傳送管線元件，您必須建立下列管線元件：</span><span class="sxs-lookup"><span data-stu-id="d6ad2-104">This send port routes a message through a custom FRR send pipeline component that you must create with the following pipeline components:</span></span>  
  
- <span data-ttu-id="d6ad2-105">中 「 組合 」 階段的 SWIFT 組合器</span><span class="sxs-lookup"><span data-stu-id="d6ad2-105">The SWIFT assembler in the Assemble stage</span></span>  
  
- <span data-ttu-id="d6ad2-106">SWIFTAsmFrrMQSeriesHelper 管線元件中的編碼階段</span><span class="sxs-lookup"><span data-stu-id="d6ad2-106">The SWIFTAsmFrrMQSeriesHelper pipeline component in the Encode stage</span></span>  
  
  <span data-ttu-id="d6ad2-107">SWIFTAsmFrrMQSeriesHelper 管線元件會將外寄訊息的 MQMD_MsgID 屬性設定為 FRRCorrelationToken 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="d6ad2-107">The SWIFTAsmFrrMQSeriesHelper pipeline component sets the MQMD_MsgID property of the outgoing message to the value of the FRRCorrelationToken property.</span></span> <span data-ttu-id="d6ad2-108">它也會指派，並會在管線設計階段設定的值開頭為"MQ"的任何其他所需的內容屬性升級。</span><span class="sxs-lookup"><span data-stu-id="d6ad2-108">It also assigns and promotes any other required context properties starting with "MQ" with values set at the pipeline design time.</span></span> <span data-ttu-id="d6ad2-109">傳送管線包含針對 MQSeries 作為可設定的屬性定義每個屬性。</span><span class="sxs-lookup"><span data-stu-id="d6ad2-109">The send pipeline includes each property defined for MQSeries as a configurable property.</span></span> <span data-ttu-id="d6ad2-110">每個值預設為 「 使用 」。</span><span class="sxs-lookup"><span data-stu-id="d6ad2-110">Each value defaults to "Not Used".</span></span>  
  
  <span data-ttu-id="d6ad2-111">傳送埠處理之訊息的[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed = = False 和[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_SWIFTBOUND = = True。</span><span class="sxs-lookup"><span data-stu-id="d6ad2-111">The send port handles messages that have [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed==False and [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_SWIFTBOUND==True.</span></span> <span data-ttu-id="d6ad2-112">傳輸機制為 BizTalk Adapter for MQSeries。</span><span class="sxs-lookup"><span data-stu-id="d6ad2-112">The transport mechanism is the BizTalk Adapter for MQSeries.</span></span> <span data-ttu-id="d6ad2-113">如需詳細資訊的傳輸屬性 的分散大小，例如 MQSeries 文件。</span><span class="sxs-lookup"><span data-stu-id="d6ad2-113">For information about the transport properties, such as the fragmentation size, see the MQSeries documentation.</span></span>