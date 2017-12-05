---
title: "使用 Oracle 資料庫配接器的 WCF 通道模型概觀 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF channel model, overview
ms.assetid: 4712ba62-8360-475c-b2e4-422e499eca21
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94cb4b8cfdb0315b55aa88ddd385396ff967b8f6
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="overview-of-the-wcf-channel-model-with-the-oracle-database-adapter"></a>使用 Oracle 資料庫配接器的 WCF 通道模型概觀
在叫用作業[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]，您的程式碼做為 WCF 用戶端，並將傳出作業傳送至配接器。 在 WCF 通道模型中，您的程式碼會透過通道傳送的要求訊息叫用的介面卡上的作業。  
  
 叫用傳入的作業，例如 receiveing 輪詢基礎資料變更訊息使用配接器所提供的 POLLINGSTMT 運算您的程式碼做為 WCF 服務，並從配接器接收傳入的作業。 換句話說，您的程式碼會接收要求訊息從配接器透過通道。  
  
 本節中的主題提供使用概觀[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]WCF 通道模型。  
  
## <a name="wcf-channel-model-overview"></a>WCF 通道模型概觀  
 用戶端和服務交換的 SOAP 訊息來進行通訊。 WCF 通道模型是低層級的抽象概念，這個訊息交換。 它提供介面和類型，可讓您傳送和接收訊息所使用的是稱為通道堆疊的多層式通訊協定堆疊。 堆疊的每個圖層由通道時，所組成，且每個通道會建立從 WCF 繫結。 最低層級是傳輸通道。 傳輸通道會實作服務的用戶端之間的基礎傳輸機制，並呈現較高的層級 （及最終使用的應用程式） 的每個訊息**System.ServiceModel.Message**。 WCF**訊息**類別是抽象的 SOAP 訊息。 WCF 提供數個通道介面，稱為通道形狀，建立模型的基本 SOAP 訊息交換模式，例如要求-回覆或單向。 WCF 傳輸繫結提供實作的其中一個或多個更高層次的通道形狀可用來傳送和接收訊息。 如需 WCF 通道模型的詳細資訊，請參閱[通道模型概觀](https://msdn.microsoft.com/library/ms729840.aspx)。   
  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]是 WCF 自訂傳輸繫結會公開為 WCF 服務的 Oracle 資料庫。  
  
## <a name="supported-channel-shapes-for-the-oracle-database-adapter"></a>Oracle 資料庫配接器支援通道形狀  
 配接器實作下列的 WCF 通道形狀：  
  
-   **IRequestChannel** (**System.ServiceModel.Channels.IRequestChannel**)。 **IRequestChannel**介面實作的用戶端的要求-回覆訊息交換。 您可以使用**IRequestChannel**若要執行您要使用回應的作業，例如若要執行 SELECT 查詢 Oracle 資料表上。  
  
-   **IOutputChannel** (**System.ServiceModel.Channels.IOutputChannel**)。 此圖形會實作單向訊息交換的用戶端。 您可以使用**IOutputChannel**叫用作業，您不需要使用的回應，例如若要呼叫 Oracle 程序沒有 OUT 參數。  
  
    > [!IMPORTANT]
    >  所有基礎呼叫配接器對 Oracle 用戶端為同步。 這包括透過叫用作業的結果將會是 Oracle 用戶端呼叫**IOutputChannel**。 當您使用**IOutputChannel**，配接器會捨棄對 Oracle 用戶端從收到的回應。  
  
-   **IInputChannel** (**System.ServiceModel.Channels.IInputChannel**)。 此圖形會實作服務端的單向訊息交換。 您使用**IInputChannel**以接收來自配接器的輸入作業的訊息。  
  
 像任何 WCF 繫結，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]用以提供應用程式程式碼的通道處理站模式。 您使用**Microsoft.Adapters.OracleDBBinding**物件建立的執行個體：  
  
-   **System.ServiceModel.ChannelFactory\<IRequestChannel\>** 提供**IRequestChannel**通道可用來叫用的介面卡上的要求-回應作業。  
  
-   **System.ServiceModel.ChannelFactory\<IOutputChannel\>** 提供**IOutputChannel**通道可用來叫用的介面卡上的單向作業。  
  
-   **System.ServiceModel.IChannelListener\<IInputChannel\>** 提供**IInputChannel**通道可用來從配接器接收內送的訊息 （例如 POLLINGSTMT 作業）.  
  
### <a name="creating-messages-for-the-oracle-database-adapter-in-the-wcf-channel-model"></a>正在建立 Oracle 資料庫配接器 WCF 通道模型中的訊息  
 在 WCF 中**System.ServiceModel.Channels.Message**類別會提供在記憶體中表示 SOAP 訊息。 您建立**訊息**叫用靜態執行個體**Message.Create**方法。  
  
 有兩個重要的部分 SOAP 訊息，您必須指定當您建立**訊息**將傳送至執行個體[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
-   訊息動作是 SOAP 訊息標頭的字串。 訊息動作會識別應該要叫用的 Oracle 資料庫的作業。 下列範例示範叫用選取的作業/SCOTT/EMP 資料表上所指定的訊息動作： `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Select`。  
  
-   訊息內文包含作業的參數資料。 訊息本文由格式正確對應至所預期的訊息結構描述的 XML 組成[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]要求的作業。 下列的訊息本文指定 SCOTT 上的選取作業。EMP 資料表 (選取 * 從 EMP)。  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Select xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP">  
        <COLUMN_NAMES>*</COLUMN_NAMES>  
    </Select>  
    ```  
  
 如需有關資訊[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]訊息結構描述和訊息作業的動作，請參閱[訊息和訊息結構描述，BizTalk adapter for Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)。  
  
 這**建立**方法多載，而且提供了許多不同的選項來提供訊息內文。 下列程式碼示範如何建立**訊息**所使用的執行個體**XmlReader**提供訊息內文。 在此程式碼，是從檔案讀取訊息本文。  
  
```  
XmlReader readerIn = XmlReader.Create("SelectAllActivity.xml");  
Message messageIn = Message.CreateMessage(MessageVersion.Default,  
    "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Select",  
    readerIn);  
```  
  
> [!IMPORTANT]
>  您必須提供中的訊息動作您**訊息**執行個體。 這通常是當**訊息**建立執行個體。  
  
## <a name="streaming-support-for-lob-data-types-in-the-wcf-channel-model"></a>WCF 通道模型中的 LOB 資料類型的串流支援  
 由配接器顯示某些作業支援端對端的資料流的 LOB 資料類型。 對於這些作業，您建立和使用您透過傳送和接收通道的訊息的方式決定是否支援資料流的 LOB 資料。  
  
 如需有關如何[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援資料流處理 LOB 資料，請參閱[串流處理大型物件資料類型在 Oracle 資料庫配接器](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md)。  
  
 如需實作串流處理您的程式碼，以支援端對端 LOB 資料的資料流中的節點值的詳細資訊，請參閱[串流處理 Oracle 資料庫的 LOB 資料類型使用 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md)。  
  
## <a name="see-also"></a>請參閱  
 [開發 Oracle 資料庫應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)