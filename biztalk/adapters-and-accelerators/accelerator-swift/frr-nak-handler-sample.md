---
title: FRR NAK 處理常式範例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples, NAKs
- examples, FRR
- NAKs
- acknowledgements
- FRR, examples
- examples, FRR NAK handler
ms.assetid: be992507-ba8c-461f-a563-f1d7b2ab221d
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a3881b8bcf4b62af7653ef6214b4fccdf8402d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22207406"
---
# <a name="frr-nak-handler-sample"></a><span data-ttu-id="32cbb-102">FRR NAK 處理常式範例</span><span class="sxs-lookup"><span data-stu-id="32cbb-102">FRR NAK Handler Sample</span></span>
<span data-ttu-id="32cbb-103">FRR NAK 處理常式範例示範如何建立 SWIFT 回應 FIN 回應對帳 (FRR) 有相互關聯的處理訊息的自訂處理常式。</span><span class="sxs-lookup"><span data-stu-id="32cbb-103">The FRR NAK Handler sample demonstrates how to create a custom handler to process messages that FIN Response Reconciliation (FRR) has correlated with SWIFT responses.</span></span> <span data-ttu-id="32cbb-104">這個自訂的處理常式處理 MTS21_FIN_ACKNAK 負值通知訊息，這表示，SWIFT 未順利收到訊息從 A4SWIFT FRR 有相互關聯的訊息。</span><span class="sxs-lookup"><span data-stu-id="32cbb-104">This custom handler processes messages that FRR has correlated with a MTS21_FIN_ACKNAK negative-acknowledgment message, which indicates that SWIFT did not successfully receive the message from A4SWIFT.</span></span> <span data-ttu-id="32cbb-105">自訂處理常式將錯誤物件加入至訊息、 兩段式訊息時，將訊息，並將升級的屬性，使訊息修復協調流程收取訊息。</span><span class="sxs-lookup"><span data-stu-id="32cbb-105">The custom handler adds an error object to the message, making the message a two-part message, and promotes the properties that cause the message-repair orchestration to pick up the message.</span></span> <span data-ttu-id="32cbb-106">如此一來，repairer 可以修正訊息，然後重新傳送至 SWIFT 聯盟存取 (SAA)。</span><span class="sxs-lookup"><span data-stu-id="32cbb-106">As a result, a repairer can fix the message and resend it to SWIFT Alliance Access (SAA).</span></span>  
  
 <span data-ttu-id="32cbb-107">**範例元件**</span><span class="sxs-lookup"><span data-stu-id="32cbb-107">**Sample Components**</span></span>  
  
 <span data-ttu-id="32cbb-108">FRR NAK 處理常式範例包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="32cbb-108">The FRR NAK Handler sample includes the following components:</span></span>  
  
-   <span data-ttu-id="32cbb-109">**RepairSWIFTRejectedMessage.odx。**</span><span class="sxs-lookup"><span data-stu-id="32cbb-109">**RepairSWIFTRejectedMessage.odx.**</span></span> <span data-ttu-id="32cbb-110">此協調流程會處理 SWIFT 無法成功接收，路由到訊息修復協調流程，讓 repairer 可以修正並重新傳送訊息的訊息的自訂處理常式。</span><span class="sxs-lookup"><span data-stu-id="32cbb-110">This orchestration is the custom handler that processes a message that SWIFT could not successfully receive, routing it to the message-repair orchestration so a repairer can fix and resend the message.</span></span>  
  
-   <span data-ttu-id="32cbb-111">**RepairSWIFTRejectedMessage.btproj。**</span><span class="sxs-lookup"><span data-stu-id="32cbb-111">**RepairSWIFTRejectedMessage.btproj.**</span></span> <span data-ttu-id="32cbb-112">此專案包含 RepairSWIFTRejectedMessage.odx 和參考專案所需建置和部署。</span><span class="sxs-lookup"><span data-stu-id="32cbb-112">This project includes RepairSWIFTRejectedMessage.odx and the references required for the project to build and deploy.</span></span>  
  
-   <span data-ttu-id="32cbb-113">**RepairSWIFTRejectedMessage.sln。**</span><span class="sxs-lookup"><span data-stu-id="32cbb-113">**RepairSWIFTRejectedMessage.sln.**</span></span> <span data-ttu-id="32cbb-114">此解決方案包括 RepairSWIFTRejectedMessage.btproj 專案。</span><span class="sxs-lookup"><span data-stu-id="32cbb-114">This solution includes the RepairSWIFTRejectedMessage.btproj project.</span></span>  
  
 <span data-ttu-id="32cbb-115">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="32cbb-115">This section contains:</span></span>  
  
-   [<span data-ttu-id="32cbb-116">實作 FRR NAK 處理常式範例</span><span class="sxs-lookup"><span data-stu-id="32cbb-116">Implementing the FRR NAK Handler Sample</span></span>](../../adapters-and-accelerators/accelerator-swift/implementing-the-frr-nak-handler-sample.md)  
  
-   [<span data-ttu-id="32cbb-117">FRR NAK 處理常式範例的運作方式</span><span class="sxs-lookup"><span data-stu-id="32cbb-117">How the FRR NAK Handler Sample Works</span></span>](../../adapters-and-accelerators/accelerator-swift/how-the-frr-nak-handler-sample-works.md)  
  
