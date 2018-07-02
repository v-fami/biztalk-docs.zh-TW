---
title: WCF 傳送配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, headers
- serializing, SOAP messages
- WCF adapters, extracting information
- messages, extracting information
- SOAP messages, serializing
- WCF adapters, message bodies
- send adapters, WCF adapters
- Web services, headers
- WCF adapters, send adapters
ms.assetid: 226a020a-2e12-41fe-a4a2-6683d9e98219
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7f36bca73ebd178d8d4052bfbcfa837c0d548ab
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37020667"
---
# <a name="wcf-send-adapter"></a>WCF 傳送配接器
WCF 傳送埠可以讓您透過無類型合約來呼叫 WCF 服務。  
  
## <a name="specifying-the-wcf-message-body"></a>指定 WCF 訊息內文  
 需要從 BizTalk Server 傳送的訊息內文，可以使用下列一個選項插入到 SOAP 訊息：  
  
- 擷取 BizTalk 訊息內文的內容  
  
- 藉由使用範本來指定內容  
  
  您可以在傳送埠傳輸屬性對話方塊中設定這些選項。  
  
#### <a name="extract-the-content-of-the-biztalk-message-body"></a>擷取 BizTalk 訊息內文的內容  
 選取這個選項時，會針對輸出 WCF 訊息內文，將 BizTalk 訊息內文的內容插入到 SOAP 內文項目。  
  
#### <a name="specify-the-content-by-using-the-template"></a>藉由使用範本來指定內容  
 選取這個選項時，會針對輸出 WCF 訊息內文，將 BizTalk 訊息內文置放於 SOAP Body 項目中的指定 XML 範本下。  
  
## <a name="serializing-the-biztalk-message-into-a-soap-message"></a>將 BizTalk 訊息序列化到 SOAP 訊息中  
 傳送配接器在將 BizTalk 訊息傳送出去前，會先將訊息序列化於 SOAP 訊息中。訊息序列化期間會套用下列規則：  
  
-   如果 BizTalk 訊息是多部分訊息，則只會使用內文部分。  
  
-   如果 BizTalk 訊息包含整個 SOAP 信封，則會包裝到另一個 SOAP 信封中。  
  
-   如果 BizTalk 訊息包含任意 XML 資料，則會將 BizTalk 訊息置放於 SOAP Body 項目中。  
  
## <a name="handling-web-services-headers"></a>處理 Web 服務標頭  
 傳送作業期間，BizTalk Server 無法控制 Web 服務的標準標頭。 這些標頭是由 WCF 所設定和處理的。 可以修改 BizTalk Server 應用程式的唯一標準標頭 **： 動作**標頭。 如果內容屬性**動作**您的配接器命名空間上指定，則 WCF 傳送配接器會使用屬性的值來設定**動作**SOAP 訊息。  
  
> [!NOTE]
>  動態傳送埠，如果**動作**中指定**OutboundHeaders**，為您設定的內容屬性**WCF。動作**將會被忽略。  
  
## <a name="specifying-the-btsisdynamicsend-context-property"></a>指定 BTS.IsDynamicSend 內容屬性  
 WCF 傳送配接器會快取傳送埠組態。 如果**BTS。IsDynamicSend**屬性設定為 true，則 WCF 傳送配接器不會使用快取的組態，但改為讀取所有的組態資訊訊息的輸出訊息的內容屬性。 在靜態傳送埠，WCF 傳送配接器會使用**BTS。SPLastUpdatedTime**、 上次修改靜態傳送埠設定的時間，來偵測是否有任何組態變更靜態傳送埠。 在這種方式下，WCF 傳送埠不需要從每個訊息內容讀取所有設定。  
  
 如果您想要覆寫靜態傳送埠屬性以外的其他**WCF。動作**傳送管線中的屬性，您必須設定**BTS。IsDynamicSend**屬性設定為 true，因此即使上次更新時間戳記，WCF 傳送配接器不會使用快取的組態未變更。  
  
## <a name="see-also"></a>另請參閱  
 [指定 WCF 配接器的訊息內文](../core/specifying-the-message-body-for-the-wcf-adapters.md)   
 [WCF 接收配接器](../core/wcf-receive-adapter.md)   
 [WCF 配接器有哪些？](../core/what-are-the-wcf-adapters.md)   
 [如何使用訊息內容屬性](../core/how-to-use-message-context-properties.md)