---
title: 了解 WCF LOB 配接器 SDK 所建立的配接器的 WCF 安全性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1ee402b-ffda-42c1-8d85-d7cbe073a307
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: baf0c62c3d0c37c1f69cb944112ff832dade5ec4
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="understand-wcf-security-on-the-adapter-created-with-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="ee65f-102">了解 WCF LOB 配接器 SDK 所建立的配接器的 WCF 安全性</span><span class="sxs-lookup"><span data-stu-id="ee65f-102">Understand WCF security on the adapter created with the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="ee65f-103">[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]擴充[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道架構，而依賴訊息基礎結構和它所提供的 API。</span><span class="sxs-lookup"><span data-stu-id="ee65f-103">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] extends the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] channel architecture and relies on the messaging infrastructure and the API that it provides.</span></span>  <span data-ttu-id="ee65f-104">WCF LOB 配接器必須連接到目標系統，因此需設定配接器以驗證及其他建立目標系統連接所需的安全性資訊。</span><span class="sxs-lookup"><span data-stu-id="ee65f-104">A WCF LOB adapter needs to establish a connection to target systems, and hence it is necessary to configure the adapter with authentication and other security information required to make the target system connections.</span></span>  
  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]<span data-ttu-id="ee65f-105"> 分散式程式設計平台根據可以通過許多不同的節點、 SOAP 媒介，防火牆和潛在網際網路路由傳送來自特定業務系統至配接器和用戶端的 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="ee65f-105"> is a distributed programming platform based on SOAP messages that can travel through many different nodes, SOAP intermediaries, firewalls, and potentially the Internet en-route from the line-of-business system to the adapter and on to the client.</span></span> <span data-ttu-id="ee65f-106">這可能會造成數目對配接器和部署案例的不同的安全性威脅。</span><span class="sxs-lookup"><span data-stu-id="ee65f-106">This could present a number of different security threats to your adapter and deployment scenario.</span></span>  
  
 <span data-ttu-id="ee65f-107">安全性會在任何企業架構解決方案中扮演的主要部分。</span><span class="sxs-lookup"><span data-stu-id="ee65f-107">Security plays a major part in any enterprise architecture solution.</span></span> <span data-ttu-id="ee65f-108">您可以利用機密性、 完整性、 驗證和授權功能以協助保護不受安全性威脅的配接器的 WCF 安全性模式中提供。</span><span class="sxs-lookup"><span data-stu-id="ee65f-108">You can leverage the confidentiality, integrity, authentication, and authorization features provided in the WCF security model to help secure the adapter from security threats.</span></span> <span data-ttu-id="ee65f-109">您也必須考慮的傳輸和訊息層級安全性來保護這些兩個實體之間的通訊的配接器與目標系統之間。</span><span class="sxs-lookup"><span data-stu-id="ee65f-109">You must also consider the transport and message-level security between the adapter and the target system to protect the communication between these two entities.</span></span> <span data-ttu-id="ee65f-110">雖然 WCF 有提供一組豐富的 WS-\* 規格，實作這些進階的安全性標準，在您的配接器將取決於特定業務系統所提供的功能。</span><span class="sxs-lookup"><span data-stu-id="ee65f-110">Even though WCF provides a rich set of WS-\* specifications, implementation of these advanced security standards in your adapter will depend on the capabilities provided by the line-of-business system.</span></span>  
  
 <span data-ttu-id="ee65f-111">如需有關[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]安全性包括概觀、 概念、 常見的案例和最佳作法，請參閱[Windows Communication Foundation 安全性](https://msdn.microsoft.com/library/ms732362.aspx)。</span><span class="sxs-lookup"><span data-stu-id="ee65f-111">For more information about [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] security including an overview, concepts, common scenarios, and best practices, see [Windows Communication Foundation Security](https://msdn.microsoft.com/library/ms732362.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ee65f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee65f-112">See Also</span></span>  
 [<span data-ttu-id="ee65f-113">計劃和設計配接器使用 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="ee65f-113">Plan and design an adapter using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-an-adapter-using-the-wcf-lob-adapter-sdk.md)