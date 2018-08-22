---
title: 串流大型物件資料類型在 Oracle 資料庫配接器 |Microsoft Docs
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
ms.openlocfilehash: af0e81c5e2430dad50090637069713680c900d13
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994111"
---
# <a name="streaming-large-object-data-types-in-oracle-database-adapter"></a>Oracle 資料庫配接器中的資料流處理大型物件資料類型
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]支援串流處理 Oracle 大型物件 (LOB) 資料類型。 使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]叫用作業，並藉由交換的 SOAP 訊息會傳回回應。 SOAP 訊息內文包含的 XML 節點。  
  
 有兩種類型的訊息資料流所支援的配接器：  
  
- **節點資料流**。 中的節點資料流的每個節點是經過緩衝處理由配接器傳送到 Oracle 資料庫之前 （或傳回給用戶端）。 這表示，對於 LOB 資料類型，完整的值讀取到緩衝區。  
  
- **節點值串流**。 節點值可以在 Oracle 資料庫與用戶端之間的區塊串流串流處理之節點的實際值。 節點值的資料流支援的 LOB 資料類型的配接器用戶端與 Oracle 資料庫之間的端對端資料流。  
  
  這兩個資料流模式依賴支援串流處理的節點和節點值的資料流處理 WCF 中的訊息。 基於這個理由，LOB 類型的串流會繫結緊密訊息建立與取用配接器和用戶端應用程式的方式。 這麼做的結果是，串流 LOB 類型不支援相同跨所有的程式設計模型。  
  
  本主題中的各節提供：  
  
- 如何在 WCF 中支援訊息資料流是和配接器的實作方式的基本的背景資訊。  
  
- 如何支援資料流 LOB 資料類型的每個程式設計模型中使用配接器時的相關資訊。  
  
## <a name="streaming-fundamentals"></a>資料流的基本概念  
 支援資料流實作[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]組成：  
  
-   在 WCF 中的訊息資料流支援。  
  
-   資料流中的 Oracle 用戶端程式庫 (ODP.NET) 的支援。  
  
-   訊息的方式建立，並在內部由配接器。  
  
### <a name="message-streaming-support-in-wcf"></a>在 WCF 中的訊息資料流支援  
 WCF 支援資料流處理訊息的方式取決於訊息的建立方式和訊息的使用方式。  
  
- WCF 訊息由使用靜態**Create**方法**System.ServiceModel.Channels.Message**。 這個方法有數個多載可支援不同的方式傳遞的訊息本文。 您可以藉由傳遞訊息本文會使用建立 WCF 訊息：  
  
  -   A **System.Xml.XmlReader**，或  
  
  -   A **System.ServiceModel.Channels.BodyWriter**。  
  
- WCF 訊息可供使用  
  
  -   **XmlReader**藉由呼叫**Message.GetReaderAtBodyContents()**，或  
  
  -   **XmlDictionaryWriter**藉由呼叫**Message.WriteBodyContents(XmlDictionaryWriter)**。  
  
  下表顯示不同的組合，建立和取用訊息的 WCF 行為的方式。  
  
|建立與訊息|與取用的訊息|WCF 行為|  
|--------------------------|---------------------------|------------------|  
|**XmlBodyWriter**|**XmlDictionaryWriter**|**節點值串流**支援。 WCF 會使用管線傳送，以達到資料流的兩個寫入器。 這兩個**XmlBodyWriter**並**XmlDictionaryWriter**必須支援這個節點值才會發生資料流。|  
|**XmlBodyWriter**|**XmlReader**|**節點資料流**支援。 WCF 會在內部緩衝**XmlReader**。|  
|**XmlReader**|**XmlDictionaryWriter**|**節點資料流**支援。 WCF 會在內部緩衝**XmlReader**並回呼至**XmlDictionaryWriter**。|  
|**XmlReader**|**XmlReader**|**節點資料流**支援。 WCF 會在內部緩衝**XmlReader**。|  
  
### <a name="streaming-support-in-the-oracle-client-library-odpnet"></a>Oracle 用戶端程式庫 (ODP.NET) 中的資料流支援  
 ODP.NET 支援串流以下列方式：  
  
-   支援只在 Oracle LOB 資料類型上的資料流。  
  
-   對於某些資料表 （及檢視） 的作業，LOB 資料類型會進行緩衝處理。 因此，不支援資料流。  
  
### <a name="internal-message-handling-by-the-adapter"></a>內部配接器所處理的訊息  
 配接器支援串流以下列方式：  
  
-   配接器延伸**訊息**若要實作自訂訊息類別， **Microsoft.Adapters.AdapterUtilities.AdapterMessage**。 它會建立**AdapterMessage**的所有 WCF 都訊息，它會提供給配接器用戶端，包括所有的輸出作業的回應都訊息和 POLLINGSTMT 作業的要求訊息。 序列化和還原序列化訊息的 XML 表示法與該訊息的 managed 程式碼物件表示法之間需要寫入和讀取整個訊息載入記憶體。  
  
-   基於這個理由，資料流處理的節點和節點值的資料流都不支援大部分的作業。  
  
-   唯一的例外是 ReadLOB 作業。 這項作業是專為支援端對端資料流來讀取資料表和檢視表的 LOB 資料行中的 WCF 服務模型的實作。  
  
## <a name="streaming-support-in-the-wcf-channel-model"></a>在 BizTalk Server 中的資料流支援  
 下表提供有關如何在 BizTalk Server 中支援資料流時的詳細的資訊。  
  
|作業|(請參閱 「 介面卡 」 的所有參考; Wcf-custom 配接器永遠都有其完整名稱，此資料表中。)|不支援配接器與 Oracle 資料庫之間;不過，BizTalk Server 與配接器之間串流資料。|描述|  
|---------------|--------------------|---------------------------|-----------------|  
|不支援端對端節點值串流處理，因為 ODP.NET 會緩衝處理 LOB 資料行的值，並接著執行 insert。|支援*|不過，BizTalk Server 與配接器之間的資料流處理的節點值支援 LOB 資料類型的因為 Wcf-custom 配接器會建立與訊息BodyWriter。 Wcf-custom 配接器會使用XmlDictionaryWriter取用回應訊息，因此支援端對端節點值串流 LOB 類型。|因為 ODP.NET 會緩衝處理 LOB 資料行的值，然後執行更新時，不支援端對端節點值資料流。 BizTalk Server 不支援 ReadLOB 作業。|  
|相反地，請使用選取的作業或 SQLEXECUTE 作業。|支援|支援|Wcf-custom 配接器會使用**BodyWriter**來建立要求訊息，因此支援端對端節點值 LOB 資料類型的資料流。 Wcf-custom 配接器會使用**XmlDictionaryWriter**取用回應訊息，因此支援端對端節點值，回應訊息中的 LOB 資料類型的資料流。|  
|Wcf-custom 配接器會使用XmlDictionaryWriter取用 （輸入） 的要求訊息，因此支援端對端節點值 LOB 資料類型的資料流。|支援|不過，BizTalk Server 與配接器之間的資料流處理的節點值支援 LOB 資料類型的因為 Wcf-custom 配接器會建立與訊息BodyWriter。 支援用戶端與配接器之間。|不支援端對端節點值串流處理，因為 LOB 資料行的值會緩衝處理 ODP.NET，並接著執行更新。 但是，節點值的資料流的用戶端與配接器之間可能是 LOB 資料行如果用戶端會建立與訊息**BodyWriter**。|  
|資料表刪除作業|支援|不過，BizTalk Server 與配接器之間的資料流處理的節點值支援 LOB 資料類型的因為 Wcf-custom 配接器會建立與訊息BodyWriter。 支援用戶端與配接器之間。|不支援端對端節點值串流處理，因為 ODP.NET 會緩衝處理 LOB 資料行的值，並接著執行刪除。 但是，節點值的資料流的用戶端與配接器之間可能是 LOB 資料行如果用戶端會建立與訊息**BodyWriter**。|  
|資料表 ReadLOB 作業|支援|支援|ReadLOB 作業主要被設計來在 WCF 服務模型中的資料流 LOB 資料行。 在 WCF 通道模型中，如果在用戶端取用訊息**XmlReader** (藉由叫用**GetReaderAtBodyContents**回應訊息上的方法)，會進行串流處理端對端的節點值。 這是因為配接器會傳回**XmlReader**支援**ReadValueChunk**呼叫 ReadLOB 回應訊息。 不過，建議您不要使用 WCF 通道模型 ReadLOB 作業。 您可以改用選取作業或 SQLEXECUTE 作業。|  
|資料表 UpdateLOB 作業|支援|支援|配接器會使用**XmlDictionaryWriter**取用的要求訊息。 如果用戶端會使用**BodyWriter**若要建立要求訊息，端對端節點值串流 LOB 資料，就會發生。|  
|SQLEXECUTE 作業|支援|支援|Wcf-custom 配接器會使用**BodyWriter**來建立要求訊息，因此支援端對端節點值 LOB 資料類型的資料流。<br /><br /> 如果用戶端會使用**XmlDictionaryWriter**取用回應訊息，端對端節點值串流 LOB 資料，就會發生。<br /><br /> 端對端節點值資料流不會支援要求訊息，因為它可以叫用 Oracle 資料庫的作業之前，配接器必須緩衝所有的運算元。|  
|預存程序和函式的作業|支援|支援|Wcf-custom 配接器會使用**BodyWriter**來建立要求訊息，因此支援端對端節點值 LOB 資料類型的資料流。<br /><br /> 如果用戶端會使用**XmlDictionaryWriter**取用回應訊息，端對端節點值串流 LOB 資料，就會發生。 (這表示，支援外的資料流和 IN 出程序和函式參數，回應訊息中的。)<br /><br /> 端對端節點值資料流不會支援要求訊息，因為它可以叫用 Oracle 資料庫的作業之前，配接器必須緩衝所有的運算元。|  
|POLLINGSTMT 作業|支援|支援|配接器會使用**BodyWriter**建立 POLLINGSTMT 要求訊息。 如果在用戶端取用訊息**XmlDictionaryWriter**，則會發生節點值的 LOB 資料行串流。|  
  
 如需如何實作 LOB 資料流在程式碼中，當您使用 WCF 通道模型的資訊，請參閱[串流處理 Oracle 資料庫的 LOB 資料類型使用的 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md)。  
  
## <a name="streaming-support-in-the-wcf-service-model"></a>WCF 服務模型中的資料流支援  
 序列化和還原序列化訊息的 XML 表示法與該訊息的 managed 程式碼物件表示法之間需要寫入和讀取整個訊息載入記憶體。 基於這個理由，資料流處理的節點和節點值的資料流都不支援大部分的作業。  
  
 唯一的例外是 ReadLOB 作業。 這項作業是專為支援端對端資料流來讀取資料表和檢視表的 LOB 資料行中的 WCF 服務模型的實作。  
  
## <a name="streaming-support-in-biztalk-server"></a>在 BizTalk Server 中的資料流支援  
 下表提供有關如何在 BizTalk Server 中支援資料流時的詳細的資訊。 (請參閱 「 介面卡 」 的所有參考[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; Wcf-custom 配接器永遠都有其完整名稱，此資料表中。)  
  
|作業|(請參閱 「 介面卡 」 的所有參考; Wcf-custom 配接器永遠都有其完整名稱，此資料表中。)|不支援配接器與 Oracle 資料庫之間;不過，BizTalk Server 與配接器之間串流資料。|描述|  
|---------------|--------------------|---------------------------|-----------------|  
|不支援端對端節點值串流處理，因為 ODP.NET 會緩衝處理 LOB 資料行的值，並接著執行 insert。|支援*|不支援配接器與 Oracle 資料庫之間;不過，BizTalk Server 與配接器之間串流資料。|不支援端對端節點值串流處理，因為 ODP.NET 會緩衝處理 LOB 資料行的值，並接著執行 insert。 不過，BizTalk Server 與配接器之間的資料流處理的節點值支援 LOB 資料類型的因為 Wcf-custom 配接器會建立與訊息**BodyWriter**。|  
|相反地，請使用選取的作業或 SQLEXECUTE 作業。|支援|支援|Wcf-custom 配接器會使用**XmlDictionaryWriter**取用回應訊息，因此支援端對端節點值串流 LOB 類型。|  
|Wcf-custom 配接器會使用XmlDictionaryWriter取用 （輸入） 的要求訊息，因此支援端對端節點值 LOB 資料類型的資料流。|支援|不支援配接器與 Oracle 資料庫之間;不過，BizTalk Server 與配接器之間串流資料。|因為 ODP.NET 會緩衝處理 LOB 資料行的值，然後執行更新時，不支援端對端節點值資料流。 不過，BizTalk Server 與配接器之間的資料流處理的節點值支援 LOB 資料類型的因為 Wcf-custom 配接器會建立與訊息**BodyWriter**。|  
|資料表刪除作業|支援|不支援配接器與 Oracle 資料庫之間;不過，BizTalk Server 與配接器之間串流資料。|不支援端對端節點值串流處理，因為 ODP.NET 會緩衝處理 LOB 資料行的值，並接著執行刪除。 不過，BizTalk Server 與配接器之間的資料流處理的節點值支援 LOB 資料類型的因為 Wcf-custom 配接器會建立與訊息**BodyWriter**。|  
|資料表 ReadLOB 作業|BizTalk Server 不支援 ReadLOB 作業。|BizTalk Server 不支援 ReadLOB 作業。|BizTalk Server 不支援 ReadLOB 作業。 相反地，請使用選取的作業或 SQLEXECUTE 作業。|  
|資料表 UpdateLOB 作業|支援|支援|Wcf-custom 配接器會使用**BodyWriter**來建立要求訊息，因此支援端對端節點值 LOB 資料類型的資料流。|  
|SQLEXECUTE 作業|支援|支援|Wcf-custom 配接器會使用**XmlDictionaryWriter**取用回應訊息，因此支援端對端節點值，回應訊息中的 LOB 資料類型的資料流。<br /><br /> 端對端節點值資料流不會支援要求訊息，因為它可以叫用 Oracle 資料庫的作業之前，配接器必須緩衝所有的運算元。|  
|預存程序和函式的作業|支援|支援|Wcf-custom 配接器會使用**XmlDictionaryWriter**取用回應訊息，因此支援端對端節點值，回應訊息中的 LOB 資料類型的資料流。 (這表示，支援外的資料流和 IN 出程序和函式參數，回應訊息中的。)<br /><br /> 端對端節點值資料流不會支援要求訊息，因為它可以叫用 Oracle 資料庫的作業之前，配接器必須緩衝所有的運算元。|  
|POLLINGSTMT 作業|支援|支援|Wcf-custom 配接器會使用**XmlDictionaryWriter**取用 （輸入） 的要求訊息，因此支援端對端節點值 LOB 資料類型的資料流。|  
  
## <a name="see-also"></a>另請參閱  
[開發您的 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)