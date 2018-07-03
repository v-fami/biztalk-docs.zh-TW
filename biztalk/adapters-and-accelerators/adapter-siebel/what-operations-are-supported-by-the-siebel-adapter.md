---
title: Siebel 配接器支援哪些作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- operations, performing by using the adapter
ms.assetid: 800cf44b-357f-4850-8878-f49ceb549adf
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3f080cedb74210d02806681b6c9e20656d3d09e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004775"
---
# <a name="what-operations-are-supported-by-the-siebel-adapter"></a><span data-ttu-id="3f403-102">Siebel 配接器支援哪些作業</span><span class="sxs-lookup"><span data-stu-id="3f403-102">What operations are supported by the Siebel adapter</span></span>
<span data-ttu-id="3f403-103">配接器用戶端可以透過下列方式執行 Siebel 系統上的作業：</span><span class="sxs-lookup"><span data-stu-id="3f403-103">Adapter clients can perform operations on the Siebel system by either:</span></span>  
  
- <span data-ttu-id="3f403-104">建立 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="3f403-104">Creating BizTalk projects.</span></span>  
  
- <span data-ttu-id="3f403-105">使用 WCF 通道模型。</span><span class="sxs-lookup"><span data-stu-id="3f403-105">Using the WCF channel model.</span></span>  
  
- <span data-ttu-id="3f403-106">使用 WCF 服務模型。</span><span class="sxs-lookup"><span data-stu-id="3f403-106">Using the WCF service model.</span></span>  
  
  <span data-ttu-id="3f403-107">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]會公開應用程式，可以在其上叫用並，它可以依次叫用應用程式上的作業。</span><span class="sxs-lookup"><span data-stu-id="3f403-107">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] exposes operations that applications can invoke on it and that it can, in turn, invoke on applications.</span></span> <span data-ttu-id="3f403-108">這些作業會叫用透過通道傳送 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="3f403-108">These operations are invoked by sending SOAP messages over a channel.</span></span> <span data-ttu-id="3f403-109">如果需要回應，它會傳回 SOAP 訊息中透過相同的通道。</span><span class="sxs-lookup"><span data-stu-id="3f403-109">If a response is required, it is returned in a SOAP message over the same channel.</span></span> <span data-ttu-id="3f403-110">訊息結構和每個作業相關聯的 SOAP 動作的相關資訊，請參閱[訊息和訊息結構描述，BizTalk adapter for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/messages-and-message-schemas-for-siebel-adapter-in-biztalk.md)。</span><span class="sxs-lookup"><span data-stu-id="3f403-110">For information about the message structure and the SOAP action associated with each operation, see [Messages and Message Schemas for BizTalk Adapter for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/messages-and-message-schemas-for-siebel-adapter-in-biztalk.md).</span></span>  
  
  <span data-ttu-id="3f403-111">本節提供有關 Siebel 系統使用支援的作業資訊[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3f403-111">This section provides information about the operations supported on the Siebel system using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f403-112">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不支援從 Siebel 系統接收傳入的呼叫。</span><span class="sxs-lookup"><span data-stu-id="3f403-112">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] does not support receiving inbound calls from a Siebel system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3f403-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="3f403-113">In This Section</span></span>  
  
-   [<span data-ttu-id="3f403-114">在 Siebel 商務元件上的作業</span><span class="sxs-lookup"><span data-stu-id="3f403-114">Operations on Business Components in Siebel</span></span>](../../adapters-and-accelerators/adapter-siebel/operations-on-business-components-in-siebel.md)  
  
-   [<span data-ttu-id="3f403-115">在 Siebel 商務服務的相關作業</span><span class="sxs-lookup"><span data-stu-id="3f403-115">Operations on Business Services in Siebel</span></span>](../../adapters-and-accelerators/adapter-siebel/operations-on-business-services-in-siebel.md)  
  
## <a name="see-also"></a><span data-ttu-id="3f403-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f403-116">See Also</span></span>  
 [<span data-ttu-id="3f403-117">BizTalk Adapter for Siebel eBusiness Applications 概觀</span><span class="sxs-lookup"><span data-stu-id="3f403-117">Overview of BizTalk Adapter for Siebel eBusiness Applications</span></span>](../../adapters-and-accelerators/adapter-siebel/overview-of-biztalk-adapter-for-siebel-ebusiness-applications.md)