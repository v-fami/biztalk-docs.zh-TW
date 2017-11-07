---
title: "接收結構描述和處理事件的 TIBCO Rendezvous 配接器 |Microsoft 文件"
description: "使用 TIBCO Rendezvous 結構描述，在接收端，而使用 BizTalk Adapter for TIBCO Rendezvous 在 BizTalk 中的事件處理"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26cb20f9-4d26-48f6-a5e9-a51348a56538
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bbbae69dc1b7df1f5675442dde544a444cec02fb
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="using-tibco-rendezvous-receive-ports-from-biztalk-server"></a><span data-ttu-id="67f9f-103">從 BizTalk Server 使用 TIBCO Rendezvous 接收埠</span><span class="sxs-lookup"><span data-stu-id="67f9f-103">Using TIBCO Rendezvous Receive Ports from BizTalk Server</span></span>

## <a name="overview"></a><span data-ttu-id="67f9f-104">概觀</span><span class="sxs-lookup"><span data-stu-id="67f9f-104">Overview</span></span>
<span data-ttu-id="67f9f-105">若要使用接收埠，您可以對 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供結構描述以用於內送訊息。</span><span class="sxs-lookup"><span data-stu-id="67f9f-105">To use a receive port, you can provide a schema to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for the incoming messages.</span></span> <span data-ttu-id="67f9f-106">接收埠是設定來接聽特定的一組主體名稱。</span><span class="sxs-lookup"><span data-stu-id="67f9f-106">A receive port is configured to listen for a particular set of subject names.</span></span> <span data-ttu-id="67f9f-107">使用主體名稱搭配選擇性的萬用字元，來比對多個主體名稱。</span><span class="sxs-lookup"><span data-stu-id="67f9f-107">It uses a subject name with optional wildcard characters to match multiple subject names.</span></span> <span data-ttu-id="67f9f-108">您可以在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程中定義不同的連接埠作業，用於符合指定字串的每個可能主體。</span><span class="sxs-lookup"><span data-stu-id="67f9f-108">You define different port operations in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration for each possible subject that matches the given string.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67f9f-109">配接器支援協調流程與傳訊實例。</span><span class="sxs-lookup"><span data-stu-id="67f9f-109">The adapter supports both orchestration and messaging scenarios.</span></span>  
  
## <a name="define-schemas"></a><span data-ttu-id="67f9f-110">定義結構描述</span><span class="sxs-lookup"><span data-stu-id="67f9f-110">Define schemas</span></span>  
 <span data-ttu-id="67f9f-111">例如，如果連接埠設定為接聽主體名稱，**存貨。市場。索引。 >** ('**>**' 是萬用字元，表示任意字都正確)，它是有效的定義作業的主體名稱，例如**存貨。市場。索引。NYSE。SP500**，**存貨。市場。索引。TSX.TSX60**，依此類推。</span><span class="sxs-lookup"><span data-stu-id="67f9f-111">For example, if the port is configured to listen to the subject name, **STOCK.MARKET.INDICES.>** ('**>**' is a wildcard character that means anything else to the right), it would be valid to define operations for subject names such as **STOCK.MARKET.INDICES.NYSE.SP500**, **STOCK.MARKET.INDICES.TSX.TSX60**, and so on.</span></span> <span data-ttu-id="67f9f-112">配接器會產生訊息使用中所述的策略[Data Type Mapping for TIBCO Rendezvous 中的 接收處理常式](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md)，並產生根項目名稱與根據接聽的命名空間名稱和接收的訊息的主旨主體分別命名。</span><span class="sxs-lookup"><span data-stu-id="67f9f-112">The adapter generates messages using the strategy described in [Data Type Mapping for Receive Handlers in TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md), and generates the root element name and namespaces based on the listen subject name and received message subject names respectively.</span></span>  
  
 <span data-ttu-id="67f9f-113">在上述範例中，配接器會產生看起來像下列的 SP500 事件訊息：</span><span class="sxs-lookup"><span data-stu-id="67f9f-113">In the previous example, the adapter generates a message that looks like the following for the SP500 event:</span></span>  
  
```  
<ns:STOCK.MARKET.INDICES.NYSE.SP500 xmlns:ns='   
http://schemas.microsoft.com/TibcoRendezvous/Types/  
STOCK.MARKET.INDICES.NYSE.GTWILDCARD'  
xmlns:tibrv=' http://schemas.microsoft.com/TibcoRendezvous/Types' … >  
<message body>  
</ns: STOCK.MARKET.INDICES.NYSE.SP500>  
  
```  
  
 <span data-ttu-id="67f9f-114">您必須定義使用相同慣例的結構描述。</span><span class="sxs-lookup"><span data-stu-id="67f9f-114">You must define a schema that uses the same conventions.</span></span> <span data-ttu-id="67f9f-115">例如：</span><span class="sxs-lookup"><span data-stu-id="67f9f-115">For example:</span></span>  
  
```  
<xsd:schema  
targetNamespace='   
  
http://schemas.microsoft.com/TibcoRendezvous/Types/STOCK.MARKET.INDICES.N  
YSE.GTWILDCARD'  
xmlns:xsd=' http://www.w3.org/2001/XMLSchema'  
xmlns:tibrv=' http://schemas.microsoft.com/TibcoRendezvous/Types'>  
xmlns:b="http://schemas.microsoft.com/BizTalk/2003"  
<xsd:element name='STOCK.MARKET.INDICES.NYSE.SP500'>  
  
 <xs:annotation>  
   <xs:appinfo>  
     <b:recordInfo rootTypeName="STOCK_MARKET_INDICES_NYSE_SP500" />  
   </xs:appinfo>  
  
 </xs:annotation>  
<xsd:complexType>  
<SP500 message definitions goes here>  
</xsd:complexType>  
<xsd:element name='STOCK.MARKET.INDICES.TSX.TSX60'>  
  
 <xs:annotation>  
   <xs:appinfo>  
     <b:recordInfo rootTypeName="STOCK_MARKET_INDICES_TSX_TSX60" />  
   </xs:appinfo>  
  
 </xs:annotation>  
<xsd:complexType>  
<TSX60 message definitions goes here>  
</xsd:complexType>  
  
```  
  
 <span data-ttu-id="67f9f-116">請注意使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] **recordInfo/rootTypeName**註解。</span><span class="sxs-lookup"><span data-stu-id="67f9f-116">Note the use of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**recordInfo/rootTypeName** annotation.</span></span> <span data-ttu-id="67f9f-117">這會指示 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]/BizTalk 整合讓產生的 .NET Framework 類型使用該名稱，而不是包含句點的名稱。</span><span class="sxs-lookup"><span data-stu-id="67f9f-117">This is to instruct the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]/BizTalk integration to use that name for the generated .NET Framework types, instead of the name that contains dots.</span></span> <span data-ttu-id="67f9f-118">您可以指定任何項目。</span><span class="sxs-lookup"><span data-stu-id="67f9f-118">You can specify anything.</span></span> <span data-ttu-id="67f9f-119">在範例中，句點都會以底線取代。</span><span class="sxs-lookup"><span data-stu-id="67f9f-119">In the examples, the dots are replaced with underscores.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67f9f-120">句點會導致 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 開發工具產生無效的名稱。</span><span class="sxs-lookup"><span data-stu-id="67f9f-120">The dots cause invalid names to be generated by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] development tools.</span></span>  

## <a name="event-processing"></a><span data-ttu-id="67f9f-121">事件處理</span><span class="sxs-lookup"><span data-stu-id="67f9f-121">Event processing</span></span>
<span data-ttu-id="67f9f-122">Microsoft BizTalk Adapter for TIBCO Rendezvous 會分派事件，從多個執行緒上的佇列。</span><span class="sxs-lookup"><span data-stu-id="67f9f-122">Microsoft BizTalk Adapter for TIBCO Rendezvous dispatches events from a queue on multiple threads.</span></span> <span data-ttu-id="67f9f-123">BizTalk Server 接收位置與一個 TIBCO Rendezvous 事件佇列和它的發送器執行緒的集區相關聯。</span><span class="sxs-lookup"><span data-stu-id="67f9f-123">A BizTalk Server receive location is associated with one TIBCO Rendezvous event queue, and its pool of dispatcher threads.</span></span>  
  
### <a name="memory-use-and-errors"></a><span data-ttu-id="67f9f-124">記憶體用量與錯誤</span><span class="sxs-lookup"><span data-stu-id="67f9f-124">Memory Use and Errors</span></span>  
 <span data-ttu-id="67f9f-125">處理事件時，配接器會監看使用的資源。</span><span class="sxs-lookup"><span data-stu-id="67f9f-125">While processing events, the adapter keeps an eye on used resources.</span></span> <span data-ttu-id="67f9f-126">如果記憶體用量超過配額上限，配接器會停止發送事件，直到回到記憶體用量配額下限為止。</span><span class="sxs-lookup"><span data-stu-id="67f9f-126">If memory use goes above the high-watermark, the adapter stops dispatching events until it reaches the low-watermark memory consumption.</span></span> <span data-ttu-id="67f9f-127">請注意，這樣可能會導致遺漏非保證訊息的 TIBCO Rendezvous 訊息 (TIBCO RV 取用者有 60 秒的時間可移除佇列中的訊息)。</span><span class="sxs-lookup"><span data-stu-id="67f9f-127">Note that this might result in TIBCO Rendezvous messages being missed for non certified messages (a TIBCO RV consumer has 60 seconds to remove messages from a queue).</span></span> <span data-ttu-id="67f9f-128">遺失此資料會報告為錯誤。</span><span class="sxs-lookup"><span data-stu-id="67f9f-128">This data loss is reported as an error.</span></span> <span data-ttu-id="67f9f-129">如果配接器收到 TIBCO Rendezvous 系統通報 NO_MEMORY 訊息，表示訊息已經遺失。</span><span class="sxs-lookup"><span data-stu-id="67f9f-129">If the adapter receives a TIBCO Rendezvous system advisory NO_MEMORY message, messages have already been lost.</span></span>  
  
 <span data-ttu-id="67f9f-130">BizTalk Adapter for TIBCO Rendezvous 會維護狀態，並依據該狀態以不同的方式執行工作。</span><span class="sxs-lookup"><span data-stu-id="67f9f-130">BizTalk Adapter for TIBCO Rendezvous maintains a state, and it executes tasks differently based on that state.</span></span> <span data-ttu-id="67f9f-131">如果 BizTalk 訊息引擎報告錯誤，且配接器設為保證的接聽程式，它會向 TIBCO Rendezvous 報告錯誤，藉此重新提交訊息。</span><span class="sxs-lookup"><span data-stu-id="67f9f-131">If the BizTalk Message Engine reports an error, and the adapter is configured to be a certified listener, it reports the error to TIBCO Rendezvous so that it can resubmit the message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67f9f-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67f9f-132">See Also</span></span>  
 <span data-ttu-id="67f9f-133">[TIBCO Rendezvous 概念](../core/tibco-rendezvous-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="67f9f-133">[TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md) </span></span>  
 <span data-ttu-id="67f9f-134">[資料類型對應在 TIBCO Rendezvous 接收處理常式](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md) </span><span class="sxs-lookup"><span data-stu-id="67f9f-134">[Data Type Mapping for Receive Handlers in TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md) </span></span>  
 [<span data-ttu-id="67f9f-135">建立 TIBCO Rendezvous 接收處理常式</span><span class="sxs-lookup"><span data-stu-id="67f9f-135">Creating TIBCO Rendezvous Receive Handlers</span></span>](../core/creating-tibco-rendezvous-receive-handlers.md)