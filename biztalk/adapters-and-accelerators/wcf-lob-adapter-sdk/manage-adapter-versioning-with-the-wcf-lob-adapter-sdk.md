---
title: 管理配接器使用 WCF LOB 配接器 SDK 進行版本控制 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb596fdd-251c-4978-9f33-cf2883d281d8
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8dfb323bf810f69c8a8f1f857b0d0240c14c4d18
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975183"
---
# <a name="manage-adapter-versioning-with-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="05f9c-102">管理配接器使用 WCF LOB 配接器 SDK 進行版本控制</span><span class="sxs-lookup"><span data-stu-id="05f9c-102">Manage adapter versioning with the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="05f9c-103">初始部署後的配接器和潛在進行數次在其存留期期間，配接器 （和它們所公開的端點） 可能需要針對各種原因而變更。</span><span class="sxs-lookup"><span data-stu-id="05f9c-103">After initial deployment of adapters and potentially several times during their lifetime, adapters (and the endpoints they expose) may need to be changed for a variety of reasons.</span></span> <span data-ttu-id="05f9c-104">這些原因，包括變更商務需求、 資訊技術需求或商務系統的配接器本身的一行的問題。</span><span class="sxs-lookup"><span data-stu-id="05f9c-104">These reasons include changing business needs, information technology requirements, or issues with the line of business system or the adapter itself.</span></span> <span data-ttu-id="05f9c-105">本主題討論不同的策略來處理使用撰寫配接器的版本控制[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="05f9c-105">This topic discusses different strategies for handling versioning for adapters that are written using the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)].</span></span>  
  
## <a name="versioning-and-windows-communication-foundation"></a><span data-ttu-id="05f9c-106">版本控制和 Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="05f9c-106">Versioning and Windows Communication Foundation</span></span>  
 <span data-ttu-id="05f9c-107">[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]建置於[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]而且依賴其基礎結構系統之間交換訊息。</span><span class="sxs-lookup"><span data-stu-id="05f9c-107">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is built upon  [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] and relies on its infrastructure for exchanging messages between systems.</span></span> <span data-ttu-id="05f9c-108">使用的機制，[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]公開 （expose)，您可以版本服務與資料合約。</span><span class="sxs-lookup"><span data-stu-id="05f9c-108">Using mechanisms that  [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] exposes, you can version both services and data contracts.</span></span> <span data-ttu-id="05f9c-109">如需詳細資訊，包括最佳作法服務版本設定，請參閱[服務版本設定](http://go.microsoft.com/fwlink/?LinkId=85497)在[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]線上參考。</span><span class="sxs-lookup"><span data-stu-id="05f9c-109">For more information, including best practices for service versioning, see [Service Versioning](http://go.microsoft.com/fwlink/?LinkId=85497) in the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] online reference.</span></span> <span data-ttu-id="05f9c-110">如需詳細資訊，包括最佳作法資料合約版本控制，請參閱[資料合約版本控制](http://go.microsoft.com/fwlink/?LinkId=120177)在[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]線上參考。</span><span class="sxs-lookup"><span data-stu-id="05f9c-110">For more information, including best practices for data contract versioning, see [Data Contract Versioning](http://go.microsoft.com/fwlink/?LinkId=120177) in the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] online reference.</span></span>  
  
## <a name="versioning-scenarios"></a><span data-ttu-id="05f9c-111">版本設定案例</span><span class="sxs-lookup"><span data-stu-id="05f9c-111">Versioning Scenarios</span></span>  
 <span data-ttu-id="05f9c-112">有兩種主要的版本控制案例：</span><span class="sxs-lookup"><span data-stu-id="05f9c-112">There are two primary versioning scenarios:</span></span>  
  
- <span data-ttu-id="05f9c-113">一個配接器版本支援目標系統的多個的版本。</span><span class="sxs-lookup"><span data-stu-id="05f9c-113">One adapter version supports multiple versions of the target system.</span></span>  
  
- <span data-ttu-id="05f9c-114">兩個或多個配接器版本支援在相同的系統或兩個或多個不同的系統。</span><span class="sxs-lookup"><span data-stu-id="05f9c-114">Two or more adapter versions support the same system or two or more different systems.</span></span>  
  
  <span data-ttu-id="05f9c-115">您可能也需要釋放您的配接器的新版本，如果更新[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]會影響現有的功能。</span><span class="sxs-lookup"><span data-stu-id="05f9c-115">You may also need to release a new version of your adapter if updates to the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] affect existing functionality.</span></span>  
  
  <span data-ttu-id="05f9c-116">每個案例都需要不同的版本控制策略。</span><span class="sxs-lookup"><span data-stu-id="05f9c-116">Each of these scenarios requires a different versioning strategy.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05f9c-117">[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]不會強制使用任何特定的版本控制案例。</span><span class="sxs-lookup"><span data-stu-id="05f9c-117">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] does not enforce any specific versioning scenarios.</span></span> <span data-ttu-id="05f9c-118">它會保留給開發人員決定配接器的版本控制需求。</span><span class="sxs-lookup"><span data-stu-id="05f9c-118">It is left to the developer to determine versioning requirements for an adapter.</span></span>  
  
### <a name="one-adapter-supports-multiple-versions-of-target-system"></a><span data-ttu-id="05f9c-119">一張介面卡支援多種版本的目標系統</span><span class="sxs-lookup"><span data-stu-id="05f9c-119">One adapter supports multiple versions of target system</span></span>  
 <span data-ttu-id="05f9c-120">當配接器支援多個版本的目標系統時，您應該公開一或多個繫結屬性，可用來識別所需的版本。</span><span class="sxs-lookup"><span data-stu-id="05f9c-120">When the adapter supports multiple versions of the target system, you should expose one or more binding properties that can be used to identify the desired version.</span></span> <span data-ttu-id="05f9c-121">例如，配接器可能支援多個目標系統的廠商所提供的通訊程式庫。</span><span class="sxs-lookup"><span data-stu-id="05f9c-121">For example, an adapter might support multiple communication libraries supplied by the target system's vendor.</span></span> <span data-ttu-id="05f9c-122">使用名為"LibraryVersion 」 的自訂繫結屬性，配接器取用者可以選擇使用哪一個程式庫基礎的部署環境或其他需求。</span><span class="sxs-lookup"><span data-stu-id="05f9c-122">Using a custom binding property named "LibraryVersion," the adapter consumer could choose which library to use based on the deployment environment or other requirements.</span></span>  
  
### <a name="two-or-more-adapters-support-one-version-of-target-system"></a><span data-ttu-id="05f9c-123">兩個或多個配接器支援目標系統的一個的版本</span><span class="sxs-lookup"><span data-stu-id="05f9c-123">Two or more adapters support one version of target system</span></span>  
 <span data-ttu-id="05f9c-124">在此情況下，每個配接器應該使用唯一的配置 (ContosoV1: / / 和 ContosoV2: / /) 和唯一的繫結名稱 （ContosoV1Binding 和 ContosoV2Binding）。</span><span class="sxs-lookup"><span data-stu-id="05f9c-124">In this case, each adapter should use a unique scheme (ContosoV1:// and ContosoV2://) and a unique binding name (ContosoV1Binding and ContosoV2Binding).</span></span> <span data-ttu-id="05f9c-125">廠商應該考慮使用中的配置和繫結名稱 （例如 Microsoft.ContosoV1:// 和 Microsoft.ContosoV1Binding） 及其名稱。</span><span class="sxs-lookup"><span data-stu-id="05f9c-125">Vendors should consider using their name in the scheme and binding name as well (for example, Microsoft.ContosoV1:// and Microsoft.ContosoV1Binding).</span></span>  
  
### <a name="new-versions-of-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="05f9c-126">WCF LOB 配接器 SDK 的新版本</span><span class="sxs-lookup"><span data-stu-id="05f9c-126">New versions of the WCF LOB Adapter SDK</span></span>  
 <span data-ttu-id="05f9c-127">當新版[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]會發行，您將能夠安裝新版本，而不必重新編譯您的配接器，因為[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]發行都可以與舊版相容。</span><span class="sxs-lookup"><span data-stu-id="05f9c-127">When new versions of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] are released, you will be able to install the new version without having to recompile your adapter, since [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] releases are be backward-compatible.</span></span> <span data-ttu-id="05f9c-128">不過，您應該評估新的版本，以判斷是否有所變更的功能，取決於您的配接器，或者如果沒有會受益於您的配接器實作的新功能。</span><span class="sxs-lookup"><span data-stu-id="05f9c-128">However, you should evaluate new releases to determine if there is a change in functionality that your adapter depends on, or if there is new functionality that your adapter would benefit from implementing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05f9c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05f9c-129">See Also</span></span>  
 [<span data-ttu-id="05f9c-130">使用 WCF LOB 配接器 SDK 開發最佳做法</span><span class="sxs-lookup"><span data-stu-id="05f9c-130">Development best practices using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/development-best-practices-using-the-wcf-lob-adapter-sdk.md)