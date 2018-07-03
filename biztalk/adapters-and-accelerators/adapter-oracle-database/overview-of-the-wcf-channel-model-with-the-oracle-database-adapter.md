---
title: 使用 Oracle 資料庫配接器的 WCF 通道模型概觀 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF channel model, overview
ms.assetid: 4712ba62-8360-475c-b2e4-422e499eca21
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1f681b4a4725f4e866d8959d8851362f0214137
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992687"
---
# <a name="overview-of-the-wcf-channel-model-with-the-oracle-database-adapter"></a>使用 Oracle 資料庫配接器的 WCF 通道模型概觀
在叫用作業[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]，您的程式碼做為 WCF 用戶端，並將傳出作業傳送至配接器。 在 WCF 通道模型中，您的程式碼會叫用介面卡上的作業，透過通道傳送要求訊息。  
  
 要叫用輸入的作業，例如 receiveing 輪詢為基礎的資料變更訊息使用 POLLINGSTMT 作業提供的配接器，您的程式碼做為 WCF 服務，並從配接器接收輸入的作業。 換句話說，您的程式碼會接收要求訊息從配接器透過通道。  
  
 在本節中的主題提供使用的概觀[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用 WCF 通道模型。  
  
## <a name="wcf-channel-model-overview"></a>WCF 通道模型概觀  
 用戶端和服務交換的 SOAP 訊息來進行通訊。 WCF 通道模型是低層級的抽象概念，此訊息交換。 它提供介面和類型，可讓您傳送和接收訊息所使用的是稱為通道堆疊的多層式通訊協定堆疊。 堆疊的每個圖層由通道所組成，每一個色頻建立從 WCF 繫結。 最低層級是傳輸通道。 傳輸通道會實作服務和用戶端之間的基礎傳輸機制，並呈現較高的層級 （和最終取用的應用程式） 每個訊息**System.ServiceModel.Message**。 WCF**訊息**類別是抽象的 SOAP 訊息。 WCF 提供數個通道介面，稱為通道形狀，模型的基本 SOAP 訊息交換模式，例如要求-回覆或單向。 WCF 傳輸繫結提供實作的其中一個或多個更新版本階層的通道形狀可用來傳送和接收訊息。 如需有關 WCF 通道模型的詳細資訊，請參閱 <<c0> [ 通道模型概觀](https://msdn.microsoft.com/library/ms729840.aspx)。   
  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]是 Oracle 資料庫為 WCF 服務公開 （expose） 的 WCF 自訂傳輸繫結。  
  
## <a name="supported-channel-shapes-for-the-oracle-database-adapter"></a>Oracle 資料庫配接器支援通道形狀  
 配接器實作下列的 WCF 通道形狀：  
  
- **IRequestChannel** (**System.ServiceModel.Channels.IRequestChannel**)。 **IRequestChannel**介面會實作要求-回覆訊息交換的用戶端。 您可以使用**IRequestChannel**若要執行您要使用回應的作業，例如若要執行 SELECT 查詢上的 Oracle 資料表。  
  
- **IOutputChannel** (**System.ServiceModel.Channels.IOutputChannel**)。 此圖形會實作單向訊息交換的用戶端。 您可以使用**IOutputChannel**叫用作業，您不需要使用的回應，例如若要呼叫 Oracle 程序沒有 OUT 參數。  
  
  > [!IMPORTANT]
  >  所有基礎呼叫，配接器以 Oracle 用戶端都是同步的。 這包括對 Oracle 用戶端是透過叫用作業的結果**IOutputChannel**。 當您使用**IOutputChannel**，配接器會捨棄從 Oracle 用戶端收到的回應。  
  
- **IInputChannel** (**System.ServiceModel.Channels.IInputChannel**)。 此圖形會實作服務端的單向訊息交換。 您使用**IInputChannel**以接收來自配接器的輸入作業的訊息。  
  
  讓任何 WCF 繫結[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]用以提供應用程式程式碼的通道處理站模式。 您使用**Microsoft.Adapters.OracleDBBinding**建立的執行個體的物件：  
  
- **System.ServiceModel.ChannelFactory\<IRequestChannel\>** 提供**IRequestChannel**通道可用來叫用的介面卡上的要求-回應作業。  
  
- **System.ServiceModel.ChannelFactory\<IOutputChannel\>** 提供**IOutputChannel**通道可用來叫用的介面卡上的單向作業。  
  
- **System.ServiceModel.IChannelListener\<IInputChannel\>** 提供**IInputChannel**通道可用來從配接器接收輸入的訊息 （例如 POLLINGSTMT 作業）。  
  
### <a name="creating-messages-for-the-oracle-database-adapter-in-the-wcf-channel-model"></a>正在建立的 WCF 通道模型中的 Oracle 資料庫配接器訊息  
 在 WCF **System.ServiceModel.Channels.Message**類別提供在記憶體中表示 SOAP 訊息。 您建立**訊息**執行個體，藉由叫用靜態**Message.Create**方法。  
  
 有兩個重要的部分，您必須指定當您建立的 SOAP 訊息**訊息**執行個體來傳送至[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
- 訊息的動作是屬於 SOAP 訊息標頭的字串。 [訊息] 動作會識別應該叫用的 Oracle 資料庫的作業。 下面顯示來叫用選取的作業/SCOTT/EMP 資料表上所指定的訊息動作： `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Select`。  
  
- 訊息內文包含作業的參數資料。 訊息內文由語式正確對應至所預期的訊息結構描述的 XML 組成[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]要求的作業。 下列的訊息本文指定 SCOTT 上的選取作業。EMP 資料表 (選取 * 從 EMP)。  
  
  ```  
  <?xml version="1.0" encoding="utf-8" ?>  
  <Select xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP">  
      <COLUMN_NAMES>*</COLUMN_NAMES>  
  </Select>  
  ```  
  
  如需[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]訊息結構描述和訊息作業的動作，請參閱[訊息和訊息結構描述，BizTalk adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)。  
  
  這**建立**方法多載，並提供許多不同的選項，來提供訊息內文。 下列程式碼示範如何建立**訊息**使用的執行個體**XmlReader**提供訊息內文。 在此程式碼，是從檔案讀取訊息主體。  
  
```  
XmlReader readerIn = XmlReader.Create("SelectAllActivity.xml");  
Message messageIn = Message.CreateMessage(MessageVersion.Default,  
    "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Select",  
    readerIn);  
```  
  
> [!IMPORTANT]
>  您必須提供中的訊息動作您**訊息**執行個體。 這通常是何時**訊息**建立執行個體。  
  
## <a name="streaming-support-for-lob-data-types-in-the-wcf-channel-model"></a>WCF 通道模型中的 LOB 資料類型的串流支援  
 端對端串流 LOB 資料類型的支援由配接器顯示某些作業。 對於這些作業，您建立和使用您傳送與透過通道接收之訊息的方式判斷是否支援資料流上的 LOB 資料。  
  
 如需有關如何[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援串流 LOB 資料，請參閱[串流大型物件資料類型在 Oracle 資料庫配接器](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md)。  
  
 如需實作串流您的程式碼，以支援端對端 LOB 資料的資料流中的節點值的詳細資訊，請參閱[串流處理 Oracle 資料庫的 LOB 資料類型使用的 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md)。  
  
## <a name="see-also"></a>另請參閱  
 [開發使用 WCF 通道模型的 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)