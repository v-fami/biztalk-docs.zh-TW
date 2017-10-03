---
title: "使用 TIBCO Rendezvous 接收埠從 BizTalk Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: receive ports, using from BizTalk Server
ms.assetid: 26cb20f9-4d26-48f6-a5e9-a51348a56538
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b8e0999362844570bb56cfbc488e5fd5775e286
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-tibco-rendezvous-receive-ports-from-biztalk-server"></a><span data-ttu-id="3995c-102">從 BizTalk Server 使用 TIBCO Rendezvous 接收埠</span><span class="sxs-lookup"><span data-stu-id="3995c-102">Using TIBCO Rendezvous Receive Ports from BizTalk Server</span></span>
<span data-ttu-id="3995c-103">若要使用接收埠，您可以對 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供結構描述以用於內送訊息。</span><span class="sxs-lookup"><span data-stu-id="3995c-103">To use a receive port, you can provide a schema to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for the incoming messages.</span></span> <span data-ttu-id="3995c-104">接收埠是設定來接聽特定的一組主體名稱。</span><span class="sxs-lookup"><span data-stu-id="3995c-104">A receive port is configured to listen for a particular set of subject names.</span></span> <span data-ttu-id="3995c-105">使用主體名稱搭配選擇性的萬用字元，來比對多個主體名稱。</span><span class="sxs-lookup"><span data-stu-id="3995c-105">It uses a subject name with optional wildcard characters to match multiple subject names.</span></span> <span data-ttu-id="3995c-106">您可以在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程中定義不同的連接埠作業，用於符合指定字串的每個可能主體。</span><span class="sxs-lookup"><span data-stu-id="3995c-106">You define different port operations in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration for each possible subject that matches the given string.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3995c-107">配接器支援協調流程與傳訊實例。</span><span class="sxs-lookup"><span data-stu-id="3995c-107">The Adapter supports both orchestration and messaging scenarios.</span></span>  
  
## <a name="defining-schemas"></a><span data-ttu-id="3995c-108">定義結構描述</span><span class="sxs-lookup"><span data-stu-id="3995c-108">Defining Schemas</span></span>  
 <span data-ttu-id="3995c-109">例如，如果連接埠設定為接聽主體名稱，**存貨。市場。索引。 >** ('**>**' 是萬用字元，表示任意字都正確)，它是有效的定義作業的主體名稱，例如**存貨。市場。索引。NYSE。SP500**，**存貨。市場。索引。TSX.TSX60**，依此類推。</span><span class="sxs-lookup"><span data-stu-id="3995c-109">For example, if the port is configured to listen to the subject name, **STOCK.MARKET.INDICES.>** ('**>**' is a wildcard character that means anything else to the right), it would be valid to define operations for subject names such as **STOCK.MARKET.INDICES.NYSE.SP500**, **STOCK.MARKET.INDICES.TSX.TSX60**, and so on.</span></span> <span data-ttu-id="3995c-110">配接器會產生訊息使用中所述的策略[Data Type Mapping for TIBCO Rendezvous 中的 接收處理常式](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md)，並產生根項目名稱與根據接聽的命名空間名稱和接收的訊息的主旨主體分別命名。</span><span class="sxs-lookup"><span data-stu-id="3995c-110">The adapter generates messages using the strategy described in [Data Type Mapping for Receive Handlers in TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md), and generates the root element name and namespaces based on the listen subject name and received message subject names respectively.</span></span>  
  
 <span data-ttu-id="3995c-111">在先前的範例中，配接器會為 SP500 事件產生的訊息看起來如下：</span><span class="sxs-lookup"><span data-stu-id="3995c-111">In the previous example, the adapter generates a message that looks like this for the SP500 event:</span></span>  
  
```  
<ns:STOCK.MARKET.INDICES.NYSE.SP500 xmlns:ns='   
http://schemas.microsoft.com/TibcoRendezvous/Types/  
STOCK.MARKET.INDICES.NYSE.GTWILDCARD'  
xmlns:tibrv=' http://schemas.microsoft.com/TibcoRendezvous/Types' … >  
<message body>  
</ns: STOCK.MARKET.INDICES.NYSE.SP500>  
  
```  
  
 <span data-ttu-id="3995c-112">您必須定義使用相同慣例的結構描述。</span><span class="sxs-lookup"><span data-stu-id="3995c-112">You must define a schema that uses the same conventions.</span></span> <span data-ttu-id="3995c-113">例如：</span><span class="sxs-lookup"><span data-stu-id="3995c-113">For example:</span></span>  
  
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
  
 <span data-ttu-id="3995c-114">請注意使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] **recordInfo/rootTypeName**註解。</span><span class="sxs-lookup"><span data-stu-id="3995c-114">Note the use of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**recordInfo/rootTypeName** annotation.</span></span> <span data-ttu-id="3995c-115">這會指示 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]/BizTalk 整合讓產生的 .NET Framework 類型使用該名稱，而不是包含句點的名稱。</span><span class="sxs-lookup"><span data-stu-id="3995c-115">This is to instruct the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]/BizTalk integration to use that name for the generated .NET Framework types, instead of the name that contains dots.</span></span> <span data-ttu-id="3995c-116">您可以指定任何項目。</span><span class="sxs-lookup"><span data-stu-id="3995c-116">You can specify anything.</span></span> <span data-ttu-id="3995c-117">在範例中，句點都會以底線取代。</span><span class="sxs-lookup"><span data-stu-id="3995c-117">In the examples, the dots are replaced with underscores.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3995c-118">句點會導致 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 開發工具產生無效的名稱。</span><span class="sxs-lookup"><span data-stu-id="3995c-118">The dots cause invalid names to be generated by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] development tools.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3995c-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3995c-119">See Also</span></span>  
 <span data-ttu-id="3995c-120">[資料類型對應在 TIBCO Rendezvous 接收處理常式](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md) </span><span class="sxs-lookup"><span data-stu-id="3995c-120">[Data Type Mapping for Receive Handlers in TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md) </span></span>  
 [<span data-ttu-id="3995c-121">建立 TIBCO Rendezvous 接收處理常式</span><span class="sxs-lookup"><span data-stu-id="3995c-121">Creating TIBCO Rendezvous Receive Handlers</span></span>](../core/creating-tibco-rendezvous-receive-handlers.md)