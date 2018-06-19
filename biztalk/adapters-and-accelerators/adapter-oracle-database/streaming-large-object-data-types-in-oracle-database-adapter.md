---
title: 資料流處理大型物件資料類型在 Oracle 資料庫配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- streaming, support in the WCF service model
- streaming, support for
- streaming, support in BizTalk Server
- streaming, support in the WCF channel model
ms.assetid: c6cbe870-6794-4bf1-90c1-db65a242e8fe
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fda4d99eb381321139e4ed493f119f9eaf21623e
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "22217910"
---
# <a name="streaming-large-object-data-types-in-oracle-database-adapter"></a>Oracle 資料庫配接器中的資料流處理大型物件資料類型
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]支援 Oracle 大型物件 (LOB) 資料類型的串流。 與[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]叫用作業，並藉由交換 SOAP 訊息會傳回回應。 將 SOAP 訊息本文所組成的 XML 節點。  
  
 有兩種類型的訊息資料流配接器所支援：  
  
-   **節點資料流**。 中的節點資料流的每個節點是經過緩衝處理配接器傳送到 Oracle 資料庫之前 （或傳回給用戶端）。 這表示，LOB 資料類型，完整的值讀取到緩衝區。  
  
-   **節點值的資料流**。 節點值的資料流處理之節點的實際值進行串流處理 Oracle 資料庫與用戶端之間的區塊 （chunk）。 節點值串流處理支援端對端的資料流的配接器用戶端與 Oracle 資料庫之間的 LOB 資料類型。  
  
 這兩種資料流模式會依賴資料流處理的節點和節點值上 WCF 中的訊息資料流的支援。 基於這個理由，LOB 類型的資料流繫結緊密如何建立和使用配接器和用戶端應用程式訊息。 其結果之一是，支援資料流 LOB 類型不相同跨所有的程式設計模型。  
  
 本主題中的各節提供：  
  
-   在 WCF 中的訊息資料流支援如何以及如何實作由配接器的基本的背景資訊。  
  
-   如何支援資料流的 LOB 資料類型是當您在每個程式撰寫模型中使用配接器的相關資訊。  
  
## <a name="streaming-fundamentals"></a>資料流的基本概念  
 支援資料流實作[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]的組合：  
  
-   在 WCF 中的訊息資料流支援。  
  
-   資料流中的 Oracle 用戶端程式庫 (ODP.NET) 的支援。  
  
-   訊息的方式建立和配接器在內部使用。  
  
### <a name="message-streaming-support-in-wcf"></a>在 WCF 中的訊息資料流支援  
 WCF 支援資料流處理訊息的方式取決於訊息的建立方式以及如何使用訊息。  
  
-   WCF 訊息由使用靜態**建立**方法**System.ServiceModel.Channels.Message**。 這個方法有數個多載可支援不同的方式傳遞的訊息本文。 您可以藉由傳遞訊息本文會使用建立 WCF 訊息：  
  
    -   A **System.Xml.XmlReader**，或  
  
    -   A **System.ServiceModel.Channels.BodyWriter**。  
  
-   可以使用取用 WCF 訊息  
  
    -   An **XmlReader** by calling **Message.GetReaderAtBodyContents()**, or  
  
    -   **XmlDictionaryWriter**藉由呼叫**Message.WriteBodyContents(XmlDictionaryWriter)**。  
  
 下表顯示不同的組合，建立及取用訊息的 WCF 行為的方式。  
  
|建立使用訊息|與取用訊息|WCF 行為|  
|--------------------------|---------------------------|------------------|  
|**XmlBodyWriter**|**XmlDictionaryWriter**|**節點值的資料流**支援。 WCF 會經由管道一起，以啟用資料流的兩個寫入器。 這兩個**XmlBodyWriter**和**XmlDictionaryWriter**必須支援的節點值的資料流處理發生這個問題。|  
|**XmlBodyWriter**|**XmlReader**|**節點資料流**支援。 WCF 在內部緩衝區**XmlReader**。|  
|**XmlReader**|**XmlDictionaryWriter**|**節點資料流**支援。 WCF 在內部緩衝區**XmlReader**並回呼至**XmlDictionaryWriter**。|  
|**XmlReader**|**XmlReader**|**節點資料流**支援。 WCF 在內部緩衝區**XmlReader**。|  
  
### <a name="streaming-support-in-the-oracle-client-library-odpnet"></a>Oracle 用戶端程式庫 (ODP.NET) 中的資料流支援  
 ODP.NET 支援串流以下列方式：  
  
-   只有在 Oracle LOB 資料型別上支援資料流。  
  
-   對於某些資料表 （及檢視） 的作業，緩衝處理 LOB 資料類型。 因此，不支援資料流。  
  
### <a name="internal-message-handling-by-the-adapter"></a>內部訊息處理配接器  
 配接器支援串流以下列方式：  
  
-   配接器擴充**訊息**來實作自訂訊息類別， **Microsoft.Adapters.AdapterUtilities.AdapterMessage**。 它會建立**AdapterMessage**所有 WCF 訊息，它會提供給配接器用戶端，包括所有輸出作業的回應訊息和 POLLINGSTMT 作業的要求訊息。 這可讓配接器以支援資料流 ReadLOB 作業，藉由提供節點值**XmlReader**支援**ReadValueChunk**配接器用戶端。  
  
-   配接器使用接收從用戶端使用的自訂實作的所有訊息**XmlDictionaryWriter**。  
  
-   配接器會建立所有的訊息傳送至用戶端使用的自訂實作**XmlBodyWriter**，除了 ReadLOB 回應訊息。 （這包括所有輸出作業的回應訊息和 POLLINGSTMT 作業的要求訊息）。  
  
## <a name="streaming-support-in-the-wcf-channel-model"></a>WCF 通道模型中的資料流支援  
 下表提供有關如何支援資料流中的 WCF 通道模型的詳細的資訊。  
  
|運算|節點資料流|節點值的資料流|Description|  
|---------------|--------------------|---------------------------|-----------------|  
|資料表的 Insert 作業|支援*|不支援 Oracle 資料庫配接器之間。 支援用戶端與 adapter.* 之間|不支援端對端的節點值資料流處理，因為 LOB 資料行的值由 ODP.NET 緩衝，則會執行插入。 但是，有可能 LOB 資料行，如果用戶端會建立訊息與節點值的資料流的用戶端與配接器之間**BodyWriter**。|  
|選取的資料表作業|Supported|Supported|配接器使用**BodyWriter**建立回應訊息。 如果在用戶端取用訊息使用**XmlDictionaryWriter**，節點值的資料流處理 LOB 資料行，就會發生。|  
|資料表更新作業|Supported|不支援 Oracle 資料庫配接器之間。 支援用戶端與配接器之間。|因為 LOB 資料行的值會由 ODP.NET 進行緩衝處理，然後執行更新時，不支援端對端的節點值資料流。 不過，節點值的資料流的用戶端與配接器之間可能是 LOB 資料行如果用戶端會建立使用訊息**BodyWriter**。|  
|資料表刪除作業|Supported|不支援 Oracle 資料庫配接器之間。 支援用戶端與配接器之間。|不支援端對端的節點值資料流處理，因為 LOB 資料行的值會緩衝 ODP.NET 和接著執行 delete。 不過，節點值的資料流的用戶端與配接器之間可能是 LOB 資料行如果用戶端會建立使用訊息**BodyWriter**。|  
|資料表 ReadLOB 作業|Supported|Supported|ReadLOB 作業主要被設計來在 WCF 服務模型中的資料流 LOB 資料行。 在 WCF 通道模型中，如果在用戶端取用訊息使用**XmlReader** (藉由叫用**GetReaderAtBodyContents**回應訊息上的方法)，端對端的節點值的資料流，就會發生。 這是因為配接器傳回**XmlReader**支援**ReadValueChunk**呼叫 ReadLOB 回應訊息。 不過，建議您不要使用 WCF 通道模型的 ReadLOB 作業。 您可以改用選取作業或 SQLEXECUTE 操作。|  
|資料表 UpdateLOB 作業|Supported|Supported|配接器使用**XmlDictionaryWriter**使用要求訊息。 如果用戶端使用**BodyWriter**若要建立要求訊息，端對端的節點值的 LOB 資料串流，就會發生。|  
|SQLEXECUTE 操作|Supported|Supported|配接器使用**BodyWriter**建立回應訊息。<br /><br /> 如果用戶端使用**XmlDictionaryWriter**取用回應訊息，端對端的節點值的 LOB 資料串流，就會發生。<br /><br /> 因為配接器必須緩衝所有運算元，它可以叫用 Oracle 資料庫上的作業之前端對端的節點值資料流不支援要求訊息。|  
|預存程序和函式的作業|Supported|Supported|配接器使用**BodyWriter**建立回應訊息。<br /><br /> 如果用戶端使用**XmlDictionaryWriter**取用回應訊息，端對端的節點值的 LOB 資料串流，就會發生。 (這表示資料流支援，以及在出程序及函式參數來回應訊息中的。)<br /><br /> 因為配接器必須緩衝所有運算元，它可以叫用 Oracle 資料庫上的作業之前端對端的節點值資料流不支援要求訊息。|  
|POLLINGSTMT 作業|Supported|Supported|配接器使用**BodyWriter**建立 POLLINGSTMT 要求訊息。 如果在用戶端取用訊息使用**XmlDictionaryWriter**，則會發生節點值的資料流處理 LOB 資料行。|  
  
 如需如何實作 LOB 資料流在程式碼中，當您使用 WCF 通道模型的資訊，請參閱[串流處理 Oracle 資料庫的 LOB 資料類型使用 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md)。  
  
## <a name="streaming-support-in-the-wcf-service-model"></a>WCF 服務模型中的資料流支援  
 序列化和還原序列化訊息的 XML 表示法之間的 managed 程式碼的物件表示該訊息需要寫入和讀取到記憶體中的整個訊息。 基於這個理由，資料流處理的節點和節點值的資料流都不支援大部分的作業。  
  
 唯一的例外是 ReadLOB 作業。 這項作業被實作是特別為了支援端對端的資料流讀取 WCF 服務模型中的資料表和檢視表 LOB 資料行。  
  
## <a name="streaming-support-in-biztalk-server"></a>BizTalk Server 中的資料流支援  
 下表提供有關 BizTalk Server 中的資料流支援方式的詳細的資訊。 (請參閱 「 介面卡 」 的所有參考[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; Wcf-custom 配接器永遠都有其完整名稱，此資料表中。)  
  
|運算|節點資料流|節點值的資料流|Description|  
|---------------|--------------------|---------------------------|-----------------|  
|資料表的 Insert 作業|支援*|不支援配接器與 Oracle 資料庫之間。不過，BizTalk Server 與配接器之間的資料是資料流。|不支援端對端的節點值資料流處理，因為 LOB 資料行的值由 ODP.NET 緩衝，則會執行插入。 不過，節點值的資料流處理 BizTalk Server 與配接器之間支援的 LOB 資料類型因為 Wcf-custom 配接器會建立使用訊息**BodyWriter**。|  
|選取的資料表作業|Supported|Supported|Wcf-custom 配接器會使用**XmlDictionaryWriter**取用回應訊息，因此，才支援端對端的節點值 LOB 類型的串流。|  
|資料表更新作業|Supported|不支援配接器與 Oracle 資料庫之間。不過，BizTalk Server 與配接器之間的資料是資料流。|因為 LOB 資料行的值會由 ODP.NET 進行緩衝處理，然後執行更新時，不支援端對端的節點值資料流。 不過，節點值的資料流處理 BizTalk Server 與配接器之間支援的 LOB 資料類型因為 Wcf-custom 配接器會建立使用訊息**BodyWriter**。|  
|資料表刪除作業|Supported|不支援配接器與 Oracle 資料庫之間。不過，BizTalk Server 與配接器之間的資料是資料流。|不支援端對端的節點值資料流處理，因為 LOB 資料行的值會緩衝 ODP.NET 和接著執行 delete。 不過，節點值的資料流處理 BizTalk Server 與配接器之間支援的 LOB 資料類型因為 Wcf-custom 配接器會建立使用訊息**BodyWriter**。|  
|資料表 ReadLOB 作業|BizTalk Server 不支援 ReadLOB 作業。|BizTalk Server 不支援 ReadLOB 作業。|BizTalk Server 不支援 ReadLOB 作業。 相反地，請使用選取的作業或 SQLEXECUTE 操作。|  
|資料表 UpdateLOB 作業|Supported|Supported|Wcf-custom 配接器會使用**BodyWriter**來建立要求訊息，因此支援端對端節點值 LOB 資料類型的串流。|  
|SQLEXECUTE 操作|Supported|Supported|Wcf-custom 配接器會使用**XmlDictionaryWriter**取用回應訊息，因此，才支援端對端的節點值資料流處理回應訊息中的 LOB 資料類型。<br /><br /> 因為配接器必須緩衝所有運算元，它可以叫用 Oracle 資料庫上的作業之前端對端的節點值資料流不支援要求訊息。|  
|預存程序和函式的作業|Supported|Supported|Wcf-custom 配接器會使用**XmlDictionaryWriter**取用回應訊息，因此，才支援端對端的節點值資料流處理回應訊息中的 LOB 資料類型。 (這表示資料流支援，以及在出程序及函式參數來回應訊息中的。)<br /><br /> 因為配接器必須緩衝所有運算元，它可以叫用 Oracle 資料庫上的作業之前端對端的節點值資料流不支援要求訊息。|  
|POLLINGSTMT 作業|Supported|Supported|Wcf-custom 配接器會使用**XmlDictionaryWriter**取用 （輸入） 的要求訊息，因此，才支援端對端的節點值 LOB 資料類型的串流。|  
  
## <a name="see-also"></a>另請參閱  
[開發您的 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)