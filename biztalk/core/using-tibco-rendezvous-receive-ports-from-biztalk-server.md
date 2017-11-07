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
# <a name="using-tibco-rendezvous-receive-ports-from-biztalk-server"></a>從 BizTalk Server 使用 TIBCO Rendezvous 接收埠

## <a name="overview"></a>概觀
若要使用接收埠，您可以對 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供結構描述以用於內送訊息。 接收埠是設定來接聽特定的一組主體名稱。 使用主體名稱搭配選擇性的萬用字元，來比對多個主體名稱。 您可以在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程中定義不同的連接埠作業，用於符合指定字串的每個可能主體。  
  
> [!NOTE]
>  配接器支援協調流程與傳訊實例。  
  
## <a name="define-schemas"></a>定義結構描述  
 例如，如果連接埠設定為接聽主體名稱，**存貨。市場。索引。 >** ('**>**' 是萬用字元，表示任意字都正確)，它是有效的定義作業的主體名稱，例如**存貨。市場。索引。NYSE。SP500**，**存貨。市場。索引。TSX.TSX60**，依此類推。 配接器會產生訊息使用中所述的策略[Data Type Mapping for TIBCO Rendezvous 中的 接收處理常式](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md)，並產生根項目名稱與根據接聽的命名空間名稱和接收的訊息的主旨主體分別命名。  
  
 在上述範例中，配接器會產生看起來像下列的 SP500 事件訊息：  
  
```  
<ns:STOCK.MARKET.INDICES.NYSE.SP500 xmlns:ns='   
http://schemas.microsoft.com/TibcoRendezvous/Types/  
STOCK.MARKET.INDICES.NYSE.GTWILDCARD'  
xmlns:tibrv=' http://schemas.microsoft.com/TibcoRendezvous/Types' … >  
<message body>  
</ns: STOCK.MARKET.INDICES.NYSE.SP500>  
  
```  
  
 您必須定義使用相同慣例的結構描述。 例如：  
  
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
  
 請注意使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] **recordInfo/rootTypeName**註解。 這會指示 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]/BizTalk 整合讓產生的 .NET Framework 類型使用該名稱，而不是包含句點的名稱。 您可以指定任何項目。 在範例中，句點都會以底線取代。  
  
> [!NOTE]
>  句點會導致 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 開發工具產生無效的名稱。  

## <a name="event-processing"></a>事件處理
Microsoft BizTalk Adapter for TIBCO Rendezvous 會分派事件，從多個執行緒上的佇列。 BizTalk Server 接收位置與一個 TIBCO Rendezvous 事件佇列和它的發送器執行緒的集區相關聯。  
  
### <a name="memory-use-and-errors"></a>記憶體用量與錯誤  
 處理事件時，配接器會監看使用的資源。 如果記憶體用量超過配額上限，配接器會停止發送事件，直到回到記憶體用量配額下限為止。 請注意，這樣可能會導致遺漏非保證訊息的 TIBCO Rendezvous 訊息 (TIBCO RV 取用者有 60 秒的時間可移除佇列中的訊息)。 遺失此資料會報告為錯誤。 如果配接器收到 TIBCO Rendezvous 系統通報 NO_MEMORY 訊息，表示訊息已經遺失。  
  
 BizTalk Adapter for TIBCO Rendezvous 會維護狀態，並依據該狀態以不同的方式執行工作。 如果 BizTalk 訊息引擎報告錯誤，且配接器設為保證的接聽程式，它會向 TIBCO Rendezvous 報告錯誤，藉此重新提交訊息。  
  
## <a name="see-also"></a>另請參閱  
 [TIBCO Rendezvous 概念](../core/tibco-rendezvous-concepts.md)   
 [資料類型對應在 TIBCO Rendezvous 接收處理常式](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md)   
 [建立 TIBCO Rendezvous 接收處理常式](../core/creating-tibco-rendezvous-receive-handlers.md)