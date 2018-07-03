---
title: Oracle 資料庫中使用 Ws-metadata 交換取得中繼資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WS-Metadata Exchange, retrieving metadata
- metadata, retrieving using WS-Metadata Exchange
ms.assetid: 6ff34438-7260-489d-a5f0-6e53f8fe43be
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41b3617afcb595a5ead57118c5b4542d12eb3191
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004015"
---
# <a name="get-metadata-using-ws-metadata-exchange-in-oracle-database"></a>Oracle 資料庫中使用 Ws-metadata 交換取得中繼資料
作為[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]會公開您可用來擷取從特定作業的中繼資料的 Ws-metadata Exchange (MEX) 端點[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]。  
  
 WCF 會提供豐富的基礎結構，匯出、 發行、 擷取和匯入服務的相關中繼資料。 WCF 服務，例如配接器，會使用中繼資料，說明如何與服務端點互動，以便 svcutil.exe 之類的工具，可以自動產生用戶端程式碼取用服務。 WCF 服務的中繼資料表示的執行個體**MetadataSet**緊密繫結來定義在 WS-中繼資料交換 (MEX) 中繼資料序列化格式的類型。 您可以建立**MetadataSet**目標使用的介面卡上的作業**MetadataExchangeClient**。  
  
 WCF 支援中繼資料交換是廣泛的主題，以及超出本文的範圍。 如需有關支援在 WCF 中的中繼資料的詳細資訊，請參閱[中繼資料](https://msdn.microsoft.com/library/ms731823.aspx)。 架構、 類別和命名空間，WCF 會公開中繼資料，特別是合適的描述，請參閱 <<c0> [ 中繼資料架構概觀](https://msdn.microsoft.com/library/ms730243.aspx)。 您應該熟悉後再繼續這些 WCF 主題中的 WCF 服務中擷取中繼資料的相關內容。  
  
 下列主題包含有關如何使用資訊**MetadataExchangeClient**來擷取中繼資料從[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
## <a name="using-a-metadataexchangeclient-to-retrieve-metadata"></a>使用 MetadataExchangeClient 來擷取中繼資料  
 若要使用**MetadataExchangeClient**您必須指定連線 URI 和繫結 (**OracleDBBinding**)。 連線 URI 識別要擷取的中繼資料的作業。  
  
 下列各節包含有關如何指定連線 URI、 重要的繫結屬性，以及如何使用資訊**MetadataExchangeClient**從配接器擷取中繼資料。  
  
### <a name="the-connection-uri"></a>連線 URI  
 若要使用**MetadataExchangeClient**您必須提供的 Oracle 連接指定 MEX 端點的作業或您要擷取的中繼資料作業的 URI。 您可以在 連線 URI 中，指定 MEX 端點和目標作業來以下列方式：  
  
- 您必須在查詢字串中包含"wsdl 」 參數。 如果是查詢字串中的第一個參數，則會將它指定後方問號 （？）。 如果不是第一個參數，它應該前面加上連字號 (&)。  
  
- 您必須遵循一或多個"op"參數"wsdl 」 的參數。 每個 「 操作 」 前面加上連字號 (&)，並指定目標作業的訊息動作 (節點 ID)。  
  
  例如，下列連線 URI 中的目標 SCOTT 的 Insert 和 Delete 作業。EMP 資料表中。 「 Wsdl"和"op"參數會反白顯示。  
  
```  
"oracledb://ADAPTER?wsdl&op=http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert&op=http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Delete"  
```  
  
> [!NOTE]
>  如果您想要修改 POLLINGSTMT 作業產生的命名空間您應該在查詢字串中指定 PollingId 參數。  
  
 您將此連線 URI 的傳遞至**MetadataExchangeClient**取決於哪一種多載您用來建立用戶端和從配接器擷取中繼資料的方法。  
  
 如需 Oracle 連接 URI 的詳細資訊，請參閱[建立的 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。  
  
### <a name="binding-properties"></a>繫結屬性  
 當您建立**MetadataExchangeClient**，您必須指定**OracleDBBinding**。  
  
 有數個會影響配接器如何產生中繼資料的繫結屬性。 這些屬性是：  
  
-   **EnableSafeTyping**  
  
-   **UseSchemaInNamespace**  
  
-   **PollingStatement**  
  
> [!IMPORTANT]
>  如果您想要擷取 POLLINGSTMT 作業的中繼資料必須設定**PollingStatement**繫結屬性。  
  
 您應該確定這些繫結屬性已設為 再叫用您的應用程式所需的值**GetMetadata**方法**MetadataExchangeClient**。 如需詳細資訊[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結屬性，請參閱[了解 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。  
  
### <a name="example"></a>範例  
 下列範例會使用**MetadataExchangeClient**為 Insert、 Update、 Delete 與 SCOTT 上的 Select 作業建立的服務描述 （WSDL 文件）。EMP 資料表中。 WSDL 會儲存至檔案，EmpOperations.wsdl。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Collections.ObjectModel;  
  
// Needed for WCF and Oracle Adapter  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
// Needced for MetadataExchangeClient class  
using System.ServiceModel.Description;  
// Needed for ServiceDescription class  
using System.Web.Services;  
  
namespace OracleMetadataExchange  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            //create a binding  
            OracleDBBinding binding = new OracleDBBinding();  
  
            //create a metadata exchange client that will retrieve metadata according to the WS-MEX standard  
            MetadataExchangeClient client = new MetadataExchangeClient(binding);  
            client.SoapCredentials.UserName.UserName = "SCOTT";  
            client.SoapCredentials.UserName.Password = "TIGER";  
  
            //set up an endpoint address and specifies the operations for which we want metadata  
            string connectionUri = "oracledb://ADAPTER?wsdl"  
                + "&op="  
                + "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert"  
                + "&op="  
                + "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Update"  
                + "&op="  
                + "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Delete"  
                + "&op="  
                + "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Select";  
  
            EndpointAddress address = new EndpointAddress(connectionUri);  
  
            //get the metadata  
            MetadataSet ms = client.GetMetadata(address);  
  
            // Check for the metadata set size   
            Collection<MetadataSection> documentCollection = ms.MetadataSections;  
            if (documentCollection != null && documentCollection.Count > 0)  
            {  
                //get the wsdl from the metadata set  
                System.Web.Services.Description.ServiceDescription wsdl = (System.Web.Services.Description.ServiceDescription)documentCollection[0].Metadata;  
  
                //save the wsdl to a file  
                wsdl.Write("EmpOperations.wsdl");  
  
            }  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [從 Oracle 資料庫，以程式設計方式取得中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-programmatically-from-the-oracle-database.md)