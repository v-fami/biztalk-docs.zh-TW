---
title: FRR SWIFT 的訊息的傳送埠 |Microsoft 文件
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
ms.openlocfilehash: 6a442b45f57009b839b4e184ef9662b253ba32b2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22209358"
---
# <a name="frr-send-port-for-messages-to-swift"></a><span data-ttu-id="6a3bd-102">FRR SWIFT 的訊息的傳送埠</span><span class="sxs-lookup"><span data-stu-id="6a3bd-102">FRR Send Port for Messages to SWIFT</span></span>
<span data-ttu-id="6a3bd-103">若要啟用 FIN 回應對帳 (FRR)，您必須設定會傳送訊息至 SAA 透過 BizTalk Adapter for MQSeries FRR 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="6a3bd-103">To enable FIN response reconciliation (FRR), you must set up an FRR send port that sends a message to SAA through the BizTalk Adapter for MQSeries.</span></span> <span data-ttu-id="6a3bd-104">此傳送連接埠的路由訊息自訂 FRR 通過傳送管線元件，您必須建立具有下列管線元件：</span><span class="sxs-lookup"><span data-stu-id="6a3bd-104">This send port routes a message through a custom FRR send pipeline component that you must create with the following pipeline components:</span></span>  
  
-   <span data-ttu-id="6a3bd-105">「 組合 」 階段中的 SWIFT 組合器</span><span class="sxs-lookup"><span data-stu-id="6a3bd-105">The SWIFT assembler in the Assemble stage</span></span>  
  
-   <span data-ttu-id="6a3bd-106">SWIFTAsmFrrMQSeriesHelper 管線元件中的編碼階段</span><span class="sxs-lookup"><span data-stu-id="6a3bd-106">The SWIFTAsmFrrMQSeriesHelper pipeline component in the Encode stage</span></span>  
  
 <span data-ttu-id="6a3bd-107">SWIFTAsmFrrMQSeriesHelper 管線元件將 MQMD_MsgID 屬性設定外寄訊息為 FRRCorrelationToken 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="6a3bd-107">The SWIFTAsmFrrMQSeriesHelper pipeline component sets the MQMD_MsgID property of the outgoing message to the value of the FRRCorrelationToken property.</span></span> <span data-ttu-id="6a3bd-108">它也會指派，並將升級開頭"MQ 「 管線設計階段設定的值與任何其他必要的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="6a3bd-108">It also assigns and promotes any other required context properties starting with "MQ" with values set at the pipeline design time.</span></span> <span data-ttu-id="6a3bd-109">傳送管線包含 MQSeries 作為可設定的屬性定義每個屬性。</span><span class="sxs-lookup"><span data-stu-id="6a3bd-109">The send pipeline includes each property defined for MQSeries as a configurable property.</span></span> <span data-ttu-id="6a3bd-110">每個值預設為 「 無法使用 」。</span><span class="sxs-lookup"><span data-stu-id="6a3bd-110">Each value defaults to "Not Used".</span></span>  
  
 <span data-ttu-id="6a3bd-111">傳送埠處理的訊息[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed = = False 和[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_SWIFTBOUND = = True。</span><span class="sxs-lookup"><span data-stu-id="6a3bd-111">The send port handles messages that have [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed==False and [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_SWIFTBOUND==True.</span></span> <span data-ttu-id="6a3bd-112">傳輸機制為 BizTalk Adapter for MQSeries。</span><span class="sxs-lookup"><span data-stu-id="6a3bd-112">The transport mechanism is the BizTalk Adapter for MQSeries.</span></span> <span data-ttu-id="6a3bd-113">如需有關傳輸屬性，例如片段大小資訊，請參閱 MQSeries 文件。</span><span class="sxs-lookup"><span data-stu-id="6a3bd-113">For information about the transport properties, such as the fragmentation size, see the MQSeries documentation.</span></span>