---
title: "WCF LOB Adapter SDK 的架構概觀 |Microsoft 文件"
description: "處理常式，通道實作，連線管理、 中繼資料，然後使用 WSDL 中 WCF LOB 配接器 SDK 簡介"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dbd9b63c-54a4-4f63-b3a8-8600f6009a74
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd86d2104fff0e227d9cdda4c9fb3faf1ea7cb84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="architecture-overview-of-the-wcf-lob-adapter-sdk"></a>WCF LOB Adapter SDK 的架構概觀
[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]建置於 WCF 通道模型之上，並提供設計階段和執行階段擴充功能，讓配接器開發人員建立有大型且動態的中繼資料的特定業務系統的配接器。 建立使用的配接器[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]呈現給取用者做為自訂的 WCF 繫結。 下圖顯示的內部架構和主要元件 WCF LOB 配接器 SDK。  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/7183bded-465e-45b9-af78-fbb87cf2df92.gif "7183bded-465e-45b9-af78-fbb87cf2df92")  
  
## <a name="handlers"></a>處理常式  
 *處理常式*定義配接器支援的訊息交換模式。  
  
 下表摘要說明可用的處理常式型別，其功能，而[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]它們所對應的通道。  
  
|**處理常式型別**|**函數**|**對應至 WCF 通道**|  
|---|---|---|  
|`Microsoft.ServiceModel.Channels.Common.IOutboundHandler`|支援單向傳送或要求/回應模式。|IOutputChannel，<br /><br /> IRequestChannel|  
|`Microsoft.ServiceModel.Channels.Common.IAsyncOutboundHandler`|支援非同步單向傳送或要求/回應模式。|IOutputChannel，<br /><br /> IRequestChannel|  
|`Microsoft.ServiceModel.Channels.Common.IInboundHandler`|支援單向接收管線或回覆模式。|IInputChannel，<br /><br /> IReplyChannel|  
|`Microsoft.ServiceModel.Channels.Common.IAsyncInboundHandler`|單向方法的支援非同步變異或收到回覆模式。|IInputChannel<br /><br /> IReplyChannel|  
|`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler`|支援的瀏覽的目標系統上的中繼資料。|IRequestChannel|  
|`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler`|支援搜尋的目標系統上的中繼資料。|IRequestChannel|  
|`Microsoft.ServiceModel.Channels.Common.IMetadataResolverHandler`|支援擷取中繼資料，從目標系統。|IRequestChannel|  
  
## <a name="channel-implementation"></a>通道實作  
 使用所建置的配接器[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]基本上就是傳輸通道 (System.ServiceModel.Channels.IServiceListner)。 使用所建置的配接器[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]會呈現給取用者為 WCF 繫結，繫結用來建立通道堆疊的位置。 這個繫結可以視為等其他預先定義的 WCF 繫結，例如 BasicHttpBinding、 WsHttpBinding，以及 nettcpbinding 等，並可以透過 app.config 或在程式碼中用戶端應用程式時設定呼叫的服務。 此繫結包含繫結項目，配接器所衍生自 T:System.ServiceModel.Channels.TransportBindingElement 類別的索引鍵繫結項目已排序的集合。 在輸出的案例中，[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]執行階段使用通道處理站建立介面卡 （也就是傳輸通道）。 在輸入案例中，[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]執行階段使用的通道接聽程式的服務應用程式中的傳入通道。  執行階段以及設計階段的訊息會通過此元件。  
  
## <a name="connection-factory-connection-and-connection-uri-builder"></a>連線 factory、 連接和連接 URI 產生器  
 *ConnectionFactory*建立 URI 和使用者的認證為基礎的連接，提供處理站模式。 如需詳細資訊，請參閱`Microsoft.ServiceModel.Channels.Common.IConnectionFactory`。  
  
 *連接*定義低階通訊合約，與目標系統，並且會封裝原生通訊應用程式開發介面和連接控制代碼。 如需詳細資訊，請參閱`Microsoft.ServiceModel.Channels.Common.IConnection`。  
  
 *連接 Uri 產生器*可讓配接器取用者以程式設計方式建置連接 Uri 特定不知情的情況下的語法。 如需詳細資訊，請參閱`Microsoft.ServiceModel.Channels.Common.ConnectionUri`。  
  
## <a name="connection-management"></a>連接管理  
 *連接管理*負責的存留期管理配接器的連接。 它在內部會保存連接集區可供使用。 此連線集區是認證和 URI 為基礎。 這個認證包含使用者名稱和定義的安全性內容連接的密碼下執行。  
  
 當使用相同的認證和 URI 時，任何在相同連接處理站所開啟的通道會取得連接從集區如果已經有一個可用。  
  
 連接集區管理員會保留該 URI 不論認證和通道處理站與界限之間有多少的開啟連接的記錄。 例如，在一個系統中，您可以有兩個使用者具有不同的認證，這表示有兩個連線到系統的通道處理站。  
  
> [!NOTE]
>  配接器可能會有所限制，相對於支援的連接數目通常受限於系統資源。  
  
 為了設定連接集區，設定配接器開發人員[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供兩個類別：`Microsoft.ServiceModel.Channels.Common.ConnectionPoolSettings`和`Microsoft.ServiceModel.Channels.Common.ConnectionManagerSettings`。  
  
## <a name="metadata-management"></a>中繼資料管理  
 *中繼資料管理*負責目標系統的中繼資料快取的物件導向表示。 中繼資料可以保留相同的快取存取跨所有認證，或快取的每個認證為基礎。  
  
 中繼資料生命週期開始其設計階段定義，並在執行階段會繼續透過使用情形。 在設計階段配接器開發人員必須識別一組作業，並必須產生必要的 WSDL 和用戶端端 proxy。 在執行階段，配接器架構為基礎的配接器會使用預先定義的中繼資料，來解譯從目標系統呼叫傳回的訊息。  
  
 為了協助進行此設定中繼資料的配接器寫入器，配接器架構提供三個類別， `Microsoft.ServiceModel.Channels.Common.CacheSettings`，`Microsoft.ServiceModel.Channels.Common.MetadataSettings`和`Microsoft.ServiceModel.Channels.Common.CommonCacheSettings`。  
  
## <a name="wsdl-builder"></a>WSDL 產生器  
 *WSDL 產生器*提供自動的 WSDL 產生從 WCF LOB Adapter SDK 的內部中繼資料物件模型 （它會覆寫需要自訂 WSDL 產生的）。  
  
 請參閱`Microsoft.ServiceModel.Channels.Common.IWsdlRetrieval`如需詳細資訊。  
  
## <a name="metadata-browsesearch"></a>中繼資料瀏覽/搜尋  
 *中繼資料瀏覽/搜尋*允許瀏覽和搜尋 LOB 的所有中繼資料。  
  
 如需詳細資訊，請參閱`Microsoft.ServiceModel.Channels.IMetadataRetrievalContract`。  
  
## <a name="metadata-generation"></a>中繼資料的產生  
 *中繼資料產生*允許 （適用於輸出的案例） 用戶端產生程式碼，以及根據選取的配接器取用者的作業 （適用於輸入案例） 服務。 雖然我們建議配接器取用者使用的工具[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]([!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] BizTalk 應用程式時)，則[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供公用介面`Microsoft.ServiceModel.Channels.MetadataRetrievalClient.GetMetadata%2A`擷取System.Web.Services.Description.ServiceDescription，代表 Web 服務描述語言 (WSDL) 包含選取的作業和類型相關資訊。 配接器寫入器可讓使用中繼資料物件模型的[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，其中包含衍生自類別`Microsoft.ServiceModel.Channels.Common.OperationMetadata`和`Microsoft.ServiceModel.Channels.Common.TypeMetadata`來描述每個作業和類型的詳細資料。  
  