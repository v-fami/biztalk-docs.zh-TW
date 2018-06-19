---
title: 讀取 WCF 如何使用 WCF LOB 配接器 SDK |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 183dd134-7273-4767-bad0-c42ae125985e
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb84124213df8cf1bd401ab80db25586f5ca4534
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22226094"
---
# <a name="read-how-wcf-is-used-by-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="8faf0-102">讀取 WCF 如何使用 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="8faf0-102">Read how WCF is used by the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="8faf0-103">[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]擴充[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道架構，並相依於[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]runtime 能夠提供基本的訊息服務才能公開配接器功能，並且交換資訊。</span><span class="sxs-lookup"><span data-stu-id="8faf0-103">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] extends the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] channel architecture and depends on the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] runtime to provide the basic messaging services required to expose adapter functionality and exchange information.</span></span> 
  
 <span data-ttu-id="8faf0-104">[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供架構，以撰寫配接器，它們在面對[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]，並補充它們，進而與一般配接器的項目，例如中繼資料和連接集區。</span><span class="sxs-lookup"><span data-stu-id="8faf0-104">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] provides a framework for writing adapters, surfacing them in [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], and complementing them with common adapter elements such as metadata and connection pooling.</span></span> <span data-ttu-id="8faf0-105">它也包含支援工具，例如增強經驗[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].NET 應用程式和[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]如[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式和[!INCLUDE[afdevwizardnamelong](../../includes/afdevwizardnamelong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8faf0-105">It also consists of support tools to enhance the experience such as the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] for .NET applications and [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] for [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications and the [!INCLUDE[afdevwizardnamelong](../../includes/afdevwizardnamelong-md.md)].</span></span>  
  
 <span data-ttu-id="8faf0-106">它負責[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]公開服務的取用應用程式，管理不同的端點之間的訊息流程，並提供 SDK 和工具，若要自訂，以設定及監視訊息流程。</span><span class="sxs-lookup"><span data-stu-id="8faf0-106">It is the responsibility of the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] to expose services to a wide array of consuming applications, to manage the flow of messages between different endpoints, and to provide an SDK and tools to customize, configure, and monitor message flow.</span></span> <span data-ttu-id="8faf0-107">例如，開發人員可以自訂行為[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]藉由擴充其通道的自訂訊息處理常式。</span><span class="sxs-lookup"><span data-stu-id="8faf0-107">For example, a developer can customize the behavior of a [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] by extending its channel with custom message handlers.</span></span>  
  
 <span data-ttu-id="8faf0-108">之間的關聯性[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]下列高層級架構圖所示。</span><span class="sxs-lookup"><span data-stu-id="8faf0-108">The relationship between the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] is shown in the following high-level architectural figure.</span></span>  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/asdk-wcf.gif "ASDK_WCF")  
  
 <span data-ttu-id="8faf0-109">[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]建置最上層的[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]做為擴充[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型。</span><span class="sxs-lookup"><span data-stu-id="8faf0-109">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is built on top of [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] as an extension to the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] channel model.</span></span> <span data-ttu-id="8faf0-110">它提供了特定的網域和簡化物件模型和工具集來建置為自訂配接器[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道。</span><span class="sxs-lookup"><span data-stu-id="8faf0-110">It provides a domain-specific and simplified object model and tool set for building adapters as custom [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] channels.</span></span> <span data-ttu-id="8faf0-111">使用所建置的配接器[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]當成自訂[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]繫結。</span><span class="sxs-lookup"><span data-stu-id="8faf0-111">Adapters built using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] are surfaced as custom [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] bindings.</span></span>  
  
 <span data-ttu-id="8faf0-112">下圖顯示使用指定的介面卡繫結的輸出訊息交換。</span><span class="sxs-lookup"><span data-stu-id="8faf0-112">The following figure shows the outbound message exchange using a given adapter binding.</span></span>  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/58609452-d09e-4dbd-b470-c92a29977858.gif "58609452-d09e-4dbd-b470-c92a29977858")  
  
 <span data-ttu-id="8faf0-113">下圖顯示使用指定的介面卡繫結的輸入的訊息交換。</span><span class="sxs-lookup"><span data-stu-id="8faf0-113">The following figure shows the inbound message exchange using a given adapter binding.</span></span>  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/b62d5040-7e40-4edd-ac7b-69768131c51b.gif "b62d5040-7e40-4edd-ac7b-69768131c51b")  
  
 <span data-ttu-id="8faf0-114">如需有關[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型，請參閱[通道模型概觀](https://msdn.microsoft.com/library/ms729840.aspx)。</span><span class="sxs-lookup"><span data-stu-id="8faf0-114">For more information about the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] channel model, see [Channel Model Overview](https://msdn.microsoft.com/library/ms729840.aspx).</span></span>  
  
## <a name="wcf-services-and-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="8faf0-115">WCF 服務和 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="8faf0-115">WCF Services and the WCF LOB Adapter SDK</span></span>  
 <span data-ttu-id="8faf0-116">當開發一般[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務時，第一個步驟是建立共用與外界描述如何與服務通訊的服務合約。</span><span class="sxs-lookup"><span data-stu-id="8faf0-116">When developing a typical [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service, the first step is to create the contract for the service that is shared with the outside world that describes how to communicate with the service.</span></span> <span data-ttu-id="8faf0-117">此合約基本上可指定集合與存取服務所提供的作業所需的訊息結構。</span><span class="sxs-lookup"><span data-stu-id="8faf0-117">This contract essentially specifies the collection and structure of messages required to access the operations offered by the service.</span></span>  
  
 <span data-ttu-id="8faf0-118">這個合約會公開為服務時，一旦[Service Model Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx)可以用來建立[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]用戶端，才能加以使用。</span><span class="sxs-lookup"><span data-stu-id="8faf0-118">Once this contract is exposed as a service, the [Service Model Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx) can be used to create a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client to consume it.</span></span> <span data-ttu-id="8faf0-119">合約會提供一組靜態資訊的作業和不可以變更的訊息。</span><span class="sxs-lookup"><span data-stu-id="8faf0-119">The contract provides information about a static set of operations and messages that must not change.</span></span> 
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/a410af83-ee3b-46d0-9afd-d32970f5ba0a.gif "a410af83-ee3b-46d0-9afd-d32970f5ba0a")  
  
 <span data-ttu-id="8faf0-120">相反地，配接器使用來建置[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供一組動態集合的作業和可用的特定業務系統內的資料相關的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="8faf0-120">In contrast, adapters built using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] provide a dynamic set of metadata about the collection of operations and data that are available within a line-of-business system.</span></span> <span data-ttu-id="8faf0-121">特定業務系統通常會有太多的作業一個合約中所述，可能會有新作業加入至回應新的商務需求。</span><span class="sxs-lookup"><span data-stu-id="8faf0-121">The line-of-business system often has too many operations to be described in one contract and may have new operations added to respond to emerging business needs.</span></span>  
  
 <span data-ttu-id="8faf0-122">例如，特定業務系統可能會提供帳戶管理作業。</span><span class="sxs-lookup"><span data-stu-id="8faf0-122">For example, a line-of-business system may provide account management operations.</span></span> <span data-ttu-id="8faf0-123">在識別需要簡化的新客戶帳戶的建立作業之後, 公司更新特定業務系統上，以包含新的作業。</span><span class="sxs-lookup"><span data-stu-id="8faf0-123">After identifying a need to streamline the creation of new customer accounts, the company updates the line-of-business system to include the new operation.</span></span> <span data-ttu-id="8faf0-124">使用所建置的配接器[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]公開它提供給用戶端的中繼資料中的這項作業。</span><span class="sxs-lookup"><span data-stu-id="8faf0-124">An adapter built using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] exposes this operation in the metadata it provides to clients.</span></span>  
  
 <span data-ttu-id="8faf0-125">在設計階段[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]-根據配接器會產生以動態方式以符合業務的系統需求的合約。</span><span class="sxs-lookup"><span data-stu-id="8faf0-125">At design time, the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]-based adapter generates contracts dynamically to meet the needs of the line-of-business system.</span></span>  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/2f4d896a-14d9-43f4-8cdc-f816c5eab46d.gif "2f4d896a-14d9-43f4-8cdc-f816c5eab46d")  
  
 <span data-ttu-id="8faf0-126">提供 ASDK[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]和[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]配接器取用者在設計階段產生動態合約的工具。</span><span class="sxs-lookup"><span data-stu-id="8faf0-126">The ASDK provides [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] tools for the adapter consumer to generate dynamic contracts at design time.</span></span>  
  
 <span data-ttu-id="8faf0-127">在執行階段，當訊息傳送到配接器使用撰寫[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，配接器通常必須採取一連串的動作上接收訊息。</span><span class="sxs-lookup"><span data-stu-id="8faf0-127">At runtime, when the message flows into the adapter written using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], the adapter often must take a series of actions on the receive message.</span></span> <span data-ttu-id="8faf0-128">這些動作包括：</span><span class="sxs-lookup"><span data-stu-id="8faf0-128">These actions include:</span></span>  
  
-   <span data-ttu-id="8faf0-129">查閱與訊息有關的中繼資料</span><span class="sxs-lookup"><span data-stu-id="8faf0-129">Looking up metadata pertaining to the message</span></span>  
  
-   <span data-ttu-id="8faf0-130">開啟郵件</span><span class="sxs-lookup"><span data-stu-id="8faf0-130">Opening the message</span></span>  
  
-   <span data-ttu-id="8faf0-131">解譯訊息</span><span class="sxs-lookup"><span data-stu-id="8faf0-131">Interpreting the message</span></span>  
  
-   <span data-ttu-id="8faf0-132">在特定業務系統中呼叫適當的函式</span><span class="sxs-lookup"><span data-stu-id="8faf0-132">Calling the appropriate functions in the line-of-business system</span></span>  
  
 <span data-ttu-id="8faf0-133">如果是[!INCLUDE[nextref_btsWinCommFoundation_md](../../includes/nextref-btswincommfoundation-md.md)]服務，訊息直接傳遞不含所透過的中繼資料解析。</span><span class="sxs-lookup"><span data-stu-id="8faf0-133">In the case of a [!INCLUDE[nextref_btsWinCommFoundation_md](../../includes/nextref-btswincommfoundation-md.md)] service, messages simply pass through without being resolved through metadata.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8faf0-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8faf0-134">See Also</span></span>  
 [<span data-ttu-id="8faf0-135">BizTalk Adapter for Oracle 資料庫與 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="8faf0-135">BizTalk Adapter for Oracle Database and the WCF LOB Adapter SDK</span></span>](../adapter-oracle-database/architecture-overview-of-the-biztalk-adapter-for-oracle-database.md)