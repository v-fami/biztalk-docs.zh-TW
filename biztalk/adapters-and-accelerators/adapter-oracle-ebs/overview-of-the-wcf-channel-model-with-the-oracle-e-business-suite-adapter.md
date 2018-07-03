---
title: 使用 Oracle E-business Suite 配接器的 WCF 通道模型概觀 |Microsoft Docs
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
ms.openlocfilehash: bcabe727b720c2319b253517ea78c573242df76c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987431"
---
# <a name="overview-of-the-wcf-channel-model-with-the-oracle-e-business-suite-adapter"></a>使用 Oracle E-business Suite 配接器的 WCF 通道模型概觀
在叫用作業[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]，您的程式碼做為 WCF 用戶端，並將傳出作業傳送至配接器。 在 WCF 通道模型中，您的程式碼會叫用介面卡上的作業，透過通道傳送要求訊息。  
  
 若要叫用輸入的作業，例如接收以輪詢為基礎的資料變更訊息使用**輪詢**配接器，您的程式碼做為 WCF 服務，並從配接器接收輸入的作業提供的運算。 換句話說，您的程式碼會接收要求訊息從配接器透過通道。  
  
 在本節中的主題提供使用的概觀[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用 WCF 通道模型。  
  
## <a name="wcf-channel-model-overview"></a>WCF 通道模型概觀  
 用戶端和服務交換的 SOAP 訊息來進行通訊。 WCF 通道模型是低層級的抽象概念，此訊息交換。 它提供介面和類型，可讓您傳送和接收訊息所使用的是稱為通道堆疊的多層式通訊協定堆疊。 堆疊的每個圖層由通道所組成，每一個色頻建立從 WCF 繫結。 最低層級是傳輸通道。 傳輸通道會實作服務和用戶端之間的基礎傳輸機制，並呈現較高的層級 （和最終取用的應用程式） 每個訊息**System.ServiceModel.Message**。 WCF**訊息**類別是抽象的 SOAP 訊息。 WCF 提供數個通道介面，稱為通道形狀，模型的基本 SOAP 訊息交換模式，例如要求-回覆或單向。 WCF 傳輸繫結提供實作的其中一個或多個更新版本階層的通道形狀可用來傳送和接收訊息。 如需有關 WCF 通道模型的詳細資訊，請查看 < 通道模型概觀 > [ http://go.microsoft.com/fwlink/?LinkId=82614 ](http://go.microsoft.com/fwlink/?LinkId=82614)。  
  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]是公開為 WCF 服務的 Oracle E-business Suite 成品的 WCF 自訂傳輸繫結。  
  
## <a name="supported-channel-shapes-for-the-oracle-e-business-suite-adapter"></a>Oracle E-business Suite 配接器的支援通道形狀  
 配接器實作下列的 WCF 通道形狀：  
  
- **IRequestChannel** (**System.ServiceModel.Channels.IRequestChannel**)。 **IRequestChannel**介面會實作要求-回覆訊息交換的用戶端。 您可以使用**IRequestChannel**若要執行您要使用回應的作業，例如若要執行 SELECT 查詢在介面資料表上。  
  
- **IOutputChannel** (**System.ServiceModel.Channels.IOutputChannel**)。 此圖形會實作單向訊息交換的用戶端。 您可以使用**IOutputChannel**叫用作業，您不需要使用的回應，例如若要呼叫沒有 OUT 參數的程序。  
  
  > [!IMPORTANT]
  >  所有基礎呼叫，配接器以 Oracle 用戶端都是同步的。 這包括對 Oracle 用戶端是透過叫用作業的結果**IOutputChannel**。 當您使用**IOutputChannel**，配接器會捨棄從 Oracle 用戶端收到的回應。  
  
- **IInputChannel** (**System.ServiceModel.Channels.IInputChannel**)。 此圖形會實作服務端的單向訊息交換。 您使用**IInputChannel**從配接器接收輸入的訊息。  
  
  讓任何 WCF 繫結[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]用以提供應用程式程式碼的通道處理站模式。 您使用**Microsoft.Adapters.OracleEBSBinding**建立的執行個體的物件：  
  
- **System.ServiceModel.ChannelFactory\<IRequestChannel\>** 提供**IRequestChannel**通道可用來叫用的介面卡上的要求-回應作業。  
  
- **System.ServiceModel.ChannelFactory\<IOutputChannel\>** 提供**IOutputChannel**通道可用來叫用的介面卡上的單向作業。  
  
- **System.ServiceModel.IChannelListener\<IInputChannel\>** 提供**IInputChannel**可用來從配接器接收輸入的訊息的通道。  
  
### <a name="creating-messages-for-the-oracle-enterprise-business-solution-in-the-wcf-channel-model"></a>正在建立 WCF 通道模型中的 Oracle 企業商務解決方案的訊息  
 在 WCF **System.ServiceModel.Channels.Message**類別提供在記憶體中表示 SOAP 訊息。 您建立**訊息**執行個體，藉由叫用靜態**Message.Create**方法。  
  
 有兩個重要的部分，您必須指定當您建立的 SOAP 訊息**訊息**執行個體來傳送至[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。  
  
- 訊息的動作是屬於 SOAP 訊息標頭的字串。 [訊息] 動作會識別應該叫用 Oracle E-business suite 的作業。 下面顯示來叫用指定的訊息動作**客戶介面**下方的並行處理程式**應收帳款**Oracle E-business Suite 中的應用程式： `ConcurrentPrograms/AR/RACUST`。  
  
- 訊息內文包含作業的參數資料。 訊息內文由語式正確對應至所預期的訊息結構描述的 XML 組成[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]要求的作業。 下列的訊息本文會指定要求訊息來叫用**客戶介面**並行處理程式。  
  
  ```  
  <RACUST xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/ConcurrentPrograms/AR">  
    <Description>Customer Interface Program</Description>  
    <StartTime></StartTime>  
    <CREATE_RECIPROCAL_CUSTOMER>Yes</CREATE_RECIPROCAL_CUSTOMER>  
    <ORG_ID>203</ORG_ID>  
  </RACUST>  
  
  ```  
  
  如需[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]訊息結構描述和訊息作業的動作，請參閱[訊息和訊息結構描述，BizTalk adapter for Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)。  
  
  **建立**方法多載，並提供許多不同的選項，來提供訊息內文。 下列程式碼示範如何建立**訊息**使用的執行個體**XmlReader**提供訊息內文。 在此程式碼，是從檔案讀取訊息主體。  
  
```  
XmlReader readerIn = XmlReader.Create("ConcProgRequest.xml");  
Message messageIn = Message.CreateMessage(MessageVersion.Default,  
    "ConcurrentPrograms/AR/RACUST",  
    readerIn);  
```  
  
 其中，ConProgRequest.xml 包含要求訊息。  
  
> [!IMPORTANT]
>  您必須提供中的訊息動作您**訊息**執行個體。 這通常是何時**訊息**建立執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [開發 Oracle E-business Suite 應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-channel-model.md)