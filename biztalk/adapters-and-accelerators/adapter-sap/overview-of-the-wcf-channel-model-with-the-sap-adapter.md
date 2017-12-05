---
title: "SAP 配接器之 WCF 通道模型的概觀 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF channel model, overview
- WCF channel model, creating messages for the SAP adapter
ms.assetid: 6192d637-efac-4580-8880-b5bae9d16f31
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 51b5469681f7acce2ebb0b55fe63e285d25192e0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="overview-of-the-wcf-channel-model-with-the-sap-adapter"></a>SAP 配接器的 WCF 通道模型概觀
若要叫用 Rfc、 tRFCs 或 Bapi 上 SAP 系統，或傳送 IDOC 至 SAP 系統，您的程式碼做為 WCF 用戶端，並將傳出作業傳送至配接器。 在 WCF 通道模型中，您的程式碼會透過通道傳送的要求訊息叫用的介面卡上的作業。  
  
 若要做為 tRFC 或 RFC 伺服器到 SAP 系統，您的程式碼做為 WCF 服務的行為。 也就是說，配接器會叫用在您的程式碼的輸入的作業 — 比方說，RFC 或 ReceiveIdoc 作業 （若要以字串格式，從 SAP 系統接收 IDOC）。 在此案例中，您的程式碼會透過配接器從通道接收作業的要求訊息。  
  
 本節中的主題提供使用概觀[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]WCF 通道模型。  
  
## <a name="wcf-channel-model-overview"></a>WCF 通道模型概觀  
 用戶端和服務交換的 SOAP 訊息來進行通訊。 WCF 通道模型是低層級的抽象概念，這個訊息交換。 它提供介面和類型，可讓您傳送和接收訊息所使用的是稱為通道堆疊的多層式通訊協定堆疊。 堆疊的每個圖層由通道時，所組成，且每個通道會建立從 WCF 繫結。 最低層級是傳輸通道。 傳輸通道會實作服務的用戶端之間的基礎傳輸機制，並呈現較高的層級 （及最終使用的應用程式） 的每個訊息**System.ServiceModel.Message**。 WCF**訊息**類別是抽象的 SOAP 訊息。 WCF 提供數個通道介面，稱為通道形狀，建立模型的基本 SOAP 訊息交換模式，例如要求-回覆或單向。 WCF 傳輸繫結提供實作的其中一個或多個更高層次的通道形狀可用來傳送和接收訊息。 如需 WCF 通道模型的詳細資訊，請參閱[通道模型概觀](https://msdn.microsoft.com/library/ms729840.aspx)。
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]是 WCF 自訂傳輸繫結會公開為 WCF 服務的 SAP 系統。  
  
## <a name="supported-channel-shapes-for-the-sap-adapter"></a>支援 SAP 配接器的通道形狀  
 配接器實作下列的 WCF 通道形狀：  
  
-   **IRequestChannel** (**System.ServiceModel.Channels.IRequestChannel**)。 **IRequestChannel**介面實作的用戶端的要求-回覆訊息交換。 您可以使用**IRequestChannel**執行作業，您想要取用的回應，例如若要叫用傳回的資料在 SAP 系統上的 RFC。  
  
-   **IOutputChannel** (**System.ServiceModel.Channels.IOutputChannel**)。 此圖形會實作單向訊息交換的用戶端。 您可以使用**IOutputChannel**叫用作業，您不需要使用的回應，例如若要叫用的 RFC，SAP 系統不會傳回任何資料。  
  
-   **IReplyChannel** (**System.ServiceModel.Channels.IReplyChannel**)。 此圖形會實作服務端的要求-回覆訊息交換。 您可以使用**IReplyChannel**實作 RFC 或 tRFC 伺服器，或是從 SAP 系統接收 Idoc。  
  
 像任何 WCF 繫結，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]用以提供應用程式程式碼的通道處理站模式。 您使用**Microsoft.Adapters.SAPBinding**物件建立的執行個體：  
  
-   **System.ServiceModel.ChannelFactory\<IRequestChannel\>** 提供**IRequestChannel**通道可用來叫用的介面卡上的要求-回應作業。  
  
-   **System.ServiceModel.ChannelFactory\<IOutputChannel\>** 提供**IOutputChannel**通道可用來叫用的介面卡上的單向作業。  
  
-   **System.ServiceModel.IChannelListener\<IReplyChannel\>** 提供**IReplyChannel**通道可用來從配接器接收要求-回應作業。  
  
## <a name="creating-messages-for-the-sap-adapter-in-the-wcf-channel-model"></a>SAP 配接器 WCF 通道模型中建立訊息  
 在 WCF 中**System.ServiceModel.Channels.Message**類別會提供在記憶體中表示 SOAP 訊息。 您建立**訊息**叫用靜態執行個體**Message.Create**方法。  
  
 有兩個重要的部分 SOAP 訊息，您必須指定當您建構**訊息**將傳送至執行個體[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
-   訊息動作是 SOAP 訊息標頭的字串。 訊息動作識別應該叫用作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 下列範例示範 SD_RFC_CUSTOMER_GET RFC，SAP 系統上叫用指定的訊息動作： `http://Microsoft.LobServices.Sap/2007/03/Rfc/SD_RFC_CUSTOMER_GET`。  
  
-   訊息內文包含作業的參數資料。 訊息本文由格式正確對應至所預期的訊息結構描述的 XML 組成[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]要求的作業。 下列的訊息本文會包含 SD_RFC_CUSTOMER_GET RFC，SAP 系統上的參數。  
  
    ```  
    <SD_RFC_CUSTOMER_GET xmlns=\"http://Microsoft.LobServices.Sap/2007/03/Rfc/\"> <KUNNR i:nil=\"true\" xmlns:i=\"http://www.w3.org/2001/XMLSchema-instance\"> </KUNNR> <NAME1>AB*</NAME1> <CUSTOMER_T> </CUSTOMER_T> </SD_RFC_CUSTOMER_GET>  
    ```  
  
 如需有關資訊[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]訊息結構描述和訊息作業的動作，請參閱[訊息和訊息結構描述，BizTalk adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)。  
  
 **Message.Create**方法多載，而且提供了許多不同的選項來提供訊息內文。 下列程式碼示範如何建立**訊息**所使用的執行個體**System.Xml.XmlReader**提供訊息內文。 在此程式碼中，訊息本文會讀取字串常數。  
  
```  
//create an XML message to send to the SAP system  
//We are invoking the SD_RFC_CUSTOMER_GET RFC.  
//The XML below specifies that we want to search for customers with names starting with "AB"  
string inputXml = "<SD_RFC_CUSTOMER_GET xmlns=\"http://Microsoft.LobServices.Sap/2007/03/Rfc/\"> <KUNNR i:nil=\"true\" xmlns:i=\"http://www.w3.org/2001/XMLSchema-instance\"> </KUNNR> <NAME1>AB*</NAME1> <CUSTOMER_T> </CUSTOMER_T> </SD_RFC_CUSTOMER_GET>";  
  
//create an XML reader from the input XML  
XmlReader reader = XmlReader.Create(new MemoryStream(Encoding.Default.GetBytes(inputXml)));  
  
//create a WCF message from the XML reader  
Message inputMessge = Message.CreateMessage(MessageVersion.Soap11, "http://Microsoft.LobServices.Sap/2007/03/Rfc/SD_RFC_CUSTOMER_GET", reader);  
```  
  
> [!IMPORTANT]
>  您必須提供中的訊息動作您**訊息**執行個體。 這通常是當**訊息**建立執行個體。  
  
## <a name="streaming-support-on-the-sap-adapter-in-the-wcf-channel-model"></a>在 SAP 中的配接器的 WCF 通道模型的資料流支援  
 如何建立及取用您 SAP 配接器與交換的訊息會決定如何將訊息串流您的程式碼與配接器之間。  
  
### <a name="node-streaming"></a>節點資料流  
 節點資料流是唯一的層級的資料流支援除了 SendIdoc 和 ReceiveIdoc 作業以外的所有作業。  
  
 若要執行節點資料流處理訊息時，您：  
  
-   建立外寄訊息使用**XmlReader**提供訊息內文。  
  
-   使用內送的訊息使用**XmlReader**。 您藉由呼叫取得讀取器**GetReaderAtBodyContents**方法在輸入**訊息**。  
  
### <a name="node-value-streaming"></a>節點值的資料流  
 因為 SendIdoc 和 ReceiveIdoc 作業包含在字串中的單一 XML 節點下的 IDOC 資料 (\<idocData\>)、 配接器支援節點值資料流處理這些作業。  
  
 若要執行這些作業的資料流處理的節點值，您可以：  
  
-   建立 SendIdoc 要求訊息 （輸出） 使用**BodyWriter**實作節點值來提供訊息內文資料流。  
  
-   使用 ReceiveIdoc 要求訊息 （輸入） 藉由呼叫**WriteBodyContents**方法在訊息與**XmlDictionaryWriter**實作節點值的資料流。  
  
 如需串流處理使用 WCF 通道模型 （字串） 的一般檔案 Idoc 的詳細資訊，請參閱[SAP 使用 WCF 通道模型中的資料流處理一般檔案 Idoc](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md)。  
  
## <a name="see-also"></a>請參閱  
[使用 WCF 通道模型開發應用程式](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)