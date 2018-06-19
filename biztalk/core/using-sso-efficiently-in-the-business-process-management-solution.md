---
title: 商務程序管理解決方案中有效使用 SSO |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SSO, process management solutions
- SSO, configuration values
- caching, configuration values [SSO]
- SSO, caching
- process management solution tutorial, SSO
ms.assetid: 39fbc42d-caa4-4003-a13b-5cde578eb5e1
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 99575e54b887124bfa4c33fc5257cd057ea818fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288518"
---
# <a name="using-sso-efficiently-in-the-business-process-management-solution"></a><span data-ttu-id="4e2ca-102">商務程序管理解決方案中有效使用 SSO</span><span class="sxs-lookup"><span data-stu-id="4e2ca-102">Using SSO Efficiently in the Business Process Management Solution</span></span>
<span data-ttu-id="4e2ca-103">如同服務導向解決方案，商務程序管理解決方案也使用「企業單一登入」(SSO) 來儲存組態值，例如，訂單處理階段數目。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-103">Like the Service Oriented solution, the Business Process Management solution uses Enterprise Single Sign-On (SSO) to store configuration values such as the number of order processing stages.</span></span> <span data-ttu-id="4e2ca-104">此解決方案使用密碼存放區，因為只要安裝 BizTalk，密碼存放區就會存在，SSO 會快取組態資訊，讓組態值隨時可供使用，而且它也可以保護如資料庫連接字串和密碼等資訊。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-104">It uses the secret store because it is present whenever BizTalk is installed, SSO caches the configuration information so that the values are readily available, and it can protect information such as database connection strings and passwords.</span></span> <span data-ttu-id="4e2ca-105">基於這些理由，即使未使用「單一登入」來管理與後端應用程式的連線，密碼存放區仍是保存組態資訊的理想位置。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-105">For all of these reasons, the secret store is a good place for the configuration information even if Single Sign-On weren't being used for managing connections to the backend applications.</span></span>  
  
 <span data-ttu-id="4e2ca-106">為減少延遲，此解決方案將使用本機快取做為組態值。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-106">To reduce latency, the solution uses a local cache for the configuration values.</span></span> <span data-ttu-id="4e2ca-107">此解決方案每五分鐘會重新整理一次快取。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-107">The solution refreshes the cache every five minutes.</span></span>  
  
 <span data-ttu-id="4e2ca-108">本主題描述解決方案使用的快取機制。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-108">This topic describes the caching mechanism used by the solution.</span></span> <span data-ttu-id="4e2ca-109">本解決方案與服務導向解決方案的 SSO 快取方式稍有不同。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-109">This solution takes a slightly different approach to SSO caching than does the service oriented solution.</span></span> <span data-ttu-id="4e2ca-110">描述如何在服務導向解決方案會快取 SSO 值，請參閱[使用 SSO 有效率地在服務導向解決方案](../core/using-sso-efficiently-in-the-service-oriented-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-110">For a description of how the service oriented solution caches SSO values, see [Using SSO Efficiently in the Service Oriented Solution](../core/using-sso-efficiently-in-the-service-oriented-solution.md).</span></span>  
  
## <a name="caching-configuration-values-locally"></a><span data-ttu-id="4e2ca-111">在本機快取組態值</span><span class="sxs-lookup"><span data-stu-id="4e2ca-111">Caching Configuration Values Locally</span></span>  
 <span data-ttu-id="4e2ca-112">商務程序管理解決方案使用單一物件中的屬性，以供存取 SSO 值。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-112">The business process management solution uses properties on a singleton object to provide access to the SSO values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e2ca-113">請您回想，單一物件是只能有一個執行個體的物件。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-113">Recall that a singleton object is an object that can have only one instance.</span></span> <span data-ttu-id="4e2ca-114">如需單一物件和在 C# 中建立它們的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=58806](http://go.microsoft.com/fwlink/?LinkId=58806)。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-114">For more information about singleton objects and creating them in C#, see [http://go.microsoft.com/fwlink/?LinkId=58806](http://go.microsoft.com/fwlink/?LinkId=58806).</span></span>  
  
 <span data-ttu-id="4e2ca-115">在解決方案中，協調流程首先會擷取單一物件，然後透過該物件的屬性來參考值。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-115">In the solution, an orchestration first retrieves the singleton object and then references the values through the object's properties.</span></span> <span data-ttu-id="4e2ca-116">以下為程式碼**OrderManager**協調流程：</span><span class="sxs-lookup"><span data-stu-id="4e2ca-116">Here is code from the **OrderManager** orchestration:</span></span>  
  
```  
configData = Microsoft.Samples.BizTalk.SouthridgeVideo.Utilities  
                .SsoConfigHelper.Singleton;  
numStages = configData.TotalStages;  
```  
  
 <span data-ttu-id="4e2ca-117">協調流程會呼叫**單一**方法**SsoConfigHelper**一份物件存取的物件。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-117">The orchestration calls the **Singleton** method on the **SsoConfigHelper** object to get access to the one copy of the object.</span></span> <span data-ttu-id="4e2ca-118">協調流程將會與該物件，擷取處理階段數目**TotalStages**。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-118">With the object in hand, the orchestration retrieves the number of processing stages, **TotalStages**.</span></span>  
  
 <span data-ttu-id="4e2ca-119">方案會遵循一般的方法，來建立單一： 讓建構函式成為 private，讓物件建立本身的執行個體並指派給私用變數，並透過方法或屬性，讓您存取變數的值。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-119">The solution follows a common method of creating a singleton: make the constructor private, have the object create an instance of itself and assign that to a private variable, and, through a method or property, provide access to the value of that variable.</span></span> <span data-ttu-id="4e2ca-120">**SsoConfigHelper**物件使用的屬性，**單一**，以存取本身的單一複本。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-120">The **SsoConfigHelper** object uses a property, **Singleton**, to provide access to the single copy of itself.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e2ca-121">**SsoConfigHelper**物件使用的靜態建構函式，從 SSO 快取取得初始值並設定重新整理機制。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-121">The **SsoConfigHelper** object uses a static constructor to get the initial values from the SSO cache and to set up the refresh mechanism.</span></span> <span data-ttu-id="4e2ca-122">由於無法呼叫靜態建構函式，所以它會保留單一設計。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-122">Because a static constructor cannot be called, it preserves the singleton design.</span></span> <span data-ttu-id="4e2ca-123">如需靜態建構函式的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=59142](http://go.microsoft.com/fwlink/?LinkId=59142)。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-123">For more information about static constructors, see [http://go.microsoft.com/fwlink/?LinkId=59142](http://go.microsoft.com/fwlink/?LinkId=59142).</span></span>  
  
 <span data-ttu-id="4e2ca-124">協調流程直接或間接參考的所有物件都必須可序列化。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-124">All objects that an orchestration references, whether directly or indirectly, must be serializable.</span></span> <span data-ttu-id="4e2ca-125">如需詳細資訊，請參閱 < 序列化 >[持續性和協調流程引擎](../core/persistence-and-the-orchestration-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-125">For more information, see "Serialization" in [Persistence and the Orchestration Engine](../core/persistence-and-the-orchestration-engine.md).</span></span> <span data-ttu-id="4e2ca-126">雖然**SsoConfigHelper**物件必須為可序列化，若引擎凍結協調流程中，當協調流程解除凍結，仍會使用單一的目前物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-126">Although the **SsoConfigHelper** object is necessarily serializable, if the engine dehydrates the orchestration, when the orchestration rehydrates it will still use the single, current instance of the object.</span></span> <span data-ttu-id="4e2ca-127">如需序列化與 BizTalk Server 變數的詳細資訊，請參閱[協調流程變數的型別](../core/orchestration-variable-types.md)。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-127">For more information about serialization and BizTalk Server variables, see [Orchestration Variable Types](../core/orchestration-variable-types.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e2ca-128">在服務導向解決方案中，物件上的所有公用方法都是靜態的。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-128">All public methods on the object in the service oriented solution are static.</span></span> <span data-ttu-id="4e2ca-129">因此協調流程不需指派執行個體給變數，類別也不需要序列化。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-129">Thus the orchestration does not need to assign an instance to a variable, and there is no need for the class to be serialized.</span></span>  
  
 <span data-ttu-id="4e2ca-130">**SsoConfigHelper**物件會使用相同的機制來擷取和重新整理組態值，如同服務導向解決方案。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-130">The **SsoConfigHelper** object uses the same mechanisms to retrieve and refresh configuration values as does the service oriented solution.</span></span> <span data-ttu-id="4e2ca-131">並且也使用相同的鎖定模式。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-131">The same pattern of locking is also used.</span></span> <span data-ttu-id="4e2ca-132">如需有關這些機制的詳細資訊，請參閱[使用 SSO 有效率地在服務導向解決方案](../core/using-sso-efficiently-in-the-service-oriented-solution.md)及原始程式碼的**SsoConfigHelper**。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-132">For more information about these mechanisms, see [Using SSO Efficiently in the Service Oriented Solution](../core/using-sso-efficiently-in-the-service-oriented-solution.md) and the source code for **SsoConfigHelper**.</span></span>  
  
 <span data-ttu-id="4e2ca-133">商務程序管理解決方案的單一登入快取服務導向解決方案中執行，例如實作**IPropertyBag**介面從**ipropertybag**命名空間來儲存值。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-133">Like the Single Sign-On caching performed in the service oriented solution, the business process management solution implements the **IPropertyBag** interface from the **Microsoft.BizTalk.SSOClient.Interop** namespace to store the values.</span></span> <span data-ttu-id="4e2ca-134">商務程序管理解決方案使用**HybridDictionary**物件而非**NameValueCollection**物件。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-134">The business process management solution uses a **HybridDictionary** object rather than a **NameValueCollection** object.</span></span>  
  
 <span data-ttu-id="4e2ca-135">和服務導向解決方案不同的是，商務程序管理解決方案會公開具有對應至組態資料的屬性之物件。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-135">Unlike the Service Oriented solution, the Business Process Management solution exposes an object with properties that correspond to the configuration data.</span></span> <span data-ttu-id="4e2ca-136">如此，協調流程就不需處理訊息類型的差異。</span><span class="sxs-lookup"><span data-stu-id="4e2ca-136">This prevents the orchestration from having to deal with differences in message types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e2ca-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e2ca-137">See Also</span></span>  
 [<span data-ttu-id="4e2ca-138">商務程序管理解決方案的實作重點</span><span class="sxs-lookup"><span data-stu-id="4e2ca-138">Implementation Highlights of the Business Process Management Solution</span></span>](../core/implementation-highlights-of-the-business-process-management-solution.md)