---
title: 串流和 SAP 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- streaming, support in WCF service model
- streaming, node-value
- streaming, node
- streaming, support in BizTalk Server
- streaming, and the SAP adapter
- streaming, support in WCF channel model
ms.assetid: 9fa1788b-f21b-4dec-be14-27dd8080a9d4
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f012073f507026a03060a4ddf6c0574fe34186ef
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004351"
---
# <a name="streaming-and-the-sap-adapter"></a>串流和 SAP 配接器
[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]支援資料流本身和用戶端應用程式之間的訊息。 使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]叫用作業，並藉由交換的 SOAP 訊息會傳回回應。 SOAP 訊息內文包含的 XML 節點。  
  
 有兩種類型的訊息資料流所支援的配接器：  
  
-   **節點資料流**。 在節點資料流中，訊息可以進行串流處理節點之間的用戶端和配接器一次。 這表示整個節點的值時，讀取到緩衝區，並再傳送給接收者。  
  
-   **節點值串流**。 節點值可以在用戶端與配接器之間的區塊串流串流處理之節點的實際值。 節點值的資料流可用於傳送或接收大型的 Idoc 使用 SendIdoc 或 ReceiveIdoc 作業就行了。 這是因為整個 IDOC 包含在單一節點。 （而不是強型別傳送或接收的 IDOC 資料會分成許多節點的作業）。  
  
> [!IMPORTANT]
>  配接器和用戶端應用程式之間，才支援資料流處理的節點值。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不支援端對端節點值與 SAP 系統資料流。 這是因為 SAP 用戶端程式庫不支援這項功能。  
  
 這兩個資料流模式依賴支援串流處理的節點和節點值的資料流處理 WCF 中的訊息。 基於這個理由，資料流繫結緊密訊息建立與取用配接器和用戶端應用程式的方式。 這麼做的結果是，訊息資料流不支援相同跨所有的程式設計模型。  
  
 本主題中的各節提供：  
  
-   如何在 WCF 中支援訊息資料流是和配接器的實作方式的基本的背景資訊。  
  
-   如何訊息資料流時，支援每個程式設計模型中所使用的配接器的相關資訊。  
  
## <a name="streaming-fundamentals"></a>資料流的基本概念  
 支援資料流實作[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]組成：  
  
-   在 WCF 中的訊息資料流支援。  
  
-   在 SAP 用戶端程式庫中的資料流支援。  
  
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
  
### <a name="streaming-support-in-the-sap-client-library"></a>在 SAP 用戶端程式庫中的資料流支援  
 SAP 用戶端程式庫不支援資料流。 因此端對端的節點值的資料流不支援[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
### <a name="internal-message-handling-by-the-adapter"></a>內部配接器所處理的訊息  
 配接器支援串流以下列方式：  
  
-   配接器取用 SendIdDoc 要求訊息使用的自訂實作，從用戶端收到**XmlDictionaryWriter**。 它會取用其他使用從用戶端收到的所有訊息**XmlReader**。  
  
-   配接器建立 ReceiveIdoc 要求訊息傳送至用戶端使用的自訂實作**XmlBodyWriter**。 它會建立針對它傳送至用戶端會使用所有其他訊息**XmlReader**。  
  
## <a name="streaming-support-in-the-wcf-channel-model"></a>在 BizTalk Server 中的資料流支援  
 下表提供有關如何在 BizTalk Server 中支援資料流時的詳細的資訊。  
  
|作業|(請參閱 「 介面卡 」 的所有參考; Wcf-custom 配接器永遠都有其完整名稱，此資料表中。)|不支援配接器與 Oracle 資料庫之間;不過，BizTalk Server 與配接器之間串流資料。|描述|  
|---------------|--------------------|---------------------------|-----------------|  
|傳出的 RFC 和 BAPI 作業 （從配接器用戶端）|不支援|不支援||  
|輸出的 tRFC 作業 （從配接器用戶端）|不支援|不支援||  
|傳送 IDOC 的作業 （強型別）|不支援|不支援||  
|接收 IDOC 的作業 （強型別）|支援|不支援||  
|SendIdoc 作業 （字串）|支援|支援|配接器會使用**XmlDictionaryWriter**取用的要求訊息。 如果用戶端會建立與訊息**BodyWriter**，從用戶端串流至配接器的節點值，就會發生。|  
|ReceiveIdoc 作業 （字串）|支援|支援|配接器會使用**BodyWriter**以建立要求訊息。 如果在用戶端取用訊息**XmlDictionaryWriter**，配接器從串流至用戶端節點值，就會發生。|  
|RFC 作業的輸入|不支援|不支援||  
|輸入的 tRFC 作業|不支援|不支援||  
  
 如需如何實作資料流傳送及接收一般檔案 （字串） 的 Idoc 使用 SendIdoc 和 ReceiveIdoc 作業程式碼中的節點值的資訊，請參閱[Stream 中使用 WCF 通道模型的 SAP 的一般檔案 Idoc](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md)。  
  
## <a name="streaming-support-in-the-wcf-service-model"></a>WCF 服務模型中的資料流支援  
 序列化和還原序列化訊息的 XML 表示法與該訊息的 managed 程式碼物件表示法之間需要寫入和讀取整個訊息載入記憶體。 基於這個理由，資料流處理的節點和節點值的資料流都不支援從 WCF 服務模型。  
  
## <a name="streaming-support-in-biztalk-server"></a>在 BizTalk Server 中的資料流支援  
 下表提供有關如何在 BizTalk Server 中支援資料流時的詳細的資訊。  
  
|作業|(請參閱 「 介面卡 」 的所有參考; Wcf-custom 配接器永遠都有其完整名稱，此資料表中。)|不支援配接器與 Oracle 資料庫之間;不過，BizTalk Server 與配接器之間串流資料。|描述|  
|---------------|--------------------|---------------------------|-----------------|  
|RFC 和 BAPI 的作業 （從配接器用戶端）|不支援|不支援||  
|tRFC 作業 （從配接器用戶端）|不支援|不支援||  
|傳送 IDOC 的作業 （強型別）|不支援|不支援||  
|接收 IDOC 的作業 （強型別）|支援|不支援||  
|SendIdoc 作業 （字串）|支援|支援|Wcf-custom 配接器會使用**BodyWriter**來建立要求訊息，因此支援節點值的資料流。|  
|ReceiveIdoc 作業 （字串）|支援|支援|Wcf-custom 配接器會使用**XmlDictionaryWriter**取用的要求訊息中，因此支援節點值的資料流。|  
|RFC 作業的輸入|不支援|不支援||  
|輸入的 tRFC 作業|不支援|不支援||  
  
## <a name="see-also"></a>另請參閱  
[開發您的 SAP 應用程式](../../adapters-and-accelerators/adapter-sap/develop-your-sap-applications.md)