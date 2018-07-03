---
title: FRR NAK 處理常式範例 |Microsoft Docs
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
ms.openlocfilehash: 35574f47af789054bd8192da93ce5cffa1b3984b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996929"
---
# <a name="frr-nak-handler-sample"></a><span data-ttu-id="385ef-102">FRR NAK 處理常式範例</span><span class="sxs-lookup"><span data-stu-id="385ef-102">FRR NAK Handler Sample</span></span>
<span data-ttu-id="385ef-103">FRR NAK 處理常式範例會示範如何使用 SWIFT 回應建立自訂的處理常式，來處理 FIN 回應對帳 (FRR) 有相互關聯的訊息。</span><span class="sxs-lookup"><span data-stu-id="385ef-103">The FRR NAK Handler sample demonstrates how to create a custom handler to process messages that FIN Response Reconciliation (FRR) has correlated with SWIFT responses.</span></span> <span data-ttu-id="385ef-104">這個自訂的處理常式處理 MTS21_FIN_ACKNAK 負值通知訊息，這會指出，SWIFT 未成功接收訊息從 A4SWIFT 的訊息的 FRR 有相互關聯。</span><span class="sxs-lookup"><span data-stu-id="385ef-104">This custom handler processes messages that FRR has correlated with a MTS21_FIN_ACKNAK negative-acknowledgment message, which indicates that SWIFT did not successfully receive the message from A4SWIFT.</span></span> <span data-ttu-id="385ef-105">自訂處理常式將錯誤物件加入至訊息中，兩部分訊息，讓訊息，並將升級的屬性，使訊息修復協調流程收取訊息。</span><span class="sxs-lookup"><span data-stu-id="385ef-105">The custom handler adds an error object to the message, making the message a two-part message, and promotes the properties that cause the message-repair orchestration to pick up the message.</span></span> <span data-ttu-id="385ef-106">如此一來，repairer 可以修正訊息，然後重新傳送至 SWIFT Alliance 存取 (SAA)。</span><span class="sxs-lookup"><span data-stu-id="385ef-106">As a result, a repairer can fix the message and resend it to SWIFT Alliance Access (SAA).</span></span>  
  
 <span data-ttu-id="385ef-107">**範例元件**</span><span class="sxs-lookup"><span data-stu-id="385ef-107">**Sample Components**</span></span>  
  
 <span data-ttu-id="385ef-108">FRR NAK 處理常式範例包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="385ef-108">The FRR NAK Handler sample includes the following components:</span></span>  
  
- <span data-ttu-id="385ef-109">**RepairSWIFTRejectedMessage.odx。**</span><span class="sxs-lookup"><span data-stu-id="385ef-109">**RepairSWIFTRejectedMessage.odx.**</span></span> <span data-ttu-id="385ef-110">此協調流程會處理 SWIFT 無法成功接收，將其路由到訊息修復協調流程，因此 repairer 可以修正並重新傳送訊息的訊息的自訂處理常式。</span><span class="sxs-lookup"><span data-stu-id="385ef-110">This orchestration is the custom handler that processes a message that SWIFT could not successfully receive, routing it to the message-repair orchestration so a repairer can fix and resend the message.</span></span>  
  
- <span data-ttu-id="385ef-111">**RepairSWIFTRejectedMessage.btproj。**</span><span class="sxs-lookup"><span data-stu-id="385ef-111">**RepairSWIFTRejectedMessage.btproj.**</span></span> <span data-ttu-id="385ef-112">此專案包含 RepairSWIFTRejectedMessage.odx 和專案所需的參考，來建置和部署。</span><span class="sxs-lookup"><span data-stu-id="385ef-112">This project includes RepairSWIFTRejectedMessage.odx and the references required for the project to build and deploy.</span></span>  
  
- <span data-ttu-id="385ef-113">**RepairSWIFTRejectedMessage.sln。**</span><span class="sxs-lookup"><span data-stu-id="385ef-113">**RepairSWIFTRejectedMessage.sln.**</span></span> <span data-ttu-id="385ef-114">此解決方案包括 RepairSWIFTRejectedMessage.btproj 專案。</span><span class="sxs-lookup"><span data-stu-id="385ef-114">This solution includes the RepairSWIFTRejectedMessage.btproj project.</span></span>  
  
  <span data-ttu-id="385ef-115">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="385ef-115">This section contains:</span></span>  
  
- [<span data-ttu-id="385ef-116">實作 FRR NAK 處理常式範例</span><span class="sxs-lookup"><span data-stu-id="385ef-116">Implementing the FRR NAK Handler Sample</span></span>](../../adapters-and-accelerators/accelerator-swift/implementing-the-frr-nak-handler-sample.md)  
  
- [<span data-ttu-id="385ef-117">FRR NAK 處理常式範例運作方式</span><span class="sxs-lookup"><span data-stu-id="385ef-117">How the FRR NAK Handler Sample Works</span></span>](../../adapters-and-accelerators/accelerator-swift/how-the-frr-nak-handler-sample-works.md)  
  
