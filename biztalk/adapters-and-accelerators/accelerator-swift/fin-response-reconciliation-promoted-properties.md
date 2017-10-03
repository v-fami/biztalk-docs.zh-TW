---
title: "FIN 回應對帳升級屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- promoted properties, FIN Response Reconciliation
- FIN Response Reconciliation, promoted properties
ms.assetid: 1a638e9e-61eb-482c-8856-b1aea36c449c
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 14a3e3a004dcb9e58abde08345352c02f0914801
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="fin-response-reconciliation-promoted-properties"></a><span data-ttu-id="62ed8-102">FIN 回應對帳升級屬性</span><span class="sxs-lookup"><span data-stu-id="62ed8-102">FIN Response Reconciliation Promoted Properties</span></span>
<span data-ttu-id="62ed8-103">[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] FIN 回應對帳功能包括下列的升級的屬性。</span><span class="sxs-lookup"><span data-stu-id="62ed8-103">The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] FIN Response Reconciliation feature includes the following promoted properties.</span></span>  
  
|<span data-ttu-id="62ed8-104">升級的名稱</span><span class="sxs-lookup"><span data-stu-id="62ed8-104">Promoted name</span></span>|<span data-ttu-id="62ed8-105">Description</span><span class="sxs-lookup"><span data-stu-id="62ed8-105">Description</span></span>|<span data-ttu-id="62ed8-106">資料類型</span><span class="sxs-lookup"><span data-stu-id="62ed8-106">Data type</span></span>|<span data-ttu-id="62ed8-107">數值範圍</span><span class="sxs-lookup"><span data-stu-id="62ed8-107">Value range</span></span>|<span data-ttu-id="62ed8-108">使用範例</span><span class="sxs-lookup"><span data-stu-id="62ed8-108">Usage example</span></span>|  
|-------------------|-----------------|---------------|-----------------|-------------------|  
|<span data-ttu-id="62ed8-109">**A4SWIFT_FRRFailed**</span><span class="sxs-lookup"><span data-stu-id="62ed8-109">**A4SWIFT_FRRFailed**</span></span>|<span data-ttu-id="62ed8-110">送出的主要訊息時，這個屬性會升級在負值的案例。</span><span class="sxs-lookup"><span data-stu-id="62ed8-110">This property is promoted in a negative scenario when sending out the main message.</span></span>|<span data-ttu-id="62ed8-111">布林</span><span class="sxs-lookup"><span data-stu-id="62ed8-111">Boolean</span></span>|<span data-ttu-id="62ed8-112">True</span><span class="sxs-lookup"><span data-stu-id="62ed8-112">True</span></span><br /><br /> <span data-ttu-id="62ed8-113">False</span><span class="sxs-lookup"><span data-stu-id="62ed8-113">False</span></span>|<span data-ttu-id="62ed8-114">用於篩選運算式中 FRR 傳送埠的失敗的訊息傳送到自訂處理常式。</span><span class="sxs-lookup"><span data-stu-id="62ed8-114">Used in the filter expression of an FRR send port to send a failed message to a custom handler.</span></span>|  
|<span data-ttu-id="62ed8-115">**A4SWIFT_FrrFailedReason**</span><span class="sxs-lookup"><span data-stu-id="62ed8-115">**A4SWIFT_FrrFailedReason**</span></span>|<span data-ttu-id="62ed8-116">表示原始訊息已尚未成功處理由 SAA/SWIFT。</span><span class="sxs-lookup"><span data-stu-id="62ed8-116">Indicates that the original message was not successfully processed by SAA/SWIFT.</span></span>|<span data-ttu-id="62ed8-117">字串</span><span class="sxs-lookup"><span data-stu-id="62ed8-117">String</span></span>|<span data-ttu-id="62ed8-118">-   \<NAKErrorCode ></span><span class="sxs-lookup"><span data-stu-id="62ed8-118">-   \<NAKErrorCode></span></span><br /><span data-ttu-id="62ed8-119">-已逾時</span><span class="sxs-lookup"><span data-stu-id="62ed8-119">-   TimedOut</span></span><br /><span data-ttu-id="62ed8-120">-TransportError</span><span class="sxs-lookup"><span data-stu-id="62ed8-120">-   TransportError</span></span><br /><span data-ttu-id="62ed8-121">-Delayed_NAK</span><span class="sxs-lookup"><span data-stu-id="62ed8-121">-   Delayed_NAK</span></span><br /><span data-ttu-id="62ed8-122">-AbortReceived</span><span class="sxs-lookup"><span data-stu-id="62ed8-122">-   AbortReceived</span></span>|<span data-ttu-id="62ed8-123">用於篩選運算式中 FRR 傳送埠的失敗的訊息傳送到自訂處理常式。</span><span class="sxs-lookup"><span data-stu-id="62ed8-123">Used in the filter expression of an FRR send port to send a failed message to a custom handler.</span></span>|  
|<span data-ttu-id="62ed8-124">**A4SWIFT_FRRCorrelationToken**</span><span class="sxs-lookup"><span data-stu-id="62ed8-124">**A4SWIFT_FRRCorrelationToken**</span></span>|<span data-ttu-id="62ed8-125">指出輸出 MT 的唯一相互關聯 token*xxx*訊息。</span><span class="sxs-lookup"><span data-stu-id="62ed8-125">Indicates the unique correlation token of the outbound MT*xxx* message.</span></span>|<span data-ttu-id="62ed8-126">字串</span><span class="sxs-lookup"><span data-stu-id="62ed8-126">String</span></span>|-|<span data-ttu-id="62ed8-127">FRR 比較這個屬性，以**MQMD_CorrelID** FIN 回應的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="62ed8-127">FRR compares this property to the **MQMD_CorrelID** context property of the FIN response.</span></span>|  
|<span data-ttu-id="62ed8-128">**A4SWIFT_SendingServiceType**</span><span class="sxs-lookup"><span data-stu-id="62ed8-128">**A4SWIFT_SendingServiceType**</span></span>|<span data-ttu-id="62ed8-129">指出 FRR 服務傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="62ed8-129">Indicates the FRR service that sends the message.</span></span>|<span data-ttu-id="62ed8-130">字串</span><span class="sxs-lookup"><span data-stu-id="62ed8-130">String</span></span>|<span data-ttu-id="62ed8-131">A4SWIFT_FrrService</span><span class="sxs-lookup"><span data-stu-id="62ed8-131">A4SWIFT_FrrService</span></span>|<span data-ttu-id="62ed8-132">升級時**A4SWIFT_FRRFailed**設為 True。</span><span class="sxs-lookup"><span data-stu-id="62ed8-132">Promoted when **A4SWIFT_FRRFailed** is set to True.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62ed8-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62ed8-133">See Also</span></span>  
 <span data-ttu-id="62ed8-134">[A4SWIFT_ * 升級屬性](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md) </span><span class="sxs-lookup"><span data-stu-id="62ed8-134">[A4SWIFT_* Promoted Properties](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md) </span></span>  
 [<span data-ttu-id="62ed8-135">Message Repair 和 New Submission 升級屬性</span><span class="sxs-lookup"><span data-stu-id="62ed8-135">Message Repair and New Submission Promoted Properties</span></span>](../../adapters-and-accelerators/accelerator-swift/message-repair-and-new-submission-promoted-properties.md)