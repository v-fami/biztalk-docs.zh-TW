---
title: "教學課程 1： 在開發回應配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffb0df3c-cd07-4bcf-af69-971065081fd6
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 484452dc4ee624f4fa41e9387098f6f792c1de28
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-1-develop-the-echo-adapter"></a>教學課程 1： 在開發回應配接器
在本教學課程中，您將開發功能的介面卡使用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 配接器模擬示範許多重要功能的 WCF LOB 配接器 SDK 包括虛構的特定業務系統的作業：  
  
-   同步輸入  
  
-   同步輸出  
  
-   中繼資料瀏覽  
  
-   中繼資料的搜尋  
  
-   中繼資料解析  
  
 本章節包含回應配接器所支援的各種功能。 它們是訊息交換、 作業的中繼資料、 連接屬性，以及配接器屬性。  
  
## <a name="message-exchange-patterns"></a>訊息交換模式  
 回應配接器支援下列兩個訊息交換模式：  
  
-   同步輸出，也就是取用的用戶端會經由配接器的 WCF 要求訊息傳送到目標系統，，然後等待從目標系統，透過配接器接收 WCF 回應訊息。 這是配接器的最常見訊息交換模式。 若要支援同步輸出，實作`Microsoft.ServiceModel.Channels.Common.IOutboundHandler`介面。  
  
-   同步輸入時，也就是取用的用戶端會接聽資料或從目標系統，透過介面卡的事件。 若要支援同步的輸入，實作`Microsoft.ServiceModel.Channels.Common.IInboundHandler`介面。  
  
 如需訊息交換模式的詳細資訊，請參閱[架構概觀](architecture-overview-of-the-wcf-lob-adapter-sdk.md)。  
  
> [!NOTE]
>  [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]資料流在 UI 中顯示的訊息交換模式。  
  
## <a name="metadata-support"></a>中繼資料支援  
 回應配接器支援中繼資料瀏覽、 搜尋和解析功能。 通常，瀏覽及搜尋會從 LOB 系統擷取作業。 回應配接器，LOB 系統是一組預先定義的作業，如下所示：  
  
```  
EchoMainCategory  
        Echo/EchoStrings  
        Echo/EchoGreetings  
        Echo/EchoCustomGreetingFromFile  
        Echo/OnReceiveEcho  
```  
  
 每個作業的定義如下：  
  
|**名稱**|**操作定義**|**說明**|**方向**|  
|--------------|------------------------------|---------------------|-------------------|  
|EchoMainCategory|類別目錄|將分類的作業。|不適用|  
|Echo/EchoStrings|string [] EchoStrings(string data)|回應傳入的字串來呼叫用戶端指定的次數。|輸出|  
|Echo/EchoGreetings|問候語 [EchoGreetings(Greeting greeting)]|回應連入問候語物件來呼叫用戶端指定次數。|輸出|  
|Echo/EchoCustomGreetingFromFile|CustomGreeting EchoCustomGreetingFromFile(Uri greetingInstancePath)|藉由從檔案讀取它的執行個體回應祝賀物件。 問候語物件的中繼資料是從預先定義的 XSD 檔案中取得。|輸出|  
|Echo/OnReceiveEcho|void OnReceiveEcho （Uri 路徑，長時間內容）|回應的位置和卸除指定的資料夾中檔案的長度。|輸入|  
  
## <a name="adapter-properties"></a>配接器屬性  
 配接器會公開下列配接器屬性。  
  
|**名稱**|**類別目錄**|**資料類型**|**說明**|  
|--------------|------------------|-------------------|---------------------|  
|Count|其他|System.Int32|用來回應呼叫的用戶端的輸入指定次數。<br /><br /> 預設值 = 5|  
|EnableConnectionPooling|其他|System.Boolean|用來啟用或停用配接器的連接共用。<br /><br /> 預設值 = true，表示執行階段引擎中會啟用連接共用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。|  
|InboundFileFilter|輸入|System.String|用於輸入案例並用 FileSystemWatcher 来監視的延伸模組檔案。<br /><br /> 預設值 = *.txt|  
|InboundFileSystemWatcherFolder|輸入|System.String|用來設定其中的檔案就會卸除 FileSystemWatcher 以引發通知配接器的資料夾。<br /><br /> 預設值 = c:\inbound\watcher。|  
  
## <a name="connection-properties"></a>連接屬性  
 回應配接器會公開下列連接屬性。  
  
|**名稱**|**資料類型**|**說明**|  
|--------------|-------------------|---------------------|  
|應用程式|System.String|LOB 系統內的應用程式名稱。 此屬性適用於說明用途。 回應配接器並不包含任何 LOB 系統。<br /><br /> 預設值 = lobapplication|  
|EnableAuthentication|System.Boolean|若為 true，配接器會預期在用戶端認證的使用者名稱欄位中的值。<br /><br /> 預設 = false|  
|主機名稱|System.String|LOB 系統所在伺服器名稱。 此屬性適用於說明用途。 回應配接器並不包含任何 LOB 系統。<br /><br /> 預設值 = lobhostname|  
  
## <a name="interface-implementation"></a>介面實作  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]定義類別和介面，以支援特定功能的配接器必須實作的集合。 下表描述這些類別和介面、 及其描述，以及何時實作它們。  
  
|**類別/介面**|**何時實作**|**說明**|  
|--------------------------|---------------------------|---------------------|  
|Microsoft.ServiceModel.Channels.Common.IConnection|如果您需要定義目標系統的連接。|定義連線到目標系統。|  
|Microsoft.ServiceModel.Channels.Common.IConnectionFactory|如果您要建立目標系統的連線。|建立連接至目標系統。|  
|Microsoft.ServiceModel.Channels.Common.ConnectionUri|如果您需要管理連線的 Uri。<br /><br /> 如果您要分類內的連接屬性[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]工具。|管理目標系統的連線 Uri。|  
|Microsoft.ServiceModel.Channels.Common.IMetadataResolverHandler|您的配接器必須支援中繼資料解析功能。|解析作業和型別中繼資料。|  
|Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler|如果您的配接器支援中繼資料的搜尋功能。|搜尋目標系統中的作業。|  
|Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler|您的配接器必須支援瀏覽功能|瀏覽目標系統中的作業。|  
|Microsoft.ServiceModel.Channels.Common.IOutboundHandler|如果您的配接器通常需要支援輸出的功能。|將內送 WCF 要求訊息轉換成目標系統訊息、 叫用目標系統特定函式，並再將回應轉換成傳出 WCF 回應訊息。|  
|Microsoft.ServiceModel.Channels.Common.IInboundHandler|如果您的配接器是否支援傳入的功能。|會接聽資料和/或從目標系統的事件。|  
  
 若要簡化您的配接器開發工作，使用[!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]產生您的配接器專案，建立一組配接器功能量身訂做衍生類別。  
  
 若要自訂的配接器和 connection 屬性透過[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]和[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]工具，修改所產生的下列檔案[!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]。  
  
-   {Projectname}BindingElement.cs  
  
-   {Projectname}BindingElementExtensionElement.cs  
  
-   {Projectname}ConnectionUri.cs  
  
 如需有關如何執行這項操作的詳細資訊，請參閱[步驟 2： 分類的介面卡和連接屬性](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-categorize-the-adapter-and-connection-properties.md)。  
  
## <a name="see-also"></a>另請參閱  
 [若要了解 WCF LOB Adapter SDK 的教學課程](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorials-to-learn-the-wcf-lob-adapter-sdk.md)