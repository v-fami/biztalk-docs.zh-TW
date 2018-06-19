---
title: 解析程式管理員 (ResolverMgr) 類別 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 89fa551d-0aca-4777-adbc-2bc46ab8664a
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6621ad0c6b9edb5bf93950f9b9d05a7655f0e36d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294742"
---
# <a name="the-resolver-manager-resolvermgr-class"></a><span data-ttu-id="68a5f-102">解析程式管理員 (ResolverMgr) 類別</span><span class="sxs-lookup"><span data-stu-id="68a5f-102">The Resolver Manager (ResolverMgr) Class</span></span>
<span data-ttu-id="68a5f-103">轉換和路由訊息處理服務會使用**ResolverMgr**執行解析的類別。</span><span class="sxs-lookup"><span data-stu-id="68a5f-103">The Transform and Routing messaging services use the **ResolverMgr** class to perform resolution.</span></span> <span data-ttu-id="68a5f-104">在 ESB 動態轉換和動態傳遞代理程式也使用**ResolverManager**類別來執行在 just-in-time (JIT) 解析。</span><span class="sxs-lookup"><span data-stu-id="68a5f-104">The ESB dynamic transformation and dynamic delivery agents also use the **ResolverManager** class to perform just-in-time (JIT) resolution.</span></span>  
  
 <span data-ttu-id="68a5f-105">ESB 核心安裝程式安裝並註冊**Microsoft.Practices.ESB.Resolver.dll**具有組件**ResolverMgr**在全域組件快取中的類別。</span><span class="sxs-lookup"><span data-stu-id="68a5f-105">The ESB Core installer installs and registers the **Microsoft.Practices.ESB.Resolver.dll** assembly with the **ResolverMgr** class in the global assembly cache.</span></span>  
  
 <span data-ttu-id="68a5f-106">您可以使用這個類別，在您自己的程式碼中您要執行的結束點或地圖的動態解析。</span><span class="sxs-lookup"><span data-stu-id="68a5f-106">You can use this class in your own code where you need to perform dynamic resolution of endpoints or maps.</span></span> <span data-ttu-id="68a5f-107">您也可以擴充這個類別，以使用自訂解決方法。</span><span class="sxs-lookup"><span data-stu-id="68a5f-107">You can also extend this class to use a custom resolution method.</span></span> <span data-ttu-id="68a5f-108">不過，請記住，類別已經支援解析機制，可以使用任何自訂解決器組件，必須符合任何您可能需要的另一種解決方案演算法。</span><span class="sxs-lookup"><span data-stu-id="68a5f-108">However, keep in mind that the class already supports a resolution mechanism that can use any custom resolver assembly, which should accommodate any alternative resolution algorithm you may require.</span></span>  
  
 <span data-ttu-id="68a5f-109">下列程式碼範例示範如何使用**ResolverMgr**類別解析端點。</span><span class="sxs-lookup"><span data-stu-id="68a5f-109">The following code example shows how to use the **ResolverMgr** class to resolve an endpoint.</span></span>  
  
```csharp  
// Move to retrieve the first resolver.  
resolvers = itineraryStep.ResolverCollection;  
resolver = resolvers.Current;  
  
// Pass the resolver configuration to the Resolver Manager for resolution.  
resolverDictionary = Microsoft.Practices.ESB.Resolver.ResolverMgr.Resolve(InboundMessage, resolver);  
  
// Set transport properties.  
transportLocation = resolverDictionary.Item("Resolver.TransportLocation");  
transportType = resolverDictionary.Item("Resolver.TransportType");  
```  
  
 <span data-ttu-id="68a5f-110">通常，您解析程式的連接字串指定至少一個解決方法，例如規則原則、 自訂組件，XPath 陳述式或通用描述、 探索與整合 (UDDI) 的標籤和伺服器名稱的屬性值。</span><span class="sxs-lookup"><span data-stu-id="68a5f-110">Usually, your resolver connection string specifies the property values for at least one resolution method, such as a rules policy, custom assembly, XPath statement, or Universal Description, Discovery, and Integration (UDDI) label and server name.</span></span> <span data-ttu-id="68a5f-111">最後，它會傳回一個字典物件，可以輕鬆地填入從具象的解析程式的自訂事實的解析程式事實的集合。</span><span class="sxs-lookup"><span data-stu-id="68a5f-111">Finally, it returns a dictionary object with a collection of resolver facts, which can be easily populated with custom facts from a concrete resolver.</span></span>  
  
 <span data-ttu-id="68a5f-112">如需 ESB 解決機制的運作方式的詳細資訊，請參閱[使用動態解析和路由](../esb-toolkit/using-dynamic-resolution-and-routing.md)。</span><span class="sxs-lookup"><span data-stu-id="68a5f-112">For more information about how the ESB resolution mechanism works, see [Using Dynamic Resolution and Routing](../esb-toolkit/using-dynamic-resolution-and-routing.md).</span></span>