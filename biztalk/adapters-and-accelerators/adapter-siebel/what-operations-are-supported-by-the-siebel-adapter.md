---
title: "Siebel 配接器支援哪些作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: operations, performing by using the adapter
ms.assetid: 800cf44b-357f-4850-8878-f49ceb549adf
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 40bfb247ff0f3af2abeec584c5fd079f392cd18e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-operations-are-supported-by-the-siebel-adapter"></a><span data-ttu-id="93a0a-102">Siebel 配接器支援哪些作業</span><span class="sxs-lookup"><span data-stu-id="93a0a-102">What operations are supported by the Siebel adapter</span></span>
<span data-ttu-id="93a0a-103">配接器用戶端可以透過執行 Siebel 系統上的作業：</span><span class="sxs-lookup"><span data-stu-id="93a0a-103">Adapter clients can perform operations on the Siebel system by either:</span></span>  
  
-   <span data-ttu-id="93a0a-104">建立 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="93a0a-104">Creating BizTalk projects.</span></span>  
  
-   <span data-ttu-id="93a0a-105">使用 WCF 通道模型。</span><span class="sxs-lookup"><span data-stu-id="93a0a-105">Using the WCF channel model.</span></span>  
  
-   <span data-ttu-id="93a0a-106">使用 WCF 服務模型。</span><span class="sxs-lookup"><span data-stu-id="93a0a-106">Using the WCF service model.</span></span>  
  
 <span data-ttu-id="93a0a-107">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]會公開應用程式可以在其上叫用，接著，可以呼叫應用程式上的作業。</span><span class="sxs-lookup"><span data-stu-id="93a0a-107">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] exposes operations that applications can invoke on it and that it can, in turn, invoke on applications.</span></span> <span data-ttu-id="93a0a-108">這些作業會叫用透過通道傳送 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="93a0a-108">These operations are invoked by sending SOAP messages over a channel.</span></span> <span data-ttu-id="93a0a-109">如果需要回應，它會傳回 SOAP 訊息中透過相同的通道。</span><span class="sxs-lookup"><span data-stu-id="93a0a-109">If a response is required, it is returned in a SOAP message over the same channel.</span></span> <span data-ttu-id="93a0a-110">訊息結構和與每個作業相關聯的 SOAP 動作的相關資訊，請參閱[訊息與 BizTalk adapter for Siebel eBusiness 應用程式的訊息結構描述](../../adapters-and-accelerators/adapter-siebel/messages-and-message-schemas-for-siebel-adapter-in-biztalk.md)。</span><span class="sxs-lookup"><span data-stu-id="93a0a-110">For information about the message structure and the SOAP action associated with each operation, see [Messages and Message Schemas for BizTalk Adapter for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/messages-and-message-schemas-for-siebel-adapter-in-biztalk.md).</span></span>  
  
 <span data-ttu-id="93a0a-111">本節提供有關 Siebel 系統使用支援的作業的相關資訊[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="93a0a-111">This section provides information about the operations supported on the Siebel system using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93a0a-112">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不支援從 Siebel 系統接收傳入的呼叫。</span><span class="sxs-lookup"><span data-stu-id="93a0a-112">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] does not support receiving inbound calls from a Siebel system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="93a0a-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="93a0a-113">In This Section</span></span>  
  
-   [<span data-ttu-id="93a0a-114">在 Siebel 商務元件上的作業</span><span class="sxs-lookup"><span data-stu-id="93a0a-114">Operations on Business Components in Siebel</span></span>](../../adapters-and-accelerators/adapter-siebel/operations-on-business-components-in-siebel.md)  
  
-   [<span data-ttu-id="93a0a-115">在 Siebel 商務服務的相關作業</span><span class="sxs-lookup"><span data-stu-id="93a0a-115">Operations on Business Services in Siebel</span></span>](../../adapters-and-accelerators/adapter-siebel/operations-on-business-services-in-siebel.md)  
  
## <a name="see-also"></a><span data-ttu-id="93a0a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93a0a-116">See Also</span></span>  
 [<span data-ttu-id="93a0a-117">BizTalk Adapter for Siebel eBusiness 應用程式中的概觀</span><span class="sxs-lookup"><span data-stu-id="93a0a-117">Overview of BizTalk Adapter for Siebel eBusiness Applications</span></span>](../../adapters-and-accelerators/adapter-siebel/overview-of-biztalk-adapter-for-siebel-ebusiness-applications.md)