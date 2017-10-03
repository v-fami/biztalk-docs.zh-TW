---
title: "執行階段中，訊息修復、 FIN 回應和傳訊 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, about architecture
- architecture
- BizTalk Accelerator for SWIFT, architecture
ms.assetid: c7f34517-6663-44a6-b6ea-6d55fdb08caf
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 539d6f6d7a2b84262750f8b3c6da3c16a67f0de9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="runtime-message-repair-fin-response-and-messaging"></a><span data-ttu-id="cf25f-102">執行階段、 訊息修復、 FIN 回應和傳訊</span><span class="sxs-lookup"><span data-stu-id="cf25f-102">Runtime, message repair, FIN response, and messaging</span></span>

## <a name="overview"></a><span data-ttu-id="cf25f-103">概觀</span><span class="sxs-lookup"><span data-stu-id="cf25f-103">Overview</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="cf25f-104">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]讓客戶和夥伴的財務業界的特定傳訊和連線功能，可協助加速實作[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]為中介軟體的財務組織。</span><span class="sxs-lookup"><span data-stu-id="cf25f-104"> [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] provides customers and partners with financial-industry-specific messaging and connectivity functionality, which helps accelerate implementation of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] as middleware for financial organizations.</span></span>  
  
 <span data-ttu-id="cf25f-105">利用開啟標準基礎的工具和執行階段設備的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]實作類似 SWIFT 的訊息格式的支援，A4SWIFT 減少屏障採用更新 SWIFT 標準採用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]做為一般用途中介軟體整合平台。</span><span class="sxs-lookup"><span data-stu-id="cf25f-105">By leveraging the open-standards based tools and runtime facilities of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] to implement support for message formats like SWIFT, A4SWIFT reduces the barrier to adoption of updated SWIFT standards by employing [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] as a general-purpose middleware integration platform.</span></span>  
  
 <span data-ttu-id="cf25f-106">A4SWIFT 和[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]減少時間上市，也減少傳遞企業等級伺服器應用程式裝載和整合，以及工作流程的整體維護和支援成本降低總擁有成本 (TCO)財務服務產業中的實作。</span><span class="sxs-lookup"><span data-stu-id="cf25f-106">A4SWIFT and [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] reduce the time-to-market while also decreasing the total cost of ownership (TCO) by reducing the overall maintenance and support cost of delivering enterprise class servers for application hosting and integration as well as workflow implementation in the financial services industry.</span></span>  
  
 <span data-ttu-id="cf25f-107">您可以針對分類 A4SWIFT 功能與通訊的 SWIFT 和 SWIFT 的連線能力。</span><span class="sxs-lookup"><span data-stu-id="cf25f-107">You can broadly categorize A4SWIFT functionality as SWIFT messaging and SWIFT connectivity.</span></span> <span data-ttu-id="cf25f-108">完整 A4SWIFT 訊息包含 SWIFT 訊息剖析和驗證 （包括輸入/輸出批次處理）、 訊息項目，以及修復 (包括整合[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]與前端使用者工具)，和其他特定業務 (LOB) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="cf25f-108">Full A4SWIFT messaging encompasses SWIFT message parsing and validation (including inbound/outbound batching), message entry and repair (including integration with [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)][!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] as the front-end user tool), and other line-of-business (LOB) applications.</span></span>  
  
 [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]<span data-ttu-id="cf25f-109">提供 XSD 結構描述和完整的驗證，包括網路規則，所有 358 的財務 (FIN) 訊息。</span><span class="sxs-lookup"><span data-stu-id="cf25f-109"> provides XSD schemas and full validation, including network rules, for all 358 of the financial (FIN) messages.</span></span> <span data-ttu-id="cf25f-110">它也提供解除批次處理即將輸入。</span><span class="sxs-lookup"><span data-stu-id="cf25f-110">It also provides inbound debatching.</span></span>  

## <a name="next-steps"></a><span data-ttu-id="cf25f-111">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="cf25f-111">Next steps</span></span>  
 <span data-ttu-id="cf25f-112">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="cf25f-112">This section contains:</span></span>  
  
-   [<span data-ttu-id="cf25f-113">元件</span><span class="sxs-lookup"><span data-stu-id="cf25f-113">Components</span></span>](components.md)  
  
-   [<span data-ttu-id="cf25f-114">BizTalk Accelerator for SWIFT 的執行階段</span><span class="sxs-lookup"><span data-stu-id="cf25f-114">BizTalk Accelerator for SWIFT Runtime</span></span>](biztalk-accelerator-for-swift-runtime.md)  
  
-   [<span data-ttu-id="cf25f-115">Message Repair 和 New Submission</span><span class="sxs-lookup"><span data-stu-id="cf25f-115">Message Repair and New Submission</span></span>](message-repair-and-new-submission.md)  
  
-   [<span data-ttu-id="cf25f-116">FIN 回應對帳</span><span class="sxs-lookup"><span data-stu-id="cf25f-116">FIN Response Reconciliation</span></span>](fin-response-reconciliation.md)  
  
-   [<span data-ttu-id="cf25f-117">SWIFT 訊息</span><span class="sxs-lookup"><span data-stu-id="cf25f-117">SWIFT Messages</span></span>](swift-messages.md)

- [<span data-ttu-id="cf25f-118">A4SWIFT_ * 升級屬性</span><span class="sxs-lookup"><span data-stu-id="cf25f-118">A4SWIFT_* Promoted Properties</span></span>](a4swift-promoted-properties.md)