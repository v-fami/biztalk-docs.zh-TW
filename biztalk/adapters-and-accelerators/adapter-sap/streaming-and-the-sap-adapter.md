---
title: "資料流和 SAP 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- streaming, support in WCF service model
- streaming, node-value
- streaming, node
- streaming, support in BizTalk Server
- streaming, and the SAP adapter
- streaming, support in WCF channel model
ms.assetid: 9fa1788b-f21b-4dec-be14-27dd8080a9d4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 48b97b0349822dcca1ae6486e4a0b515778b4d4d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="streaming-and-the-sap-adapter"></a>資料流和 SAP 配接器
[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]支援資料流本身與用戶端應用程式之間的訊息。 與[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]叫用作業，並藉由交換 SOAP 訊息會傳回回應。 將 SOAP 訊息本文所組成的 XML 節點。  
  
 有兩種類型的訊息資料流配接器所支援：  
  
-   **節點資料流**。 在節點資料流中，訊息可以進行資料流處理節點之間的用戶端和配接器一次。 這表示，整個節點的值是讀取到緩衝區，然後傳送給收件者。  
  
-   **節點值的資料流**。 中的節點值資料流處理之節點的實際值進行串流處理的用戶端與配接器之間的區塊 （chunk）。 節點值的資料流適用於傳送或接收大型 Idoc SendIdoc 或 ReceiveIdoc 作業使用。 這是因為整個 IDOC 包含在單一節點。 （而不是強型別傳送或接收的 IDOC 資料會分成許多節點的作業）。  
  
> [!IMPORTANT]
>  配接器和用戶端應用程式之間才支援資料流處理的節點值。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]不支援端對端的節點值與 SAP 系統資料流。 這是因為 SAP 用戶端程式庫不支援這項功能。  
  
 這兩種資料流模式會依賴資料流處理的節點和節點值上 WCF 中的訊息資料流的支援。 基於這個理由，資料流繫結緊密如何建立和使用配接器和用戶端應用程式訊息。 這個結果就是，訊息資料流不支援相同跨所有的程式設計模型。  
  
 本主題中的各節提供：  
  
-   在 WCF 中的訊息資料流支援如何以及如何實作由配接器的基本的背景資訊。  
  
-   如何訊息資料流時，支援您在每個程式撰寫模型中使用配接器的相關資訊。  
  
## <a name="streaming-fundamentals"></a>資料流的基本概念  
 支援資料流實作[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]的組合：  
  
-   在 WCF 中的訊息資料流支援。  
  
-   SAP 用戶端程式庫中的資料流支援。  
  
-   訊息的方式建立和配接器在內部使用。  
  
### <a name="message-streaming-support-in-wcf"></a>在 WCF 中的訊息資料流支援  
 WCF 支援資料流處理訊息的方式取決於訊息的建立方式以及如何使用訊息。  
  
-   WCF 訊息由使用靜態**建立**方法**System.ServiceModel.Channels.Message**。 這個方法有數個多載可支援不同的方式傳遞的訊息本文。 您可以藉由傳遞訊息本文會使用建立 WCF 訊息：  
  
    -   A **System.Xml.XmlReader**，或  
  
    -   A **System.ServiceModel.Channels.BodyWriter**。  
  
-   可以使用取用 WCF 訊息  
  
    -   **XmlReader**藉由呼叫**Message.GetReaderAtBodyContents()**，或  
  
    -   **XmlDictionaryWriter**藉由呼叫**Message.WriteBodyContents(XmlDictionaryWriter)**。  
  
 下表顯示不同的組合，建立及取用訊息的 WCF 行為的方式。  
  
|建立使用訊息|與取用訊息|WCF 行為|  
|--------------------------|---------------------------|------------------|  
|**XmlBodyWriter**|**XmlDictionaryWriter**|**節點值的資料流**支援。 WCF 會經由管道一起，以啟用資料流的兩個寫入器。 這兩個**XmlBodyWriter**和**XmlDictionaryWriter**必須支援的節點值的資料流處理發生這個問題。|  
|**XmlBodyWriter**|**XmlReader**|**節點資料流**支援。 WCF 在內部緩衝區**XmlReader**。|  
|**XmlReader**|**XmlDictionaryWriter**|**節點資料流**支援。 WCF 在內部緩衝區**XmlReader**並回呼至**XmlDictionaryWriter**。|  
|**XmlReader**|**XmlReader**|**節點資料流**支援。 WCF 在內部緩衝區**XmlReader**。|  
  
### <a name="streaming-support-in-the-sap-client-library"></a>SAP 用戶端程式庫中的資料流支援  
 SAP 用戶端程式庫不支援資料流。 因此端對端的節點值的資料流不支援[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
### <a name="internal-message-handling-by-the-adapter"></a>內部訊息處理配接器  
 配接器支援串流以下列方式：  
  
-   配接器取用 SendIdDoc 要求訊息使用的自訂實作接收自用戶端**XmlDictionaryWriter**。 它會取用來自用戶端會使用所有其他訊息**XmlReader**。  
  
-   配接器建立 ReceiveIdoc 要求訊息傳送至用戶端使用的自訂實作**XmlBodyWriter**。 它會建立所有其他訊息傳送至用戶端會使用**XmlReader**。  
  
## <a name="streaming-support-in-the-wcf-channel-model"></a>WCF 通道模型中的資料流支援  
 下表提供有關如何支援資料流中的 WCF 通道模型的詳細的資訊。  
  
|作業|節點資料流|節點值的資料流|Description|  
|---------------|--------------------|---------------------------|-----------------|  
|傳出的 RFC 和 BAPI 作業 （從用戶端至配接器）|不支援|不支援||  
|（從用戶端至配接器） 輸出 tRFC 作業|不支援|不支援||  
|傳送 IDOC 的作業 （強型別）|不支援|不支援||  
|接收 IDOC 的作業 （強型別）|支援|不支援||  
|SendIdoc 作業 （字串）|支援|支援|配接器使用**XmlDictionaryWriter**使用要求訊息。 如果用戶端會建立使用訊息**BodyWriter**，節點值從用戶端串流至配接器，就會發生。|  
|ReceiveIdoc 作業 （字串）|支援|支援|配接器使用**BodyWriter**建立要求訊息。 如果在用戶端取用訊息使用**XmlDictionaryWriter**，節點值從配接器串流至用戶端，就會發生。|  
|輸入的 RFC 操作|不支援|不支援||  
|輸入 tRFC 作業|不支援|不支援||  
  
 如需如何實作資料流來傳送和接收一般檔案 （字串） 的 Idoc 使用 SendIdoc 和 ReceiveIdoc 作業程式碼中的節點值的資訊，請參閱[SAP 使用 WCF 通道模型中的資料流一般檔案 Idoc](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md)。  
  
## <a name="streaming-support-in-the-wcf-service-model"></a>WCF 服務模型中的資料流支援  
 序列化和還原序列化訊息的 XML 表示法之間的 managed 程式碼的物件表示該訊息需要寫入和讀取到記憶體中的整個訊息。 基於這個理由，資料流處理的節點和節點值的資料流都不支援從 WCF 服務模型。  
  
## <a name="streaming-support-in-biztalk-server"></a>BizTalk Server 中的資料流支援  
 下表提供有關 BizTalk Server 中的資料流支援方式的詳細的資訊。  
  
|作業|節點資料流|節點值的資料流|Description|  
|---------------|--------------------|---------------------------|-----------------|  
|RFC 和 BAPI 的作業 （從用戶端至配接器）|不支援|不支援||  
|tRFC 作業 （從用戶端至配接器）|不支援|不支援||  
|傳送 IDOC 的作業 （強型別）|不支援|不支援||  
|接收 IDOC 的作業 （強型別）|支援|不支援||  
|SendIdoc 作業 （字串）|支援|支援|Wcf-custom 配接器會使用**BodyWriter**來建立要求訊息，因此支援的節點值的資料流。|  
|ReceiveIdoc 作業 （字串）|支援|支援|Wcf-custom 配接器會使用**XmlDictionaryWriter**使用要求訊息，因此支援的節點值的資料流。|  
|輸入的 RFC 操作|不支援|不支援||  
|輸入 tRFC 作業|不支援|不支援||  
  
## <a name="see-also"></a>另請參閱  
[開發您的 SAP 應用程式](../../adapters-and-accelerators/adapter-sap/develop-your-sap-applications.md)