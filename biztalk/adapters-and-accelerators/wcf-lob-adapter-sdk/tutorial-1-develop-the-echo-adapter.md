---
title: 教學課程 1： 開發 Echo 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ffb0df3c-cd07-4bcf-af69-971065081fd6
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b1b1a4d0e0293ba26792508ea367c5e91cccec5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977607"
---
# <a name="tutorial-1-develop-the-echo-adapter"></a>教學課程 1： 開發 Echo 配接器
在本教學課程中，您將開發功能的配接器使用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 配接器模擬來說明許多重要功能的 WCF LOB 配接器 SDK 包括虛構的特定業務系統的作業：  

- 同步輸入  

- 同步輸出  

- 中繼資料瀏覽  

- 中繼資料搜尋  

- 中繼資料解析  

  本章節包含 echo 配接器所支援的各種功能。 它們是訊息交換，作業的中繼資料，連接屬性，以及配接器屬性。  

## <a name="message-exchange-patterns"></a>訊息交換模式  
 Echo 配接器支援下列兩種訊息交換模式：  

- 同步輸出，也就是取用的用戶端會透過配接器的 WCF 要求訊息傳送到目標系統，，然後等待接收配接器透過在目標系統中的 WCF 回應訊息。 這是最常見的訊息交換模式，為配接器。 若要支援同步輸出，實作`Microsoft.ServiceModel.Channels.Common.IOutboundHandler`介面。  

- 同步也就是輸入資料或透過配接器在目標系統中的事件取用的用戶端接聽。 若要支援同步輸入，實作`Microsoft.ServiceModel.Channels.Common.IInboundHandler`介面。  

  如需詳細的訊息交換模式的詳細資訊，請參閱[架構概觀](architecture-overview-of-the-wcf-lob-adapter-sdk.md)。  

> [!NOTE]
>  [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]訊息交換模式會顯示為 UI 中的資料流程。  

## <a name="metadata-support"></a>中繼資料支援  
 Echo 配接器支援中繼資料瀏覽、 搜尋和解析功能。 通常，瀏覽和搜尋會從 LOB 系統擷取作業。 Echo 配接器，LOB 系統是一組預先定義的作業，如下所示：  

```  
EchoMainCategory  
        Echo/EchoStrings  
        Echo/EchoGreetings  
        Echo/EchoCustomGreetingFromFile  
        Echo/OnReceiveEcho  
```  

 每個作業的定義如下：  

|**名稱**|**作業定義**|**說明**|**方向**|  
|--------------|------------------------------|---------------------|-------------------|  
|EchoMainCategory|類別目錄|將分類的作業。|不適用|  
|Echo/EchoStrings|string [] EchoStrings(string data)|會回應傳入的字串來呼叫用戶端指定的次數。|輸出|  
|Echo/EchoGreetings|[] EchoGreetings(Greeting greeting) 的問候語|會回應傳入的問候語物件來呼叫用戶端指定次數。|輸出|  
|Echo/EchoCustomGreetingFromFile|CustomGreeting EchoCustomGreetingFromFile(Uri greetingInstancePath)|藉由從檔案讀取其執行個體回應的問候語物件。 問候語物件的中繼資料被取自預先定義的 XSD 檔案。|輸出|  
|Echo/OnReceiveEcho|void OnReceiveEcho （Uri 路徑，長時間內容）|將回應的位置和長度的指定資料夾中卸除的檔案。|輸入|  

## <a name="adapter-properties"></a>配接器屬性  
 配接器會公開下列配接器屬性。  


|            **名稱**            | **類別目錄** | **資料類型**  |                                                                                                              **說明**                                                                                                               |
|--------------------------------|--------------|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|             Count              |     其他     |  System.Int32  |                                                                    用來回應呼叫的用戶端的輸入指定重試次數。<br /><br /> 預設值 = 5                                                                     |
|    EnableConnectionPooling     |     其他     | System.Boolean | 用來啟用或停用配接器的連接共用。<br /><br /> 預設 = true，表示在執行階段引擎會啟用連接共用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 |
|       InboundFileFilter        |   輸入    | System.String  |                                                   用於僅限輸入的案例，而且使用 FileSystemWatcher 來監視擴充功能的檔案。<br /><br /> 預設 =\*.txt                                                   |
| InboundFileSystemWatcherFolder |   輸入    | System.String  |                                        用來設定其中的檔案就會卸除 FileSystemWatcher 來引發通知配接器的資料夾。<br /><br /> 預設 = c:\inbound\watcher。                                        |

## <a name="connection-properties"></a>連接屬性  
 Echo 配接器會公開下列連接屬性。  

|**名稱**|**資料類型**|**說明**|  
|--------------|-------------------|---------------------|  
|應用程式|System.String|LOB 系統內的應用程式名稱。 這個屬性是用於說明用途。 Echo 配接器並不包含任何 LOB 系統。<br /><br /> 預設 = lobapplication|  
|EnableAuthentication|System.Boolean|若為 true，配接器會預期在用戶端認證的使用者名稱 欄位中的值。<br /><br /> 預設 = false|  
|主機名稱|System.String|LOB 系統的所在位置的伺服器名稱。 這個屬性是用於說明用途。 Echo 配接器並不包含任何 LOB 系統。<br /><br /> 預設 = lobhostname|  

## <a name="interface-implementation"></a>介面實作  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]定義的類別和介面，必須實作，以支援特定功能的介面卡集合。 下表描述這些類別和介面、 其描述和實作它們的時機。  


|                       **類別/介面**                       |                                                                                       **何時實作**                                                                                        |                                                                                      **說明**                                                                                       |
|-----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|       Microsoft.ServiceModel.Channels.Common.IConnection        |                                                                     如果您需要在目標系統中定義的連接。                                                                     |                                                                        定義目標系統的連線。                                                                        |
|    Microsoft.ServiceModel.Channels.Common.IConnectionFactory    |                                                                      如果您需要建立在目標系統的連線。                                                                      |                                                                        建立目標系統的連線。                                                                        |
|      Microsoft.ServiceModel.Channels.Common.ConnectionUri       | 如果您需要管理連線的 Uri。<br /><br /> 如果您要將分類內的連接屬性[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]工具。 |                                                                      管理目標系統的連線 Uri。                                                                       |
| Microsoft.ServiceModel.Channels.Common.IMetadataResolverHandler |                                                                       您的配接器必須支援中繼資料解析功能。                                                                       |                                                                           解析作業和型別中繼資料。                                                                            |
|  Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler  |                                                                        如果您的配接器支援中繼資料搜尋功能。                                                                        |                                                                   搜尋目標系統中的作業。                                                                    |
|  Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler  |                                                                            您的配接器必須支援瀏覽功能                                                                             |                                                                    瀏覽在目標系統中的作業。                                                                    |
|     Microsoft.ServiceModel.Channels.Common.IOutboundHandler     |                                                                  如果您的配接器通常需要支援輸出的功能。                                                                   | 將內送 WCF 要求訊息轉換成目標系統訊息、 叫用目標系統特定函式，並接著將回應轉換成傳出的 WCF 回應訊息。 |
|     Microsoft.ServiceModel.Channels.Common.IInboundHandler      |                                                                            如果您的配接器支援輸入的功能。                                                                            |                                                                   會接聽資料和/或從目標系統的事件。                                                                   |

 若要簡化您的配接器開發工作，使用[!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]來產生配接器專案，這會建立一組專門針對您的配接器功能的衍生類別。  

 若要自訂的配接器和 connection 屬性透過[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]並[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]工具，修改所產生的下列檔案[!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]。  

- {Projectname}BindingElement.cs  

- {Projectname}BindingElementExtensionElement.cs  

- {Projectname}ConnectionUri.cs  

  如需有關如何執行這項操作的詳細資訊，請參閱 <<c0> [ 步驟 2： 分類配接器和連接屬性](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-categorize-the-adapter-and-connection-properties.md)。  

## <a name="see-also"></a>另請參閱  
 [若要了解 WCF LOB 配接器 SDK 教學課程](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorials-to-learn-the-wcf-lob-adapter-sdk.md)