---
title: 重要元件 WCF LOB 配接器 SDK |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59b8029b-4799-471b-8825-15d79a30bf1f
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3d033e452c4f67b66ed7e3b50b2c553def558015
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972231"
---
# <a name="key-components-of-the-wcf-lob-adapter-sdk"></a>WCF LOB 配接器 SDK 的重要元件
開發配接器使用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]需要使用許多下列的基本元件：  

- **連接元件**，協助建立和維護特定業務系統的連線。  

- **處理常式元件**定義和實作程序用來處理輸入和輸出訊息和中繼資料作業。  

- **中繼資料元件**定義和操作與特定業務系統進行通訊所使用的中繼資料。  

- **自訂元件**提供異動、 可靠傳訊和安全性的支援。  

- **核心元件**緊密整合的所有元件，並確保緊密地整合到[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]。  

  這些元件是本主題的重點。  

## <a name="connection-components"></a>連接元件  
 連接元件包含介面和類別，可協助定義和控制連線的存留期，以及管理統一資源識別元 (URI) 查詢的屬性和使用者屬性。 連接元件包含介面和下表中所述的類別。  

|連接元件|必要項？|描述|  
|---|---|---|  
|`Microsoft.ServiceModel.Channels.Common.ConnectionUri`|必要項|基底類別提供自訂的 URI，建立會使用您的配接器的使用者體驗。|  
|`Microsoft.ServiceModel.Channels.Common.IConnection`|必要項|介面會定義連接的行為。 開發人員必須實作這個介面來定義目標系統的連接。|  
|`Microsoft.ServiceModel.Channels.Common.IConnectionFactory`|必要項|連線處理站的基底類別。 定義目標系統的連線處理站時，開發人員會將子類別。|  
|`Microsoft.ServiceModel.Channels.Common.ConnectionPoolSettings`|選擇性|包含控制連接共用行為的設定。 開發人員可能想要調整這些值，根據目標系統的行為。|  
|`Microsoft.ServiceModel.Channels.Common.ConnectionManagerSettings`|選擇性|包含控制行為的連接集區的靜態設定。 開發人員可能想要調整為其目標系統的這些值。|  

 [!INCLUDE[afdevwizardnamelong](../../includes/afdevwizardnamelong-md.md)]會建立實作`Microsoft.ServiceModel.Channels.Common.IConnection``Microsoft.ServiceModel.Channels.Common.ConnectionUri`和`Microsoft.ServiceModel.Channels.Common.IConnectionFactory`不論所選的精靈選項。 這些實作會包含程式碼支援 （包括在 連線 URI 的連接屬性） 精靈 中選擇的選項，但配接器開發人員必須提供開啟、 關閉及其他方法的實作`Microsoft.ServiceModel.Channels.Common.IConnection`和`Microsoft.ServiceModel.Channels.Common.ConnectionUri`.  

## <a name="handler-components"></a>處理常式元件  
 處理常式元件提供的支援，針對不同訊息交換模式包括輸入、 輸出、 非同步輸入，非同步輸出和中繼資料搜尋服務中，瀏覽及解析作業。 處理常式元件包含介面和下表中所述的類別。  

|處理常式元件|必要項？|描述|  
|---|---|---|  
|`Microsoft.ServiceModel.Channels.Common.IAsyncInboundHandler`|選擇性|用來從目標系統，以非同步方式接收訊息。 非同步支援是選擇性的。|  
|`Microsoft.ServiceModel.Channels.Common.IAsyncOutboundHandler`|選擇性|用來從目標系統，以非同步方式傳送訊息。 非同步支援是選擇性的。|  
|`Microsoft.ServiceModel.Channels.Common.IInboundHandler`|選擇性|用來接收目標系統中的訊息。 如果配接器需要接聽來自目標系統的訊息，開發人員應該實作這個處理常式。|  
|`Microsoft.ServiceModel.Channels.Common.IOutboundHandler`|選擇性|將訊息傳送至目標系統中提供支援。 雖為選擇性，並需要要求-回應訊息模式。 此模式，包括 HTTP、 RPC 與許多其他以最基本的通訊技術。|  
|`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler`|選擇性|此處理常式的實作時，配接器支援中繼資料瀏覽。 雖然是選擇性的開發人員通常會實作這個處理常式，以提供可用在目標系統中的作業清單。|  
|`Microsoft.ServiceModel.Channels.Common.IMetadataResolverHandler`|選擇性|當配接器會擷取並傳回中繼資料，從目標系統，表示系統的特定邏輯和資料類型時，就必須實作這個處理常式。 可擷取中繼資料是從實際的目標系統，或可以建立來代表目標系統的功能。 例如，FTP 配接器可以在其中建立 GET 和 PUT 作業。<br /><br /> 雖然並非必要，開發人員通常會實作這個處理常式，以提供特定作業的相關資訊。|  
|`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler`|選擇性|配接器支援中繼資料搜尋時，會實作這個處理常式。|  

 [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]會建立實作`Microsoft.ServiceModel.Channels.Common.IAsyncOutboundHandler`， `Microsoft.ServiceModel.Channels.Common.IOutboundHandler`，`Microsoft.ServiceModel.Channels.Common.IInboundHandler`和開發人員所做的選擇為基礎的中繼資料處理常式。 會提供支援程式碼;不過，配接器開發人員必須提供程式碼，以啟動和停止輸入的接聽程式和 TODO 註解標記的其他程式碼。  

## <a name="metadata-components"></a>中繼資料元件  
處理中繼資料要求，以及描述類型和目標應用程式中的作業，中繼資料元件會提供支援。 處理常式元件控制與未處理的中繼資料要求。 中繼資料元件描述的資料類型和目標系統所公開的作業。  

 中繼資料元件用來保存中繼資料資訊的兩種類型： 輸入中繼資料和作業的中繼資料。  

- *型別中繼資料*描述可在目標系統中的資料類型，並包含類型，其陣列屬性的名稱，如果是陣列，且無論是簡單的 XSD 結構描述型別或複雜型別。  

- *作業的中繼資料*描述可在目標系統中的作業。 屬性包含傳回型別、 參數和作業名稱清單。  

  配接器內的中繼資料支援是選擇性的但建議使用。 其中一個使用的優點[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]建置的配接器實作的功能與[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務會公開 （expose） 和繫結至一組動態作業的能力。  

> [!NOTE]
>  如果您需要公開一組有限的靜態方法，您應該考慮使用[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]。  

  適用於處理的元件，描述，並使用中繼資料是下表中所述。  

|中繼資料元件|描述|  
|---|---|  
|`Microsoft.ServiceModel.Channels.Common.ComplexQualifiedType`|代表複雜的限定型別配接器的類別。 例如，如果目標系統的關聯式資料庫、 資料表、 資料列，或使用者定義的程序傳回型別所有可能自訂限定的型別。|  
|`Microsoft.ServiceModel.Channels.Common.OperationMetadata`|代表目標系統的作業中繼資料的基底類別。 例如，您可以子類別 OperationMetadata 包含配接器針對關聯式資料庫中的預存程序的相關資訊。|  
|`Microsoft.ServiceModel.Channels.Common.OperationMetadataTraceRecord`|可用來擷取作業的中繼資料，以追蹤檔案。 追蹤會收集資訊，例如唯一識別碼、 上次存取時間，時間戳記，顯示名稱、 原始名稱、 參數和其他詳細資料。|  
|`Microsoft.ServiceModel.Channels.Common.ParameterizedOperationMetadata`|提供一種定義的作業，例如參數和傳回類型的屬性。|  
|`Microsoft.ServiceModel.Channels.Common.OperationParameter`|描述用來叫用目標系統上的作業參數。 屬性包括名稱、 原始名稱、 參數方向和旗標，指出參數是否為空白。|  
|`Microsoft.ServiceModel.Channels.Common.OperationParameterDirection`|描述作業的參數方向的列舉的類型。 參數可以是輸入只 (In)，輸出只 （輸出） 或雙向 (InOut)。|  
|`Microsoft.ServiceModel.Channels.Common.OperationResult`|表示作業結果。 可以是 OperationResult.Empty 傳回 void，則為 null 的運算和字串、 整數或其他值，視作業而定。|  
|`Microsoft.ServiceModel.Channels.Common.QualifiedType`|設計成限定類型屬性的基底類別，且用來描述的目標系統的型別中繼資料屬性。|  
|`Microsoft.ServiceModel.Channels.Common.QualifiedTypeContainer`|提供一組相關的限定類型的容器。|  
|`Microsoft.ServiceModel.Channels.Common.SimpleQualifiedType`|當該類型會直接對應到 W3C XSD 結構描述類型，描述目標系統的型別中繼資料的屬性。 如需允許的類型，請參閱[XmlTypeCode 列舉](https://msdn.microsoft.com/library/system.xml.schema.xmltypecode(v=vs.110).aspx)。|  
|`Microsoft.ServiceModel.Channels.Common.TypeMember`|提供方法來結構化型別中繼資料中定義的簡單或複雜的資料成員。|  
|`Microsoft.ServiceModel.Channels.Common.TypeMetadata`|代表目標系統的型別中繼資料的基底類別。|  
|`Microsoft.ServiceModel.Channels.Common.StructuredTypeMetadata`|提供定義包含複雜和/或簡單的型別成員的資料結構的方式。|  
|`Microsoft.ServiceModel.Channels.Common.TypeMetadataCollection`|提供一組相關的型別中繼資料的容器。|  
|`Microsoft.ServiceModel.Channels.Common.TypeMetadataTraceRecord`|可用來擷取至追蹤檔案的型別中繼資料。 上次存取時間戳記和其他詳細資料，追蹤收集資訊，例如唯一識別碼。|  

## <a name="custom-components"></a>自訂元件  
 自訂元件提供交易、 安全性、 可靠傳訊和其他功能高度相依於目標系統的支援。 使用配接器開發人員為[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，您必須了解目標系統的功能，並判斷您要支援它們的範圍。  

## <a name="core-components"></a>核心元件  
 核心元件提供一組基底類別和介面，可讓配接器以插入[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]。 下表中詳述的核心元件。  


|                     核心元件                      | 必要項？ |                                                                                                                                                                                          描述                                                                                                                                                                                          |
|---------------------------------------------------------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `Microsoft.ServiceModel.Channels.Common.Adapter`     | 必要項  |                                                      撰寫使用的配接器的基底類別[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 它會負責互動[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道架構                                                      |
| `Microsoft.ServiceModel.Channels.Common.AdapterBinding` | 必要項  | 包含可控制各種設定，包括連接集區的配接器設定的類別 (`Microsoft.ServiceModel.Channels.Common.ConnectionPoolSettings`)，快取 (`Microsoft.ServiceModel.Channels.Common.CacheSettings`)，中繼資料 (`Microsoft.ServiceModel.Channels.Common.MetadataSettings`)，和傳訊 (`Microsoft.ServiceModel.Channels.Common.MessagingSettings`)。 |

 自訂配接器會透過 WCF 繫結公開。 如需詳細資訊，請參閱 WCF 文件，網址[ http://go.microsoft.com/fwlink/?LinkId=100308 ](http://go.microsoft.com/fwlink/?LinkId=100308)。  

 [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]建立的實作`Microsoft.ServiceModel.Channels.Common.Adapter`， `Microsoft.ServiceModel.Channels.Common.AdapterBinding`， `System.ServiceModel.Configuration.StandardBindingElement`，和`System.ServiceModel.Configuration.StandardBindingCollectionElement`公開 WCF 組態系統的配接器繫結。 [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]也會在產生的實作`System.ServiceModel.Configuration.BindingElementExtensionElement`若要啟用`Microsoft.ServiceModel.Channels.Common.Adapter`WCF 自訂繫結從電腦或應用程式組態檔內使用。  

 如需 StandardBindingElement、 StandardBindingCollectionElement 和 BindingElementExtensionElement 的詳細資訊，請參閱 WCF 文件。  

 如需有關設定配接器與寫入[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，請參閱 <<c2> [ 部署配接器使用 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/deploy-an-adapter-using-the-wcf-lob-adapter-sdk.md)。  

## <a name="see-also"></a>另請參閱  
 [了解 LOB 系統與 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/understand-the-lob-system-with-the-wcf-lob-adapter-sdk.md)