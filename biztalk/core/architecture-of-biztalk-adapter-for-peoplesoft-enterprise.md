---
title: "BizTalk Adapter for PeopleSoft Enterprise 的架構 |Microsoft 文件"
description: "描述如何接收訊息，訊息時，如何驗證，並提供元件介面方法的資訊，與 BizTalk Server 使用 PeopleSoft 配接器時"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f246e974-a082-430c-ad15-23a5e597738b
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3eb0f43dacdbd6036ef59fa3fe16102d4fe12379
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="peoplesoft-enterprise-adapter-architecture"></a><span data-ttu-id="d939c-103">PeopleSoft Enterprise 配接器架構</span><span class="sxs-lookup"><span data-stu-id="d939c-103">PeopleSoft Enterprise adapter architecture</span></span>
<span data-ttu-id="d939c-104">在 Microsoft BizTalk Adapter for PeopleSoft Enterprise 基本作業期間，配接器會從 BizTalk Server 收到 XML 訊息，</span><span class="sxs-lookup"><span data-stu-id="d939c-104">During the basic operation of Microsoft BizTalk Adapter for PeopleSoft Enterprise, the adapter receives an XML message from BizTalk Server.</span></span> <span data-ttu-id="d939c-105">然後將 XML 訊息包在 SOPA 信封中。</span><span class="sxs-lookup"><span data-stu-id="d939c-105">It encloses the XML message in a SOAP envelope.</span></span> <span data-ttu-id="d939c-106">BizTalk Adapter for PeopleSoft Enterprise 將這些 SOAP 要求轉送至伺服器。</span><span class="sxs-lookup"><span data-stu-id="d939c-106">BizTalk Adapter for PeopleSoft Enterprise forwards the SOAP requests to the server.</span></span> <span data-ttu-id="d939c-107">此配接器會使用 PeopleSoft psjoa 類別與 PeopleSoft 系統進行通訊，這些類別會透過 Jolt 傳輸通訊協定連接至 PeopleSoft 系統。</span><span class="sxs-lookup"><span data-stu-id="d939c-107">The adapter communicates with the PeopleSoft system using the PeopleSoft psjoa classes, which connect to the PeopleSoft system through Jolt Transaction Protocol.</span></span> <span data-ttu-id="d939c-108">PeopleSoft 系統收到要求，並執行商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="d939c-108">The PeopleSoft system receives the request and executes the business logic.</span></span> <span data-ttu-id="d939c-109">回覆會透過類似的程序送回。</span><span class="sxs-lookup"><span data-stu-id="d939c-109">The reply is sent back through a similar process.</span></span>  
  
 ![](../core/media/psadapter-01-architecture.gif "PSAdapter_01_Architecture")  

  
## <a name="component-interface-methods"></a><span data-ttu-id="d939c-110">元件介面方法</span><span class="sxs-lookup"><span data-stu-id="d939c-110">Component Interface Methods</span></span>  
 <span data-ttu-id="d939c-111">PeopleSoft 元件介面所提供的基本 API 本質上是低階的。</span><span class="sxs-lookup"><span data-stu-id="d939c-111">The basic APIs that are provided by the PeopleSoft component interface are low-level in nature.</span></span> <span data-ttu-id="d939c-112">用戶端需要多次叫用這些 API。</span><span class="sxs-lookup"><span data-stu-id="d939c-112">The client requires multiple invocations of these APIs.</span></span> <span data-ttu-id="d939c-113">例如，若要取得某個元件介面執行個體的屬性，用戶端需要進行一或多個呼叫來設定索引鍵值，然後再呼叫低階 Get 方法。</span><span class="sxs-lookup"><span data-stu-id="d939c-113">For example, to obtain the property of an instance of a component interface, the client needs one or more calls to set the key values followed by a low-level Get method call.</span></span> <span data-ttu-id="d939c-114">它必須接著傳送多個呼叫以取得屬性。</span><span class="sxs-lookup"><span data-stu-id="d939c-114">It must then send multiple calls to get the properties.</span></span> <span data-ttu-id="d939c-115">BizTalk Adapter for PeopleSoft Enterprise 新提供一組標準方法 (Get、Create、Find 和 Update)，讓用戶端只需要進行一次呼叫，就能達到相同的結果。</span><span class="sxs-lookup"><span data-stu-id="d939c-115">With BizTalk Adapter for PeopleSoft Enterprise, a new set of standard methods (Get, Create, Find, and Update) are provided in such a way that the client is required to make a single call to accomplish the same result.</span></span> <span data-ttu-id="d939c-116">這是讓 BizTalk Adapter for PeopleSoft Enterprise 代表用戶端執行多次呼叫來達成。</span><span class="sxs-lookup"><span data-stu-id="d939c-116">You do this by having BizTalk Adapter for PeopleSoft Enterprise perform multiple calls on behalf of the client.</span></span> <span data-ttu-id="d939c-117">如需這類方法的詳細資訊，請參閱[附錄 a： 元件介面方法](../core/appendix-a-component-interface-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="d939c-117">For more information about the methods, see [Appendix A: Component Interface Methods](../core/appendix-a-component-interface-methods.md).</span></span>  
  
 <span data-ttu-id="d939c-118">為了建立 PeopleSoft 的結構描述，BizTalk Adapter for PeopleSoft Enterprise 會擷取 PeopleSoft 元件介面定義或中繼資料。</span><span class="sxs-lookup"><span data-stu-id="d939c-118">To create a schema for PeopleSoft, BizTalk Adapter for PeopleSoft Enterprise retrieves the PeopleSoft component interface definitions or metadata.</span></span>  
  
 <span data-ttu-id="d939c-119">BizTalk Adapter for PeopleSoft Enterprise 是以傳送功能的元件介面為基礎，不需要使用 PeopleSoft Integration Broker。</span><span class="sxs-lookup"><span data-stu-id="d939c-119">BizTalk Adapter for PeopleSoft Enterprise is based on component interfaces for the Send functionality and does not require the PeopleSoft Integration Broker.</span></span> <span data-ttu-id="d939c-120">這些元 件介面會公開為可從 BizTalk Server 存取的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="d939c-120">The component interfaces are exposed as Web services, which can be accessed from BizTalk Server.</span></span>  
  
### <a name="validation"></a><span data-ttu-id="d939c-121">驗證</span><span class="sxs-lookup"><span data-stu-id="d939c-121">Validation</span></span>  
 <span data-ttu-id="d939c-122">BizTalk Adapter for PeopleSoft Enterprise 從 BizTalk Server 收到 XML 訊息時，會執行兩個層級的驗證：</span><span class="sxs-lookup"><span data-stu-id="d939c-122">When BizTalk Adapter for PeopleSoft Enterprise receives an XML message from BizTalk Server, two levels of validation are performed:</span></span>  
  
-   <span data-ttu-id="d939c-123">XML 訊息必須符合相關 XML 規格。</span><span class="sxs-lookup"><span data-stu-id="d939c-123">The XML message must be valid with regard to XML specification.</span></span>  
  
-   <span data-ttu-id="d939c-124">XML 訊息必須符合特定 Web 服務的要求 (例如，如資料型別之類的介面比對)。</span><span class="sxs-lookup"><span data-stu-id="d939c-124">The XML message must match what is required by the specific Web service (for example, interface matching such as data types).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d939c-125">不會有商務邏輯方面的驗證 (這是 PeopleSoft 系統的領域，BizTalk Adapter for PeopleSoft Enterprise 可清楚辨認該驗證)。</span><span class="sxs-lookup"><span data-stu-id="d939c-125">There is no validation with regard to business logic, which is the domain of the PeopleSoft system, and is transparent to BizTalk Adapter for PeopleSoft Enterprise.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d939c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d939c-126">See Also</span></span>  
 [<span data-ttu-id="d939c-127">快速入門</span><span class="sxs-lookup"><span data-stu-id="d939c-127">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-peoplesoft-enterprise.md)   