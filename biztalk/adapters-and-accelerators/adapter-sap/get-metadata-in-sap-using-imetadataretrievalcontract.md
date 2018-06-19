---
title: 取得中繼資料中使用 IMetadataRetrievalContract SAP |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- how to, search metadata
- searching metadata
- how to, browse metadata
- browsing metadata
ms.assetid: 0944fc39-9ee5-4702-8b52-e0bc87f202c6
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efa36eee26dd9467a71f7e8dd4d28d2e37e26606
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22218270"
---
# <a name="get-metadata-in-sap-using-imetadataretrievalcontract"></a>使用 IMetadataRetrievalContract SAP 中取得中繼資料
[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]公開**IMetadataRetrievalContract**端點可讓您瀏覽及搜尋 SAP 系統成品，以及擷取中繼資料的 Web 服務描述語言 (WSDL) 文件形式作業。  
  
 **IMetadataRetrievalContract**介面由實作[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，並提供中繼資料瀏覽、 搜尋和擷取功能。 除了**IMetadataRetrievalContract**介面，[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]公開**MetadataRetrievalClient**類別，實作介面。 您可以使用**IMetadataRetrievalContract**通道或**MetadataRetrievalClient**才能使用中繼資料; 若要瀏覽、 搜尋和擷取中繼資料中公開的方法會在每個案例相同。  
  
 下列各節提供有關如何使用資訊**IMetadataRetrievalContract**介面。  
  
## <a name="the-imetadataretrievalcontract-interface"></a>IMetadataRetrievalContract 介面  
 下表提供當您使用時所使用的重要類別的相關資訊**IMetadataRetrievalContract**介面。  
  
|類別或介面|Description|  
|------------------------|-----------------|  
|**IMetadataRetrievalContract**介面<br /><br /> (Microsoft.ServiceModel.Channels)|定義**瀏覽**，**搜尋**，和**GetMetadata**方法。 您呼叫這些方法，藉由使用**IMetadataRetrievalContract**通道或**MetadataRetrievalClient**才能使用配接器中繼資料。|  
|**MetadataRetrievalClient**類別<br /><br /> (Microsoft.ServiceModel.Channels)|實作**IMetadataRetrievalContract**介面。 您可以建立這個類別的執行個體，並可藉由提供將它設定為 SAP 系統**SAPBinding**和**EndpointAddress**。 然後您可以叫用其方法與中繼資料一起運作。|  
|**MetadataRetrievalNode**類別<br /><br /> (Microsoft.ServiceModel.Channels)|表示介面卡上的中繼資料節點。 **瀏覽**和**搜尋**方法會傳回此節點類型，而**GetMetadata**方法會採用此節點類型做為參數。|  
|**ServiceDescription**類別<br /><br /> (System.Web.Services.Description)|提供建立和格式化有效的 WSDL 文件檔案的方法。 **GetMetadata**方法會傳回**ServiceDescription**物件。|  
  
 如需有關**IMetadataRetrievalContract**介面， **MetadataRetrievalClient**類別，而**MetadataRetrievalNode**類別，請參閱 < **Microsoft.ServiceModel.Channels**受管理參考在[http://go.microsoft.com/fwlink/?LinkId=105566](http://go.microsoft.com/fwlink/?LinkId=105566)。  
  
### <a name="metadata-node-ids"></a>中繼資料節點識別碼  
 配接器會將它的中繼資料組織為階層式樹狀結構的節點。 此樹狀結構中有兩種類型的中繼資料節點：  
  
-   **作業節點**代表 SAP 成品會呈現配接器的作業。 作業的節點是樹狀結構的分葉。  
  
-   **分類節點**代表 SAP 成品，並不會直接對應的 SAP 成品的群組給配接器上的作業。 分類節點是樹狀結構中; 的分支它們包含其他分類節點和/或運算節點。 例如，RFC 功能群組或 SAP 商務物件會以類別目錄節點表示。  
  
 每個配接器所提出的中繼資料節點識別唯一的節點識別碼。 與節點有關的中繼資料顯示配接器的識別碼的詳細資訊，請參閱[中繼資料的節點識別碼](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md)。 您可以使用這些節點識別碼來指定當您使用的目標 SAP 成品**IMetadataRetrievalContract**介面，以瀏覽、 搜尋及擷取中繼資料。 您可以使用中定義的常數`Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants`和`Microsoft.Adapters.SAP.SAPAdapterConstants.ActionConstants`來協助您建構中繼資料節點識別碼。  
  
### <a name="binding-properties"></a>繫結屬性  
 不論您是使用**IMetadataRetrievalContract**通道或**IMetadataRetrievalClient**若要使用中繼資料，您必須指定**SAPBinding**當您建立執行個體。  
  
 有幾個會影響配接器如何產生中繼資料的繫結屬性。 這些屬性如下：  
  
-   **GenerateFlatfileCompatibleIdocSchema**  
  
-   **ReceiveIDocFormat**  
  
-   **EnableSafeTyping**  
  
-   **FlatFileSegmentIndicator**  
  
 您應該確定這些繫結屬性設定為需要您的應用程式之前開啟中繼資料擷取物件的值。 如需有關 SAP 配接器繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
### <a name="browsing-metadata-nodes"></a>瀏覽中繼資料節點  
 您使用**瀏覽**方法以傳回所包含的所有中繼資料節點中的父節點。 下列範例會瀏覽的 SAP 系統上的前三個 RFC 功能群組。 在此範例中，**用戶端**的執行個體**MetadataRetrievalClient**。  
  
```  
// The first parameter is the node ID.   
// The second parameter is the start index.  
// The third parameter is the maximum number of nodes to return.  
IMetadataRetrievalNode[] nodes = client.Browse(Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, 0, 3);  
```  
  
> [!IMPORTANT]
>  您只能瀏覽類別節點;您無法瀏覽作業節點。  
  
### <a name="searching-for-metadata-nodes"></a>搜尋中繼資料節點  
 您使用**搜尋**方法來執行搜尋的父節點所包含的節點。 您可以指定星號 (\*) 萬用字元。 此字元會比對零個或多個字元。 下列範例會顯示搜尋所有包含字串"BAPI"的 Rfc。 在此範例中，**用戶端**的執行個體**MetadataRetrievalClient**。  
  
```  
// Search for all nodes that contain "BAPI" under the RFC node.  
// The parameters are the parent node ID, the search expression, and   
// the maximum number of nodes to return.  
IMetadataRetrievalNode[] nodes = client.Search(Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, "*BAPI*", int.MaxValue);  
```  
  
> [!IMPORTANT]
>  搜尋只支援一組有限的節點上。 如需有關支援搜尋的節點，以及搜尋運算式中支援的萬用字元的詳細資訊，請參閱[中繼資料的節點識別碼](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md)。  
  
### <a name="retrieving-metadata-wsdl-for-operations"></a>擷取作業的中繼資料 (WSDL)  
 您使用**GetMetadata**方法來擷取群組的作業節點的服務描述 （WSDL 文件）。 下列範例會擷取 BAPI_TRANSACTION_COMMIT RFC 的服務描述。 在此範例中，**用戶端**的執行個體**MetadataRetrievalClient**。 請注意，運算節點的節點識別碼相當於該作業的訊息動作。  
  
```  
// Get a WSDL document that specifies a contract that contains the  
// BAPI_TRANSACTION_COMMIT operation.  
MetadataRetrievalNode[] nodes = new MetadataRetrievalNode[1];  
nodes[0] = new MetadataRetrievalNode();  
nodes[0].NodeId = Microsoft.Adapters.SAP.SAPAdapterConstants.ActionConstants.RfcActionPrefix + "BAPI_TRANSACTION_COMMIT";  
nodes[0].IsOperation = true;  
  
System.Web.Services.Description.ServiceDescription description = client.GetMetadata(nodes);  
```  
  
> [!IMPORTANT]
>  您只需要指定作業中的節點**GetMetadata**方法。  
  
### <a name="using-a-metadataretrievalclient"></a>使用 MetadataRetrievalClient  
 建立和使用**MetadataRetrievalClient**是非常類似任何其他 WCF 用戶端。 您指定端點和執行個體建立用戶端**SAPBinding**。 以宣告方式在組態或命令式程式碼中，您可以這樣做。 然後叫用的方法**MetadataRetrievalClient**瀏覽，搜尋，然後從配接器擷取中繼資料。  
  
 下列範例示範如何使用**MetadataRetrievalClient**來瀏覽，搜尋和擷取中繼資料從[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.ServiceModel;  
using Microsoft.Adapters.SAP;  
using Microsoft.ServiceModel.Channels;  
  
using System.Web.Services.Description;  
  
namespace SapMetaDataBrowseClient  
{  
    class NodeWriter  
    {  
        // This method writes the value of a collection of metadata retrieval nodes  
        // to the console.  
        public void Write(string title, MetadataRetrievalNode[] nodes)  
        {  
            Console.WriteLine(title);  
            Console.WriteLine();  
  
            //Write all the nodes returned to the console.  
            foreach (MetadataRetrievalNode node in nodes)  
            {  
                Console.WriteLine("NodeId = " + node.NodeId);  
                Console.WriteLine("\tDirection   = " + node.Direction.ToString());  
                Console.WriteLine("\tIsOperation = " + node.IsOperation.ToString());  
                Console.WriteLine("\tDisplayName = " + node.DisplayName);  
                Console.WriteLine("\tDescription = " + node.Description);  
            }  
            Console.WriteLine();  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            MetadataRetrievalClient browser = null;  
            NodeWriter nodeWriter = new NodeWriter();  
  
            try  
            {  
                // Create a binding  
                SAPBinding binding = new SAPBinding();  
  
                EndpointAddress address = new EndpointAddress("sap://Client=800;lang=EN@A/YourSAPHost/00");  
  
                browser = new MetadataRetrievalClient(binding, address);  
                browser.ClientCredentials.UserName.UserName = "YourUserName";  
                browser.ClientCredentials.UserName.Password = "YourPassword";  
                browser.Open();  
  
                // Return the nodes directly under the root.  
                // The parameters are the parent node ID, the start index, and the maximum number  
                // of nodes to return.  
                MetadataRetrievalNode[] nodes = browser.Browse(MetadataRetrievalNode.Root.NodeId, 0, int.MaxValue);  
                nodeWriter.Write("Browse results for the root node:", nodes);  
  
                // Return first 3 RFC group nodes.  
                nodes = browser.Browse(Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, 0, 3);  
                nodeWriter.Write(String.Format("Browse results for the first {1} nodes of {0}:", Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, nodes.Length), nodes);  
  
                // Search for first 3 nodes that begin with "BAPI_TRANSACTION" under the RFC node.  
                // The parameters are the parent node ID, the search expression, and the maximum number  
                // of nodes to return.  
                nodes = browser.Search(Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, "*BAPI_TRANSACTION*", 3);  
                nodeWriter.Write(String.Format("Search results for \"*BAPI_TRANSACTION*\" under {0} node:", Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection), nodes);  
  
                // Get a WSDL document that specifies a contract that contains the operations  
                // found in the search and write it to a file.  
                // You could explicitly specify operations as in the following:  
                //    nodes[0] = new MetadataRetrievalNode();  
                //    nodes[0].NodeId = Microsoft.Adapters.SAP.SAPAdapterConstants.ActionConstants.RfcActionPrefix + "BAPI_TRANSACTION_COMMIT";  
                //    nodes[0].IsOperation = true;  
                // Note that the operation NodeId is equivalent to the message action.  
                System.Web.Services.Description.ServiceDescription description = browser.GetMetadata(nodes);  
                description.Write("SampleContract.wsdl");  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
            }  
            finally  
            {  
                if (browser != null)  
                {  
                    if (browser.State == CommunicationState.Opened)  
                        browser.Close();  
                    else  
                        browser.Abort();  
                }  
            }  
        }  
    }  
}  
```  
  
 以下顯示在主控台上此程式的輸出。 您可以看到每個方法所傳回的中繼資料擷取節點的結構。 程式也會寫入 WSDL 文件描述的檔案搜尋傳回的節點所組成的服務合約。 （大部分的 SAP 安裝的服務描述會包含 BAPI_TRANSACTION_COMMIT 和 BAPI_TRANSACTION_ROLLBACK 作業）。  
  
```  
Browse results for the root node:  
  
NodeId = http://Microsoft.LobServices.Sap/2007/03/BAPISECTION/000001  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = BAPI  
        Description = BAPI  
NodeId = http://Microsoft.LobServices.Sap/2007/03/IDOCSECTION/  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = IDOC  
        Description = IDOC  
NodeId = http://Microsoft.LobServices.Sap/2007/03/RFCSECTION/  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = RFC  
        Description = RFC  
NodeId = http://Microsoft.LobServices.Sap/2007/03/TRFCSECTION/  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = TRFC  
        Description = TRFC  
  
Browse results for the first 3 nodes of http://Microsoft.LobServices.Sap/2007/03  
/RFCSECTION/:  
  
NodeId = http://Microsoft.LobServices.Sap/2007/03/RFCGROUP/A  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = Asset Accounting  
        Description = Asset Accounting  
NodeId = http://Microsoft.LobServices.Sap/2007/03/RFCGROUP/S  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = Basis  
        Description = Basis  
NodeId = http://Microsoft.LobServices.Sap/2007/03/RFCGROUP/B  
        Direction   = Inbound, Outbound  
        IsOperation = False  
        DisplayName = Business Information Warehouse  
        Description = Business Information Warehouse  
  
Search results for "*BAPI_TRANSACTION*" under http://Microsoft.LobServices.Sap/2  
007/03/RFCSECTION/ node:  
  
NodeId = http://Microsoft.LobServices.Sap/2007/03/Rfc/BAPI_TRANSACTION_COMMIT  
        Direction   = Inbound, Outbound  
        IsOperation = True  
        DisplayName = BAPI_TRANSACTION_COMMIT  
        Description = Execute external Commit when using BAPIs  
NodeId = http://Microsoft.LobServices.Sap/2007/03/Rfc/BAPI_TRANSACTION_ROLLBACK  
        Direction   = Inbound, Outbound  
        IsOperation = True  
        DisplayName = BAPI_TRANSACTION_ROLLBACK  
        Description = Execute external Rollback when using BAPIs  
  
```  
  
## <a name="using-an-imetadataretrievalcontract-channel"></a>使用 IMetadataRetrievalContract 通道  
 您也可以建立**IMetadataRetrievalContract**通道，並接著使用這個通道來瀏覽、 搜尋及擷取中繼資料從配接器。 (方法簽章是不一樣**MetadataRetrievalClient**類別。)下列範例顯示如何執行這項工作。  
  
```  
…  
//Create a binding and endpoint address.  
SAPBinding binding = new SAPBinding();  
EndpointAddress address = new EndpointAddress("sap://Client=800;lang=EN@A/YourSAPHost/00");  
  
//Create and open a channel factory that will return an IMetadataRetrievalContract object, on which browse, search, and get can be performed.  
ChannelFactory<IMetadataRetrievalContract> factory = new ChannelFactory<IMetadataRetrievalContract>(binding, address);  
factory.Credentials.UserName.UserName = "YourUserName";  
factory.Credentials.UserName.Password = "YourPassword";  
factory.Open();  
  
//Obtain an IMetadataRetrievalContract channel from the factory.  
IMetadataRetrievalContract channel = factory.CreateChannel();  
  
//Perform a search using the channel.  
MetadataRetrievalNode[] nodes = channel.Search(Microsoft.Adapters.SAP.SAPAdapterConstants.MetadataConstants.RfcSection, "BAPI_TRANSACTION*", int.MaxValue);  
…  
```  
  
## <a name="see-also"></a>另請參閱  
 [以程式設計方式從 SAP 擷取中繼資料](../../adapters-and-accelerators/adapter-sap/get-metadata-programmatically-from-sap.md)