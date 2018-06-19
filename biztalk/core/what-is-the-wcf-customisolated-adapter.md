---
title: WCF-CustomIsolated 配接器為何？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF-CustomIsolated adapters, about WCF-CustomIsolated adapters
ms.assetid: 872fe97a-8a96-4b2a-8cc1-2db9b315c44f
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fdf5a646f586030df6c9492fc6fb2999e49527a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289694"
---
# <a name="what-is-the-wcf-customisolated-adapter"></a><span data-ttu-id="be2fb-103">WCF-CustomIsolated 配接器為何？</span><span class="sxs-lookup"><span data-stu-id="be2fb-103">What Is the WCF-CustomIsolated Adapter?</span></span>
<span data-ttu-id="be2fb-104">WCF-CustomIsolated 配接器是用來啟用在具有外掛式主控件的 BizTalk Server 中使用 WCF 擴充性元件的功能。</span><span class="sxs-lookup"><span data-stu-id="be2fb-104">The WCF-CustomIsolated adapter is used to enable the use of WCF extensibility components in BizTalk Server with an isolated host.</span></span> <span data-ttu-id="be2fb-105">此配接器可以發揮 WCF 架構的完整彈性。</span><span class="sxs-lookup"><span data-stu-id="be2fb-105">The adapter enables complete flexibility of the WCF framework.</span></span> <span data-ttu-id="be2fb-106">它可以讓使用者選取及設定接收位置的 WCF 繫結，以及指定端點行為和安全性設定。</span><span class="sxs-lookup"><span data-stu-id="be2fb-106">It allows users to select and configure a WCF binding for the receive location, and to specify the endpoint behaviors and security settings.</span></span> <span data-ttu-id="be2fb-107">只有裝載在 Internet Information Services (IIS) 中的傳輸方式才能使用這個配接器。</span><span class="sxs-lookup"><span data-stu-id="be2fb-107">This adapter can only be used by transports that are hosted in Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="be2fb-108">WCF-CustomIsolated 配接器只包含一個接收配接器。</span><span class="sxs-lookup"><span data-stu-id="be2fb-108">The WCF-CustomIsolated adapter consists of a receive adapter only.</span></span> <span data-ttu-id="be2fb-109">您可以使用這個 WCF-CustomIsolated 接收配接器，透過您針對在外掛式主控件中執行的接收位置所選取和設定的 WCF 繫結、服務行為、端點行為、安全性機制和輸入訊息內文來源，接收 WCF 服務要求。</span><span class="sxs-lookup"><span data-stu-id="be2fb-109">You use the WCF-CustomIsolated receive adapter to receive WCF service requests through WCF bindings, service behavior, endpoint behavior, security mechanism, and the source of the inbound message body that you selected and configured for the receive location running in an isolated host.</span></span> <span data-ttu-id="be2fb-110">使用 WCF-CustomIsolated 接收配接器的接收位置可以設定為單向或要求-回應 (雙向)。</span><span class="sxs-lookup"><span data-stu-id="be2fb-110">A receive location that uses the WCF-CustomIsolated receive adapter can be configured as one-way or request-response (two-way).</span></span>  
  
 <span data-ttu-id="be2fb-111">如需有關 WCF 接收配接器，請參閱[WCF 配接器為何？](../core/what-are-the-wcf-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="be2fb-111">For more information about WCF receive adapters, see [What Are the WCF Adapters?](../core/what-are-the-wcf-adapters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be2fb-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be2fb-112">See Also</span></span>  
 <span data-ttu-id="be2fb-113">[設定 Wcf-customisolated 配接器](../core/configuring-the-wcf-customisolated-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="be2fb-113">[Configuring the WCF-CustomIsolated Adapter](../core/configuring-the-wcf-customisolated-adapter.md) </span></span>  
 [<span data-ttu-id="be2fb-114">WCF 配接器</span><span class="sxs-lookup"><span data-stu-id="be2fb-114">WCF Adapters</span></span>](../core/wcf-adapters.md)