---
title: "何謂 WCF-Custom 配接器？ | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF-Custom adapters, about WCF-Custom adapters
ms.assetid: 7b2178dd-f737-4784-9bcb-e2b3979bfb0d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e090f82bc43d96dc14295af2fac2807cf1fd137
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-wcf-custom-adapter"></a><span data-ttu-id="b852e-103">何謂 WCF-Custom 配接器？</span><span class="sxs-lookup"><span data-stu-id="b852e-103">What Is the WCF-Custom Adapter?</span></span>
<span data-ttu-id="b852e-104">WCF-Custom 配接器是用來啟用 BizTalk Server 中的 WCF 擴充性元件。</span><span class="sxs-lookup"><span data-stu-id="b852e-104">The WCF-Custom adapter is used to enable the use of WCF extensibility components in BizTalk Server.</span></span> <span data-ttu-id="b852e-105">此配接器可以發揮 WCF 架構的完整彈性。</span><span class="sxs-lookup"><span data-stu-id="b852e-105">The adapter enables complete flexibility of the WCF framework.</span></span> <span data-ttu-id="b852e-106">它可以讓使用者針對接收位置和傳送埠選取及設定 WCF 繫結，</span><span class="sxs-lookup"><span data-stu-id="b852e-106">It allows users to select and configure a WCF binding for the receive location and send port.</span></span> <span data-ttu-id="b852e-107">也能讓使用者設定結束點行為和安全性設定。</span><span class="sxs-lookup"><span data-stu-id="b852e-107">It also allows users to set the endpoint behaviors and security settings.</span></span>  
  
 <span data-ttu-id="b852e-108">WCF-Custom 配接器是由兩個配接器所組成：接收配接器和傳送配接器。</span><span class="sxs-lookup"><span data-stu-id="b852e-108">The WCF-Custom adapter consists of two adapters—a receive adapter and a send adapter.</span></span>  
  
 <span data-ttu-id="b852e-109">**WCF 自訂接收配接器**</span><span class="sxs-lookup"><span data-stu-id="b852e-109">**WCF-Custom Receive Adapter**</span></span>  
  
 <span data-ttu-id="b852e-110">使用 WCF-Custom 接收配接器可以透過您在接收位置的 [傳輸屬性] 對話方塊中所選取和設定的繫結、服務行為、結束點行為、安全性機制和輸入訊息內文的來源，接收 WCF 服務要求。</span><span class="sxs-lookup"><span data-stu-id="b852e-110">You use the WCF-Custom receive adapter to receive WCF service requests through the bindings, service behavior, endpoint behavior, security mechanism, and the source of the inbound message body that you selected and configured in the transport properties dialog in the receive location.</span></span> <span data-ttu-id="b852e-111">使用 WCF-Custom 接收配接器的接收位置可以設定為單向或要求-回應 (雙向)。</span><span class="sxs-lookup"><span data-stu-id="b852e-111">A receive location that uses the WCF-Custom receive adapter can be configured as one-way or request-response (two-way).</span></span>  
  
 <span data-ttu-id="b852e-112">**Wcf-custom 傳送配接器**</span><span class="sxs-lookup"><span data-stu-id="b852e-112">**WCF-Custom Send Adapter**</span></span>  
  
 <span data-ttu-id="b852e-113">使用 WCF-Custom 傳送配接器可以透過您所選取和設定的無類型繫結合約、服務行為、結束點行為、安全性機制和輸出訊息內文的來源，呼叫 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="b852e-113">You use the WCF-Custom send adapter to call a WCF service through the typeless contract with the bindings, service behavior, endpoint behavior, security mechanism, and the source of the outbound message body that you selected and configured.</span></span>  
  
 <span data-ttu-id="b852e-114">如需有關 WCF 接收和傳送配接器，請參閱[WCF 配接器為何？](../core/what-are-the-wcf-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="b852e-114">For more information about WCF receive and send adapters, see [What Are the WCF Adapters?](../core/what-are-the-wcf-adapters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b852e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b852e-115">See Also</span></span>  
 <span data-ttu-id="b852e-116">[設定 WCF 自訂配接器](../core/configuring-the-wcf-custom-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="b852e-116">[Configuring the WCF-Custom Adapter](../core/configuring-the-wcf-custom-adapter.md) </span></span>  
 [<span data-ttu-id="b852e-117">WCF 配接器</span><span class="sxs-lookup"><span data-stu-id="b852e-117">WCF Adapters</span></span>](../core/wcf-adapters.md)