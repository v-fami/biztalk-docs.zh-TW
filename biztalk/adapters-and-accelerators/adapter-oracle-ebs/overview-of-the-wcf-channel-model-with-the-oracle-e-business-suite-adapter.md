---
title: Oracle E-business Suite 配接器的 WCF 通道模型概觀 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3afd2a97-5734-4c25-87a3-702d8461898b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5317099b1a576c9dd4e0b13593c16f4ef3a6831
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25963252"
---
# <a name="overview-of-the-wcf-channel-model-with-the-oracle-e-business-suite-adapter"></a>Oracle E-business Suite 配接器的 WCF 通道模型概觀
在叫用作業[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]，您的程式碼做為 WCF 用戶端，並將傳出作業傳送至配接器。 在 WCF 通道模型中，您的程式碼會透過通道傳送的要求訊息叫用的介面卡上的作業。  
  
 要叫用傳入的作業，例如輪詢基礎資料變更使用接收訊息**輪詢**作業提供的配接器，您的程式碼做為 WCF 服務，並從配接器接收傳入的作業。 換句話說，您的程式碼會接收要求訊息從配接器透過通道。  
  
 本節中的主題提供使用概觀[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]WCF 通道模型。  
  
## <a name="wcf-channel-model-overview"></a>WCF 通道模型概觀  
 用戶端和服務交換的 SOAP 訊息來進行通訊。 WCF 通道模型是低層級的抽象概念，這個訊息交換。 它提供介面和類型，可讓您傳送和接收訊息所使用的是稱為通道堆疊的多層式通訊協定堆疊。 堆疊的每個圖層由通道時，所組成，且每個通道會建立從 WCF 繫結。 最低層級是傳輸通道。 傳輸通道會實作服務的用戶端之間的基礎傳輸機制，並呈現較高的層級 （及最終使用的應用程式） 的每個訊息**System.ServiceModel.Message**。 WCF**訊息**類別是抽象的 SOAP 訊息。 WCF 提供數個通道介面，稱為通道形狀，建立模型的基本 SOAP 訊息交換模式，例如要求-回覆或單向。 WCF 傳輸繫結提供實作的其中一個或多個更高層次的通道形狀可用來傳送和接收訊息。 WCF 通道模型的詳細資訊，請參閱 < 通道模型概觀 >，網址[http://go.microsoft.com/fwlink/?LinkId=82614](http://go.microsoft.com/fwlink/?LinkId=82614)。  
  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]是 WCF 自訂傳輸繫結會公開為 WCF 服務的 Oracle E-business Suite 成品。  
  
## <a name="supported-channel-shapes-for-the-oracle-e-business-suite-adapter"></a>支援 Oracle E-business Suite 配接器的通道形狀  
 配接器實作下列的 WCF 通道形狀：  
  
-   **IRequestChannel** (**System.ServiceModel.Channels.IRequestChannel**)。 **IRequestChannel**介面實作的用戶端的要求-回覆訊息交換。 您可以使用**IRequestChannel**若要執行您要使用回應的作業，例如若要執行 SELECT 查詢介面資料表上。  
  
-   **IOutputChannel** (**System.ServiceModel.Channels.IOutputChannel**)。 此圖形會實作單向訊息交換的用戶端。 您可以使用**IOutputChannel**叫用作業，您不需要耗用的回應，例如若要呼叫的程序沒有 OUT 參數。  
  
    > [!IMPORTANT]
    >  所有基礎呼叫配接器對 Oracle 用戶端為同步。 這包括透過叫用作業的結果將會是 Oracle 用戶端呼叫**IOutputChannel**。 當您使用**IOutputChannel**，配接器會捨棄對 Oracle 用戶端從收到的回應。  
  
-   **IInputChannel** (**System.ServiceModel.Channels.IInputChannel**)。 此圖形會實作服務端的單向訊息交換。 您使用**IInputChannel**從配接器接收內送的訊息。  
  
 像任何 WCF 繫結，[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]用以提供應用程式程式碼的通道處理站模式。 您使用**Microsoft.Adapters.OracleEBSBinding**物件建立的執行個體：  
  
-   **System.ServiceModel.ChannelFactory\<IRequestChannel\>** 提供**IRequestChannel**通道可用來叫用的介面卡上的要求-回應作業。  
  
-   **System.ServiceModel.ChannelFactory\<IOutputChannel\>** 提供**IOutputChannel**通道可用來叫用的介面卡上的單向作業。  
  
-   **System.ServiceModel.IChannelListener\<IInputChannel\>** 提供**IInputChannel**可用來從配接器接收內送的訊息的通道。  
  
### <a name="creating-messages-for-the-oracle-enterprise-business-solution-in-the-wcf-channel-model"></a>正在建立 「 訊息 Oracle Enterprise 商務解決方案中的 WCF 通道模型  
 在 WCF 中**System.ServiceModel.Channels.Message**類別會提供在記憶體中表示 SOAP 訊息。 您建立**訊息**叫用靜態執行個體**Message.Create**方法。  
  
 有兩個重要的部分 SOAP 訊息，您必須指定當您建立**訊息**將傳送至執行個體[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。  
  
-   訊息動作是 SOAP 訊息標頭的字串。 訊息動作識別 Oracle E-business suite 中叫用的作業。 下列範例示範叫用指定的訊息動作**客戶介面**下的並行程式**應收帳款**Oracle E-business Suite 中的應用程式： `ConcurrentPrograms/AR/RACUST`。  
  
-   訊息內文包含作業的參數資料。 訊息本文由格式正確對應至所預期的訊息結構描述的 XML 組成[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]要求的作業。 下列的訊息本文指定要求訊息來叫用**客戶介面**並行處理程式。  
  
    ```  
    <RACUST xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/ConcurrentPrograms/AR">  
      <Description>Customer Interface Program</Description>  
      <StartTime></StartTime>  
      <CREATE_RECIPROCAL_CUSTOMER>Yes</CREATE_RECIPROCAL_CUSTOMER>  
      <ORG_ID>203</ORG_ID>  
    </RACUST>  
  
    ```  
  
 如需有關資訊[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]訊息結構描述和訊息作業的動作，請參閱[訊息和訊息結構描述，BizTalk adapter for Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)。  
  
 **建立**方法多載，而且提供了許多不同的選項來提供訊息內文。 下列程式碼示範如何建立**訊息**所使用的執行個體**XmlReader**提供訊息內文。 在此程式碼，是從檔案讀取訊息本文。  
  
```  
XmlReader readerIn = XmlReader.Create("ConcProgRequest.xml");  
Message messageIn = Message.CreateMessage(MessageVersion.Default,  
    "ConcurrentPrograms/AR/RACUST",  
    readerIn);  
```  
  
 其中，ConProgRequest.xml 包含要求訊息。  
  
> [!IMPORTANT]
>  您必須提供中的訊息動作您**訊息**執行個體。 這通常是當**訊息**建立執行個體。  
  
## <a name="see-also"></a>請參閱  
 [開發 Oracle E-business Suite 應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-channel-model.md)