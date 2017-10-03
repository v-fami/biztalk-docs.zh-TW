---
title: "取得中繼資料在 Oracle 資料庫中使用 IMetadataRetrievalContract |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: metadata, retrieving using IMetadataRetrievalContract
ms.assetid: 7d32694f-4384-4c2f-be72-ac52c7b2e9f5
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 132ad3f64d377a3bfcbf7b1b2303e1c0de0c612f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="get-metadata-in-oracle-database-using-imetadataretrievalcontract"></a>使用 IMetadataRetrievalContract Oracle 資料庫中取得中繼資料
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]公開**IMetadataRetrievalContract**可讓您瀏覽和搜尋 Oracle 資料庫成品並擷取作業的 Web 服務描述語言 (WSDL 格式的中繼資料端點) 文件。  
  
 **IMetadataRetrievalContract**介面由實作[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，並提供中繼資料瀏覽、 搜尋和擷取功能。 除了**IMetadataRetrievalContract**介面，[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]公開**MetadataRetrievalClient**類別，實作介面。 您可以使用**IMetadataRetrievalContract**通道或**MetadataRetrievalClient**才能使用中繼資料; 若要瀏覽、 搜尋和擷取中繼資料中公開的方法會在每個案例相同。  
  
 下列各節提供有關如何使用資訊**IMetadataRetrievalContract**介面。  
  
## <a name="the-imetadataretrievalcontract-interface"></a>IMetadataRetrievalContract 介面  
 下表提供當您使用時所使用的重要類別的相關資訊**IMetadataRetrievalContract**介面。  
  
|類別或介面|Description|  
|------------------------|-----------------|  
|**IMetadataRetrievalContract**介面<br /><br /> (Microsoft.ServiceModel.Channels)|定義**瀏覽**，**搜尋**，和**GetMetadata**方法。 您呼叫這些方法，藉由使用**IMetadataRetrievalContract**通道或**MetadataRetrievalClient**才能使用配接器中繼資料。|  
|**MetadataRetrievalClient**類別<br /><br /> (Microsoft.ServiceModel.Channels)|實作**IMetadataRetrievalContract**介面。 您可以建立這個類別的執行個體，並可藉由提供設定 Oracle 資料庫的**OracleDBBinding**和**EndpointAddress**。 然後您可以叫用其方法與中繼資料一起運作。|  
|**MetadataRetrievalNode**類別<br /><br /> (Microsoft.ServiceModel.Channels)|表示介面卡上的中繼資料節點。 **瀏覽**和**搜尋**方法會傳回此節點類型，而**GetMetadata**方法會採用此節點類型做為參數。|  
|**ServiceDescription**類別<br /><br /> (System.Web.Services.Description)|提供建立和格式化有效的 WSDL 文件檔案的方法。 **GetMetadata**方法會傳回**ServiceDescription**物件。|  
  
 
### <a name="metadata-node-ids"></a>中繼資料節點識別碼  
 配接器會將它的中繼資料組織為階層式樹狀結構的節點。 此樹狀結構中有兩種類型的中繼資料節點：  
  
-   **作業節點**表示 Oracle 資料庫成品會呈現配接器的作業。 作業的節點是樹狀結構的分葉。  
  
-   **分類節點**代表 Oracle 資料庫成品並不會直接對應的 Oracle 資料庫成品的群組給配接器上的作業。 分類節點是樹狀結構中; 的分支它們包含其他分類節點和/或運算節點。 例如，Oracle 資料表和封裝會以類別目錄節點表示。  
  
 每個配接器所提出的中繼資料節點識別唯一的節點識別碼。 與節點有關的中繼資料顯示配接器的識別碼的詳細資訊，請參閱[中繼資料的節點識別碼](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md)。 您可以使用這些節點識別碼來使用時，指定目標 Oracle 資料庫成品**IMetadataRetrievalContract**介面，以瀏覽、 搜尋及擷取中繼資料。  
  
### <a name="binding-properties"></a>繫結屬性  
 不論您是使用**IMetadataRetrievalContract**通道或**IMetadataRetrievalClient**若要使用中繼資料，您必須指定**OracleDBBinding**時您建立執行個體。  
  
 有幾個會影響配接器如何產生中繼資料的繫結屬性。 這些屬性如下：  
  
-   **EnableSafeTyping**  
  
-   **UseSchemaInNamespace**  
  
-   **PollingStatement**  
  
> [!IMPORTANT]
>  如果您想要擷取 POLLINGSTMT 作業的中繼資料必須先設定**PollingStatement**繫結屬性。  
  
 您應該確定這些繫結屬性設定為需要您的應用程式之前開啟中繼資料擷取物件的值。 如需有關[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結屬性，請參閱[閱讀有關 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。  
  
### <a name="browsing-metadata-nodes"></a>瀏覽中繼資料節點  
 您使用**瀏覽**方法以傳回所包含的所有中繼資料節點中的父節點。 下列範例會瀏覽 Oracle 資料庫上的前三個結構描述。 在此範例中，**用戶端**的執行個體**MetadataRetrievalClient**。  
  
```  
// The first parameter is the node ID.   
// The second parameter is the start index.  
// The third parameter is the maximum number of nodes to return.  
                MetadataRetrievalNode[] nodes = client.Browse(MetadataRetrievalNode.Root.NodeId, 0, 3);  
```  
  
> [!IMPORTANT]
>  您只能瀏覽類別節點;您無法瀏覽作業節點。  
  
### <a name="searching-for-metadata-nodes"></a>搜尋中繼資料節點  
 您使用**搜尋**方法來執行搜尋的父節點所包含的節點。 配接器支援萬用字元搜尋在運算式中。例如，您可以指定百分比 （%） 萬用字元來比對零個或多個字元。 下列範例會示範包含字串"EMP"SCOTT 結構描述中的所有資料表中搜尋。 在此範例中，**用戶端**的執行個體**MetadataRetrievalClient**。  
  
```  
// Search for all nodes that contain "EMP" under the SCOTT.Table node.  
// The parameters are the parent node ID, the search expression, and   
// the maximum number of nodes to return.  
IMetadataRetrievalNode[] nodes = client.Search("http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table", "%EMP%", 3);  
  
```  
  
> [!IMPORTANT]
>  搜尋只支援一組有限的節點上。 如需有關支援搜尋的節點，以及搜尋運算式中支援的萬用字元的詳細資訊，請參閱[中繼資料的節點識別碼](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md)。  
  
### <a name="retrieving-metadata-wsdl-for-operations"></a>擷取作業的中繼資料 (WSDL)  
 您使用**GetMetadata**方法來擷取群組的作業節點的服務描述 （WSDL 文件）。 下列範例會擷取服務描述，其中包含的所有作業，配接器提供諸如 scott。EMP 資料表，藉由指定其節點識別碼。 在此範例中，**用戶端**的執行個體**MetadataRetrievalClient**。  
  
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
>  **IsOperation**屬性應為分類節點和運算節點的 true false。  
  
### <a name="using-a-metadataretrievalclient"></a>使用 MetadataRetrievalClient  
 建立和使用**MetadataRetrievalClient**是非常類似任何其他 WCF 用戶端。 您指定端點和執行個體建立用戶端**OracleDBBinding**。 以宣告方式在組態或命令式程式碼中，您可以這樣做。 然後叫用的方法**MetadataRetrievalClient**瀏覽，搜尋，然後從配接器擷取中繼資料。  
  
 下列範例示範如何使用**MetadataRetrievalClient**來瀏覽，搜尋和擷取中繼資料從[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 此範例示範：  
  
-   瀏覽 Oracle 資料庫結構描述的中繼資料樹狀結構的根節點。  
  
-   搜尋名稱含有字串"EMP"SCOTT 結構描述中的資料表。  
  
-   擷取所有 scott 支援作業的中繼資料。藉由傳遞至類別目錄節點 EMP 資料表**GetMetadata**方法。  
  
-   透過傳遞 POLLINGSTMT 作業節點，以擷取中繼資料 POLLINGSTMT 作業**GetMetadata**方法...  
  
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
  
 以下顯示在主控台上此程式的輸出。 您可以看到每個方法所傳回的中繼資料擷取節點的結構。 也程式會將兩份 WSDL 文件寫入檔案中。  
  
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
 您也可以建立**IMetadataRetrievalContract**通道，並接著使用這個通道來瀏覽、 搜尋及擷取中繼資料從配接器。 (方法簽章是不一樣**MetadataRetrievalClient**類別。)下列範例顯示如何執行這項工作。  
  
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
 [以程式設計方式從 Oracle 資料庫中取得中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-programmatically-from-the-oracle-database.md)