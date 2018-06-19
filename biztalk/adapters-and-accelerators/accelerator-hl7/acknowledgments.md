---
title: 通知 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, acknowledgements
- parties, acknowledgements
- acknowledgements, about acknowledgements
- acknowledgements, messages
- acknowledgements, parties
ms.assetid: d25352a4-bae9-4de9-a504-2339bea25c4a
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c519ec4649ee1fbcfbc51edb7e3e8fe6ba6b5871
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204342"
---
# <a name="acknowledgments"></a><span data-ttu-id="fa7c7-102">致謝</span><span class="sxs-lookup"><span data-stu-id="fa7c7-102">Acknowledgments</span></span>
<span data-ttu-id="fa7c7-103">您在合作對象層級使用設定 HL7 通知[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 組態總管。</span><span class="sxs-lookup"><span data-stu-id="fa7c7-103">You configure HL7 acknowledgments at the party level using [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) Configuration Explorer.</span></span> <span data-ttu-id="fa7c7-104">套用至傳送到接收位置 （可能是 MLLP 配接器） 以及 HL7 HL7 訊息的合作對象的通知 2.X 接收管線。</span><span class="sxs-lookup"><span data-stu-id="fa7c7-104">Acknowledgments apply to parties that are sending HL7 messages through a receive location (possibly the MLLP adapter) and the HL7 2.X receive pipeline.</span></span> <span data-ttu-id="fa7c7-105">當訊息完成剖析和驗證，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]可以建立通知訊息，其中包含驗證程序的結果 （成功或錯誤）。</span><span class="sxs-lookup"><span data-stu-id="fa7c7-105">When a message completes parsing and validation, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] can create an acknowledgment message that contains the result (success or error) of the validation process.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="fa7c7-106">可以在其中一種方式傳回通知訊息。</span><span class="sxs-lookup"><span data-stu-id="fa7c7-106"> can return acknowledgment messages in one of two ways.</span></span> <span data-ttu-id="fa7c7-107">如果原始的傳送合作對象送出原始訊息透過雙向接收埠組態[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會透過該原始的連接埠位置認可訊息傳回。</span><span class="sxs-lookup"><span data-stu-id="fa7c7-107">If the original sending party submitted the original message through a two-way receive port configuration, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] returns the acknowledgment message through that original port location.</span></span> <span data-ttu-id="fa7c7-108">如果原始的傳送埠送出原始訊息透過單向接收埠，則[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]將通知訊息提交至 MessageBox 資料庫，並將它使用訂用帳戶模型路由傳送。[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa7c7-108">If the original sending port submitted the original message through a one-way receive port, then [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] submits the acknowledgment message into the MessageBox database and routes it using the subscription model.[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]</span></span> <span data-ttu-id="fa7c7-109">執行合作對象關聯的接收訊息處理會自動根據 HL7 訊息 (MSH 3.1) 的傳送端應用程式欄位內的值。</span><span class="sxs-lookup"><span data-stu-id="fa7c7-109">performs party association for receive message processing automatically based on the value within the sending application field of the HL7 message (MSH 3.1).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa7c7-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa7c7-110">See Also</span></span>  
 [<span data-ttu-id="fa7c7-111">訊息流程</span><span class="sxs-lookup"><span data-stu-id="fa7c7-111">Message Flow</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-flow.md)