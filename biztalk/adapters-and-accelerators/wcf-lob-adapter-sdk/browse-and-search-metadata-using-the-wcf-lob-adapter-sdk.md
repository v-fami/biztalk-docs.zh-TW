---
title: 瀏覽和搜尋中繼資料使用 WCF LOB 配接器 SDK |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fbb4add7-6cc8-4b93-b559-471b6e31c01a
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67f4717c8621b798ff960487dfd156c4f0934dfc
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "22225670"
---
# <a name="browse-and-search-metadata-using-the-wcf-lob-adapter-sdk"></a>瀏覽和搜尋中繼資料使用 WCF LOB 配接器 SDK
本節提供如何藉由分別實作 IMetadataBrowseHandler IMetadataSearchHandler，公開與配接器的瀏覽和搜尋功能的相關資訊。  
  
## <a name="imetadatabrowsehandler"></a>IMetadataBrowseHandler  
 將配接器加入至專案，IMetadataBrowseHandler 讓您瀏覽的類別目錄與配接器支援的作業。 這可讓配接器取用者，以檢視中繼資料資訊，在設計階段，並選取用戶端程序需要的作業。  
  
 使用時[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]將配接器加入至專案中，填入 IMetadataBrowseHandler**選取的合約型別**，**選取類別目錄**，和**可用的類別和作業**方塊。  
  
 ![瀏覽作業](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/b143971c-a50b-4ef2-a973-dfe4aa4fc17e.gif "b143971c-a50b-4ef2-a973-dfe4aa4fc17e")  
  
 下列範例會示範如何實作 IMetadataBrowseHandler。 它會建構 MetadataRetrievalNode 陣列，包含的類別和介面卡所支援作業的詳細資訊。  
  
```csharp  
public class EchoAdapterMetadataBrowseHandler : EchoAdapterHandlerBase, IMetadataBrowseHandler  
    {  
        /// <summary>  
        /// Initializes a new instance of the EchoAdapterMetadataBrowseHandler class  
        /// </summary>  
        public EchoAdapterMetadataBrowseHandler(EchoAdapterConnection connection  
            , MetadataLookup metadataLookup)  
            : base(connection, metadataLookup)  
        {  
        }  
  
        #region IMetadataBrowseHandler Members  
  
        /// <summary>  
        /// Retrieves an array of MetadataRetrievalNodes from the target system.  
        /// The browse operation will return nodes starting from the childStartIndex in the path provided in absoluteName, and the number of nodes returned is limited by maxChildNodes.  
        /// The method should complete within the specified timespan or throw a timeout exception.  
        /// If absoluteName is null or an empty string, return nodes starting from the root + childStartIndex.  
        /// If childStartIndex is zero, then return starting at the node indicated by absoluteName (or the root node if absoluteName is null or empty).  
        /// </summary>  
        public MetadataRetrievalNode[] Browse(string nodeId  
            , int childStartIndex  
            , int maxChildNodes, TimeSpan timeout)  
        {  
            // note we don't support timeout in this sample  
            if (MetadataRetrievalNode.Root.NodeId.Equals(nodeId))  
            {  
                MetadataRetrievalNode node = new MetadataRetrievalNode("EchoMainCategory");  
                node.DisplayName = "Main Category";  
                node.IsOperation = false;  
                node.Description = "This category contains inbound and outbound categories.";  
                node.Direction = MetadataRetrievalNodeDirections.Inbound | MetadataRetrievalNodeDirections.Outbound;  
                return new MetadataRetrievalNode[] { node };  
            }  
            else if( "EchoMainCategory".CompareTo(nodeId) == 0 )  
            {  
                // Inbound operations  
                MetadataRetrievalNode inOpNode1 = new MetadataRetrievalNode("Echo/OnReceiveEcho");  
                inOpNode1.DisplayName = "OnReceiveEcho";  
                inOpNode1.Description = "This operation echoes the location and length of a file dropped in the specified file system.";  
                inOpNode1.Direction = MetadataRetrievalNodeDirections.Inbound;  
                inOpNode1.IsOperation = true;  
                // Outbound operations  
                MetadataRetrievalNode outOpNode1 = new MetadataRetrievalNode("Echo/EchoStrings");  
                outOpNode1.DisplayName = "EchoStrings";  
                outOpNode1.Description = "This operation echoes the incoming string COUNT number of times in a string array.";  
                outOpNode1.Direction = MetadataRetrievalNodeDirections.Outbound;  
                outOpNode1.IsOperation = true;  
                MetadataRetrievalNode outOpNode2 = new MetadataRetrievalNode("Echo/EchoGreetings");  
                outOpNode2.DisplayName = "EchoGreetings";  
                outOpNode2.Description = "This operation echoes the incoming Greeting object COUNT number of times in an array of type Greeting.";  
                outOpNode2.Direction = MetadataRetrievalNodeDirections.Outbound;  
                outOpNode2.IsOperation = true;  
                MetadataRetrievalNode outOpNode3 = new MetadataRetrievalNode("Echo/EchoCustomGreetingFromFile");  
                outOpNode3.DisplayName = "EchoCustomGreetingFromFile";  
                outOpNode3.Description = "This operation echoes the greeting object by reading its instance from a file. The Greeting object's metadata is obtained from a predefined XSD file.";  
                outOpNode3.Direction = MetadataRetrievalNodeDirections.Outbound;  
                outOpNode3.IsOperation = true;  
                return new MetadataRetrievalNode[] { inOpNode1, outOpNode1, outOpNode2, outOpNode3 };  
            }  
  
            return null;  
        }  
  
        #endregion IMetadataBrowseHandler Members  
    }  
```  
  
## <a name="imetadatasearchhandler"></a>IMetadataSearchHandler  
 配接器內實作 IMetadataSearchHandler 能夠輸入搜尋詞彙，例如作業名稱的一部分來搜尋可用作業在執行階段。 這是非常有用，如果您的配接器會包含多項作業，因為您可以輸入搜尋值來限制傳回的作業。  
  
 當使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]IMetadataSearchHandler 解析將配接器加入至專案，搜尋字串中輸入**類別目錄中的搜尋** 方塊中，並傳回相符的清單中的項目**可用的類別和作業**方塊。  
  
 ![搜尋作業](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/48dc9ca6-8697-42bf-9419-5fa35a19937f.gif "48dc9ca6-8697-42bf-9419-5fa35a19937f")  
  
 您也可以執行搜尋使用 svcutil.exe 產生 WSDL 或配接器的 proxy 時，藉由搜尋值傳遞做為查詢字串格式的 op = value。 以下是使用 svcutil.exe 來只傳回回應/EchoStrings 作業資訊的範例。  
  
```  
svcutil.exe “echov2://lobhostname/lobapplication?enableAuthentication=False&op=Echo/EchoStrings” /target:metadata  
  
```  
  
> [!NOTE]
>  [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]不提供預設萬用字元搜尋功能，例如回應 * 或 Echo %%。 這是由配接器的作者，以實作萬用字元或模式比對功能。  
  
 下列範例會示範如何實作 IMetadataSearchHandler。 它會建構 MetadataRetrievalNode 陣列，包含類別和配接器支援的作業的相關資訊。  
  
```csharp  
public class EchoAdapterMetadataSearchHandler : EchoAdapterHandlerBase, IMetadataSearchHandler  
    {  
        /// <summary>  
        /// Initializes a new instance of the EchoAdapterMetadataSearchHandler class  
        /// </summary>  
        public EchoAdapterMetadataSearchHandler(EchoAdapterConnection connection  
            , MetadataLookup metadataLookup)  
            : base(connection, metadataLookup)  
        {  
        }  
  
        #region IMetadataSearchHandler Members  
  
        /// <summary>  
        /// Retrieves an array of MetadataRetrievalNodes (see Microsoft.ServiceModel.Channels) from the target system.  
        /// The search will begin at the path provided in absoluteName, which points to a location in the tree of metadata nodes.  
        /// The contents of the array are filtered by SearchCriteria and the number of nodes returned is limited by maxChildNodes.  
        /// The method should complete within the specified timespan or throw a timeout exception.  If absoluteName is null or an empty string, return nodes starting from the root.  
        /// If SearchCriteria is null or an empty string, return all nodes.  
        /// </summary>  
        public MetadataRetrievalNode[] Search(string nodeId  
            , string searchCriteria  
            , int maxChildNodes, TimeSpan timeout)  
        {  
  
            List<MetadataRetrievalNode> resultList = new List<MetadataRetrievalNode>();  
            if ("OnReceiveEcho".ToLower().Contains(searchCriteria.ToLower()))  
            {  
                MetadataRetrievalNode nodeInbound = new MetadataRetrievalNode("Echo/OnReceiveEcho");  
                nodeInbound.DisplayName = "OnReceiveEcho";  
                nodeInbound.Description = "This operation echos the location and length of a file dropped in the specified file system.";  
                nodeInbound.Direction = MetadataRetrievalNodeDirections.Inbound;  
                nodeInbound.IsOperation = true;  
                resultList.Add(nodeInbound);  
            }  
            if ("EchoStrings".ToLower().Contains(searchCriteria.ToLower()))  
            {  
                MetadataRetrievalNode outOpNode1 = new MetadataRetrievalNode("Echo/EchoStrings");  
                outOpNode1.DisplayName = "EchoStrings";  
                outOpNode1.Description = "This operation echoes the incoming string COUNT number of times in a string array.";  
                outOpNode1.Direction = MetadataRetrievalNodeDirections.Outbound;  
                outOpNode1.IsOperation = true;  
                resultList.Add(outOpNode1);  
            }  
            if ("EchoGreetings".ToLower().Contains(searchCriteria.ToLower()))  
            {  
                MetadataRetrievalNode outOpNode2 = new MetadataRetrievalNode("Echo/EchoGreetings");  
                outOpNode2.DisplayName = "EchoGreetings";  
                outOpNode2.Description = "This operation echoes the incoming Greeting object COUNT number of times in an array of type Greeting.";  
                outOpNode2.Direction = MetadataRetrievalNodeDirections.Outbound;  
                outOpNode2.IsOperation = true;  
                resultList.Add(outOpNode2);  
            }  
            if ("EchoCustomGreetingFromFile".ToLower().Contains(searchCriteria.ToLower()))  
            {  
                MetadataRetrievalNode outOpNode3 = new MetadataRetrievalNode("Echo/EchoCustomGreetingFromFile");  
                outOpNode3.DisplayName = "EchoCustomGreetingFromFile";  
                outOpNode3.Description = "This operation echoes the greeting object by reading its instance from a file. The Greeting object's metadata is obtained from a predefined XSD file.";  
                outOpNode3.Direction = MetadataRetrievalNodeDirections.Outbound;  
                outOpNode3.IsOperation = true;  
                resultList.Add(outOpNode3);  
            }  
            return resultList.ToArray();  
        }  
  
        #endregion IMetadataSearchHandler Members  
    }  
```  
  
## <a name="see-also"></a>另請參閱  
 [開發活動](../../esb-toolkit/development-activities.md)