---
title: 在 Oracle 資料庫中使用 IMetadataRetrievalContract 取得中繼資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- metadata, retrieving using IMetadataRetrievalContract
ms.assetid: 7d32694f-4384-4c2f-be72-ac52c7b2e9f5
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9510c7ae534251218826a31eea1cc39c8d1f139
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977991"
---
# <a name="get-metadata-in-oracle-database-using-imetadataretrievalcontract"></a>在 Oracle 資料庫中使用 IMetadataRetrievalContract 取得中繼資料
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]公開**IMetadataRetrievalContract**瀏覽及搜尋 Oracle 資料庫成品，以及擷取表單的 Web 服務描述語言 (WSDL 中的作業的中繼資料，您可以使用的端點) 文件。  
  
 **IMetadataRetrievalContract**介面由實作[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，並提供中繼資料瀏覽、 搜尋和擷取功能。 除了**IMetadataRetrievalContract**介面[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]公開**MetadataRetrievalClient**實作介面的類別。 您可以使用**IMetadataRetrievalContract**通道或**MetadataRetrievalClient**才能使用中繼資料; 若要瀏覽、 搜尋及擷取中繼資料中公開的方法是在每個案例相同。  
  
 下列各節提供有關如何使用資訊**IMetadataRetrievalContract**介面。  
  
## <a name="the-imetadataretrievalcontract-interface"></a>IMetadataRetrievalContract 介面  
 下表提供當您使用時所使用的重要類別的相關資訊**IMetadataRetrievalContract**介面。  
  
|類別或介面|描述|  
|------------------------|-----------------|  
|**IMetadataRetrievalContract**介面<br /><br /> (Microsoft.ServiceModel.Channels)|定義**瀏覽**，**搜尋**，並**GetMetadata**方法。 您可以叫用這些方法使用**IMetadataRetrievalContract**通道或**MetadataRetrievalClient**使用配接器中繼資料。|  
|**MetadataRetrievalClient**類別<br /><br /> (Microsoft.ServiceModel.Channels)|Implements **IMetadataRetrievalContract**介面。 您可以建立這個類別的執行個體，並設定 Oracle 資料庫的方法是提供**OracleDBBinding**並**EndpointAddress**。 然後您可以叫用其方法，以使用中繼資料。|  
|**MetadataRetrievalNode**類別<br /><br /> (Microsoft.ServiceModel.Channels)|表示介面卡上的中繼資料節點。 **瀏覽**並**搜尋**方法會傳回此節點類型，而**GetMetadata**方法會採用此節點類型做為參數。|  
|**ServiceDescription**類別<br /><br /> (System.Web.Services.Description)|提供方法來建立和格式化的有效的 WSDL 文件檔案。 **GetMetadata**方法會傳回**ServiceDescription**物件。|  
  
 
### <a name="metadata-node-ids"></a>中繼資料節點識別碼  
 配接器會將其中繼資料組織為階層式樹狀結構的節點。 此樹狀結構內有兩種類型的中繼資料節點：  
  
- **作業節點**代表配接器會呈現 Oracle 資料庫成品的作業。 作業節點是樹狀結構的分葉。  
  
- **類別目錄節點**代表作業的介面卡上 Oracle 資料庫成品並不會直接對應的 Oracle 資料庫成品的群組。 類別目錄節點是樹狀結構; 的分支它們包含其他類別目錄節點和/或作業節點。 例如，Oracle 資料表和封裝被以類別目錄節點。  
  
  每個配接器所顯示的中繼資料節點識別唯一的節點識別碼。 如需有關中繼資料節點識別碼顯示配接器的詳細資訊，請參閱[中繼資料節點識別碼](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md)。 指定目標 Oracle 資料庫成品，當您使用的情況下，您在使用這些節點 Id **IMetadataRetrievalContract**介面來瀏覽、 搜尋及擷取中繼資料。  
  
### <a name="binding-properties"></a>繫結屬性  
 您是否使用**IMetadataRetrievalContract**通道或有**IMetadataRetrievalClient**若要使用的中繼資料，您必須指定**OracleDBBinding**時您建立執行個體。  
  
 有數個會影響配接器如何產生中繼資料的繫結屬性。 這些屬性是：  
  
-   **EnableSafeTyping**  
  
-   **UseSchemaInNamespace**  
  
-   **PollingStatement**  
  
> [!IMPORTANT]
>  如果您想要擷取 POLLINGSTMT 作業的中繼資料必須設定**PollingStatement**繫結屬性。  
  
 您應該確定這些繫結屬性已設為開啟中繼資料擷取物件之前，您的應用程式所需的值。 如需詳細資訊[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結屬性，請參閱[了解 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。  
  
### <a name="browsing-metadata-nodes"></a>瀏覽中繼資料節點  
 您使用**瀏覽**方法來傳回所包含的所有中繼資料節點中的父節點。 下列範例會瀏覽 Oracle 資料庫上的前三個結構描述。 在此範例中，**用戶端**的執行個體**MetadataRetrievalClient**。  
  
```  
// The first parameter is the node ID.   
// The second parameter is the start index.  
// The third parameter is the maximum number of nodes to return.  
                MetadataRetrievalNode[] nodes = client.Browse(MetadataRetrievalNode.Root.NodeId, 0, 3);  
```  
  
> [!IMPORTANT]
>  您只能瀏覽類別節點;您無法瀏覽作業節點。  
  
### <a name="searching-for-metadata-nodes"></a>搜尋中繼資料節點  
 您使用**搜尋**方法，以執行搜尋的父節點所包含的節點。 配接器支援萬用字元搜尋在運算式中;例如，您也可以指定百分比 （%） 比對零或多個字元的萬用字元。 下列範例會示範包含字串"EMP"SCOTT 結構描述中所有資料表的搜尋。 在此範例中，**用戶端**的執行個體**MetadataRetrievalClient**。  
  
```  
// Search for all nodes that contain "EMP" under the SCOTT.Table node.  
// The parameters are the parent node ID, the search expression, and   
// the maximum number of nodes to return.  
IMetadataRetrievalNode[] nodes = client.Search("http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table", "%EMP%", 3);  
  
```  
  
> [!IMPORTANT]
>  搜尋僅適用於一組有限的節點上。 如需有關支援搜尋的節點以及搜尋運算式中支援的萬用字元的詳細資訊，請參閱[中繼資料節點識別碼](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md)。  
  
### <a name="retrieving-metadata-wsdl-for-operations"></a>擷取作業的中繼資料 (WSDL)  
 您使用**GetMetadata**方法來擷取群組的作業節點的服務描述 （WSDL 文件）。 下列範例會擷取服務描述，其中包含所有配接器會呈現 scott 的作業。EMP 資料表，藉由指定其節點識別碼。 在此範例中，**用戶端**的執行個體**MetadataRetrievalClient**。  
  
```  
// Get a service description that contains all of the operations   
// surfaced for the SCOTT.EMP table. The IsOperation  
// property is set false because this is a category node.  
nodes = new MetadataRetrievalNode[1];  
nodes[0] = new MetadataRetrievalNode();  
nodes[0].NodeId = "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP";  
nodes[0].IsOperation = false;  
System.Web.Services.Description.ServiceDescription description = client.GetMetadata(nodes);  
  
```  
  
> [!IMPORTANT]
>  **IsOperation**屬性應該是類別目錄節點和運算節點為 true，則為 false。  
  
### <a name="using-a-metadataretrievalclient"></a>使用 MetadataRetrievalClient  
 建立和使用**MetadataRetrievalClient**是非常類似任何其他 WCF 用戶端。 您可以建立用戶端藉由指定端點和執行個體**OracleDBBinding**。 以宣告方式在組態或命令式程式碼中，您可以這麼做。 然後叫用的方法**MetadataRetrievalClient**瀏覽、 搜尋及擷取配接器的中繼資料。  
  
 下列範例示範如何使用**MetadataRetrievalClient**瀏覽、 搜尋及擷取中繼資料從[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 此範例示範：  
  
-   瀏覽 Oracle 資料庫結構描述的中繼資料樹狀結構的根節點。  
  
-   搜尋名稱中包含字串"EMP"SCOTT 結構描述中的資料表。  
  
-   正在擷取所有 scott 所支援的作業中繼資料。藉由傳遞的類別目錄節點的 EMP 資料表**GetMetadata**方法。  
  
-   藉由傳遞 POLLINGSTMT 作業節點，以擷取 POLLINGSTMT 作業的中繼資料**GetMetadata**方法...  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.ServiceModel;  
using Microsoft.Adapters.OracleDB;  
using Microsoft.ServiceModel.Channels;  
  
using System.Web.Services.Description;  
  
namespace OracleMetadataRetrieval  
{  
    class NodeWriter  
    {  
        // This method writes the value of a collection of metadata retrieval nodes  
        // to the console  
        public void Write(string title, MetadataRetrievalNode[] nodes)  
        {  
            Console.WriteLine(title);  
            Console.WriteLine();  
  
            //write all the nodes returned to the console.  
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
            MetadataRetrievalClient client = null;  
            NodeWriter nodeWriter = new NodeWriter();  
  
            try  
            {  
                // create a binding and   
                // set the PollingStatement binding property if you want to  
                // return metadata for the POLLINGSTMT operation  
                OracleDBBinding binding = new OracleDBBinding();  
                binding.PollingStatement = "SELECT * FROM EMP";  
  
                // Set PollingId parameter if you want to alter the namespace of the POLLINGSTMT operation  
                EndpointAddress address = new EndpointAddress("oracledb://ADAPTER?PollingId=1");  
  
                client = new MetadataRetrievalClient(binding, address);  
                client.ClientCredentials.UserName.UserName = "SCOTT";  
                client.ClientCredentials.UserName.Password = "TIGER";  
                client.Open();  
  
                // Browse for the first 3 (schema) nodes directly under the root  
                // The parameters are the parent Node ID, the start index, and the maximum number  
                // of nodes to return  
                MetadataRetrievalNode[] nodes = client.Browse(MetadataRetrievalNode.Root.NodeId, 0, 3);  
                nodeWriter.Write("Browse results for the root node:", nodes);  
  
                // Search for first 3 tables that contain "EMP" in the SCOTT schema  
                // The parameters are the parent node ID, the search expression, and the maximum number  
                // of nodes to return  
                nodes = client.Search("http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table", "%EMP%", 3);  
                nodeWriter.Write(String.Format("Search results for \"%EMP%\" under {0} node:", "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table"), nodes);  
  
                // Get a WSDL document that specifies a contract that contains the operations  
                // surfaced for the SCOTT.EMP table. The IsOperation property is set false  
                // because this is a category node.  
                nodes = new MetadataRetrievalNode[1];  
                nodes[0] = new MetadataRetrievalNode();  
                nodes[0].NodeId = "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP";  
                nodes[0].IsOperation = false;  
                System.Web.Services.Description.ServiceDescription description = client.GetMetadata(nodes);  
                description.Write("EmpTableContract.wsdl");  
  
                // Get a WSDL document that specifies a contract that contains the   
                // the POLLINGSTMT operation. The IsOperation property is set true  
                // because this is an operation node.  
                // Note that the operation NodeId is equivalent to the message action.  
                nodes = new MetadataRetrievalNode[1];  
                nodes[0] = new MetadataRetrievalNode();  
                nodes[0].NodeId = "http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMT";  
                nodes[0].IsOperation = true;  
                description = client.GetMetadata(nodes);  
                description.Write("PollingContract.wsdl");  
  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
            }  
            finally  
            {  
                if (client != null)  
                {  
                    if (client.State == CommunicationState.Opened)  
                        client.Close();  
                    else  
                        client.Abort();  
                }  
            }  
        }  
    }  
}  
```  
  
 以下顯示在主控台上此程式的輸出。 您可以看到每個方法所傳回的中繼資料擷取節點的結構。 也計劃會將兩個 WSDL 文件寫入檔案中。  
  
```  
Browse results for the root node:  
  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/ADAPTERTEST  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = ADAPTERTEST  
        Description = Owned By ADAPTERTEST  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/ADAPTEST  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = ADAPTEST  
        Description = Owned By ADAPTEST  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/ADMIN123  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = ADMIN123  
        Description = Owned By ADMIN123  
  
Search results for "%EMP%" under http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table node:  
  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/AEMP  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = AEMP  
        Description = Table.AEMP  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = EMP  
        Description = Table.EMP  
NodeId = http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP1  
        Direction   = Outbound  
        IsOperation = False  
        DisplayName = EMP1  
        Description = Table.EMP1  
```  
  
## <a name="using-an-imetadataretrievalcontract-channel"></a>使用 IMetadataRetrievalContract 通道  
 您也可以建立**IMetadataRetrievalContract**通道，然後使用此通道瀏覽、 搜尋及擷取配接器的中繼資料。 (是針對相同的方法簽章**MetadataRetrievalClient**類別。)下列範例顯示如何執行這項工作。  
  
```  
…  
//Create a binding and endpoint address.  
OracleDBBinding binding = new OracleDBBinding();  
EndpointAddress address = new EndpointAddress("oracledb://ADAPTER/");  
  
//Create and open a channel factory that will return an IMetadataRetrievalContract object, on which browse, search, and get can be performed.  
ChannelFactory<IMetadataRetrievalContract> factory = new ChannelFactory<IMetadataRetrievalContract>(binding, address);  
factory.Credentials.UserName.UserName = "SCOTT";  
factory.Credentials.UserName.Password = "TIGER";  
factory.Open();  
  
//Obtain an IMetadataRetrievalContract channel from the factory.  
IMetadataRetrievalContract channel = factory.CreateChannel();  
  
//Perform a search using the channel.  
MetadataRetrievalNode[] nodes = channel.Search("http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table", "%EMP%", int.MaxValue);  
…  
```  
  
## <a name="see-also"></a>另請參閱  
 [從 Oracle 資料庫，以程式設計方式取得中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-programmatically-from-the-oracle-database.md)