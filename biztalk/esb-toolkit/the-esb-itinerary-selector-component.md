---
title: ESB 路線的選取器元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c2cd8a85-e036-4817-9541-3fd720ca04ef
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c83cdd0b2022eb7dc4ad78e5702f5c21e4c4f432
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295150"
---
# <a name="the-esb-itinerary-selector-component"></a><span data-ttu-id="d4731-102">ESB 路線的選取器元件</span><span class="sxs-lookup"><span data-stu-id="d4731-102">The ESB Itinerary Selector Component</span></span>
<span data-ttu-id="d4731-103">ESB 行程選取器元件可讓沒有 SOAP 標頭來選取適當的伺服器端路線的解析程式的說明訊息通過 ESB 行程的內送訊息。</span><span class="sxs-lookup"><span data-stu-id="d4731-103">The ESB Itinerary Selector component allows incoming messages that do not have the itinerary SOAP header to pass through the ESB by selecting an appropriate server-side itinerary for the message with the help of a resolver.</span></span> <span data-ttu-id="d4731-104">元件也用於使用 SOAP 標頭定義的名稱和版本的路線，用戶端要求的訊息。</span><span class="sxs-lookup"><span data-stu-id="d4731-104">The component is also used for messages that use a SOAP header to define the name and version of an itinerary, as requested by the client.</span></span>  
  
## <a name="installation"></a><span data-ttu-id="d4731-105">安裝</span><span class="sxs-lookup"><span data-stu-id="d4731-105">Installation</span></span>  
 <span data-ttu-id="d4731-106">自動安裝 ESB 核心安裝**ItinerarySelector**元件的 BizTalk Server 管線元件資料夾中。</span><span class="sxs-lookup"><span data-stu-id="d4731-106">Installing the ESB Core automatically installs the **ItinerarySelector** component in the BizTalk Server Pipeline Components folder.</span></span>  
  
## <a name="how-it-works"></a><span data-ttu-id="d4731-107">運作方式</span><span class="sxs-lookup"><span data-stu-id="d4731-107">How It Works</span></span>  
 <span data-ttu-id="d4731-108">ESB 行程選取器元件會接收管線中只可位於 Microsoft BizTalk 管線元件。</span><span class="sxs-lookup"><span data-stu-id="d4731-108">The ESB Itinerary Selector component is a Microsoft BizTalk pipeline component that can reside only in a receive pipeline.</span></span> <span data-ttu-id="d4731-109">元件選取用於伺服器端行程中處理訊息。</span><span class="sxs-lookup"><span data-stu-id="d4731-109">The component selects a server-side itinerary for use in processing a message.</span></span> <span data-ttu-id="d4731-110">當訊息通過接收管線中的元件，元件會讀取其組態，並使用**ResolverConnectionString**呼叫正確的解析程式來查閱適當路線時要使用的屬性處理訊息。</span><span class="sxs-lookup"><span data-stu-id="d4731-110">As the message passes through the component in a receive pipeline, the component reads its configuration and uses the **ResolverConnectionString** property to call the correct resolver to look up the appropriate itinerary to use when processing the message.</span></span> <span data-ttu-id="d4731-111">行程選取器元件，然後執行路線管線元件來驗證訊息和升級的屬性以確保訊息會繼續到下個處理階段所需的相同步驟。</span><span class="sxs-lookup"><span data-stu-id="d4731-111">The Itinerary Selector component then performs the same steps as the Itinerary pipeline component to validate the message and promote the properties necessary to ensure the message continues to the next processing stage.</span></span>  
  
## <a name="using-the-esb-itinerary-selector-component"></a><span data-ttu-id="d4731-112">使用 ESB 路線的選取器元件</span><span class="sxs-lookup"><span data-stu-id="d4731-112">Using the ESB Itinerary Selector Component</span></span>  
 <span data-ttu-id="d4731-113">您可以 ESB 行程元件新增至接收管線，然後使用管線，接收位置中。</span><span class="sxs-lookup"><span data-stu-id="d4731-113">You can add the ESB Itinerary component to a receive pipeline and then use the pipeline in a receive location.</span></span> <span data-ttu-id="d4731-114">當此元件設定為 WCF 上手、 名稱和版本的路線 （如 SOAP 標頭中所表示），用戶端要求中的行程靜態解析程式會擷取從訊息內容和用來選取適當路線。</span><span class="sxs-lookup"><span data-stu-id="d4731-114">When this component is configured with the ITINERARY-STATIC resolver in WCF on-ramp, the name and version of the itinerary requested by the client (as represented in the SOAP header) will be retrieved from the message context and used to select the appropriate itinerary.</span></span>  
  
## <a name="component-properties"></a><span data-ttu-id="d4731-115">元件屬性</span><span class="sxs-lookup"><span data-stu-id="d4731-115">Component Properties</span></span>  
 <span data-ttu-id="d4731-116">ESB 行程選取器元件會公開三個公用屬性：</span><span class="sxs-lookup"><span data-stu-id="d4731-116">The ESB Itinerary Selector component exposes three public properties:</span></span>  
  
-   <span data-ttu-id="d4731-117">**IgnoreErrorKey**。</span><span class="sxs-lookup"><span data-stu-id="d4731-117">**IgnoreErrorKey**.</span></span> <span data-ttu-id="d4731-118">此屬性會定義是否，解析程式所傳回的錯誤時，如果應該處理訊息沒有路線 (當設定為**True**) 或暫止。</span><span class="sxs-lookup"><span data-stu-id="d4731-118">This property defines whether, if an error is returned by the resolver, the message should be processed without the itinerary (when set to **True**) or suspended.</span></span>  
  
-   <span data-ttu-id="d4731-119">**ItineraryFactKey**。</span><span class="sxs-lookup"><span data-stu-id="d4731-119">**ItineraryFactKey**.</span></span> <span data-ttu-id="d4731-120">這表示，其中包含選取路線的實際 XML 解析程式所傳回之字典中索引鍵。</span><span class="sxs-lookup"><span data-stu-id="d4731-120">This represents the key in the dictionary returned by the resolver that contains the actual XML of the Itinerary selected.</span></span> <span data-ttu-id="d4731-121">一般而言， **Resolver.Itinerary**，除非您使用自訂解析程式。</span><span class="sxs-lookup"><span data-stu-id="d4731-121">Generally, **Resolver.Itinerary**, unless a custom resolver is used.</span></span>  
  
-   <span data-ttu-id="d4731-122">**ResolverConnectionString**。</span><span class="sxs-lookup"><span data-stu-id="d4731-122">**ResolverConnectionString**.</span></span> <span data-ttu-id="d4731-123">這是解析程式的連接字串，包含名稱 / 值組的解析程式可以用來選取和 （或） 查詢的路線。</span><span class="sxs-lookup"><span data-stu-id="d4731-123">This is a resolver connection string that contains name-value pairs that a resolver can use to select and/or look-up an itinerary.</span></span>