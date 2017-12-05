---
title: "取用 WCF LOB 配接器 SDK 中的配接器的.NET 專案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6934b96d-5704-4f3c-b53f-4e36e352a338
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 622c6ad687e681591071d472e2ff8a9e8c515f95
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="consume-a-wcf-lob-adapter-sdk-adapter-in-a-net-project"></a>取用 WCF LOB 配接器 SDK 中的配接器的.NET 專案
若要使用配接器使用建置[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您必須加入服務參考加入專案。 您可以：  
  
-   使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，安裝的一部分[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。  
  
-   使用 svcutil.exe （ServiceModel 中繼資料公用程式），它會安裝為 Windows SDK 的一部分。  
  
## <a name="add-a-service-reference-using-the-add-adapter-service-reference-plug-in"></a>加入服務參考使用加入的配接器服務參考外掛程式  
 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]可用來瀏覽和搜尋中繼資料，並產生.NET CLR proxy 類別，使用選取的作業與型別。  
  
 
1.  開啟.NET 應用程式中的[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。  
  
2.  在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，以滑鼠右鍵按一下**專案**功能表，然後再按一下**新增配接器服務參考**。  
  
    > [!NOTE]
    >  此選項將不會看到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案。  
  
3.  在[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] 畫面上，從**選取繫結**下拉式清單中，選取配接器繫結。  
  
4.  若要設定選取的配接器繫結的連線 URI，並提供任何認證、 URI 屬性和繫結屬性，請按一下**設定**。 實際需求會根據選取的配接器繫結而有所不同。  
  
5.  當您已設定 URI 時，按一下 **確定**。  
  
6.  按一下 **[連接]**。 連線 URI 是否有效且用戶端認證 （如果有的話） 已被接受，**類別**窗格應填入的類別和配接器所提供的作業。  
  
7.  如果配接器支援搜尋，[搜尋] 欄位將會啟用。 否則，您可以依合約類型篩選，探索類型，以及作業中的節點，即可**類別**窗格。  
  
8.  如需進階的 proxy 產生選項，按一下 **進階**。 選項包含：  
  
    |選項|對等的 svcutil.exe 選項|Description|  
    |------------|-----------------------------------|-----------------|  
    |**產生非同步方法**|/async|同時產生同步與非同步方法簽章。<br /><br /> 預設值 （如果尚未選取）： 產生只同步方法簽章。|  
    |**產生訊息合約**|/messageContract|會產生訊息合約型別。|  
    |**讓內部類型**|/ 內部|產生標示為內部的類別。<br /><br /> 預設值 （如果尚未選取）： 產生公用類別。|  
    |**啟用資料繫結**|/enableDataBinding|實作 System.ComponentModel.INotifyPropertyChanged 介面以啟用資料繫結的所有資料合約類型。|  
    |**匯入非資料類型做為 IXmlSerializable**|/importXmlTypes|設定資料合約序列化程式在匯入非資料合約類型當成 IXmlSerializable 類型。|  
    |**產生通道的介面**||產生的通道介面。|  
    |**可序列化的標記類別**||選取是否要產生序列化程式與資料型別。|  
    |**不會產生 app.config**|/noConfig|不產生應用程式組態檔。|  
    |**序列化程式**<br /><br /> **Auto**|/serializer:Auto|會自動選取進行序列化與還原序列化的序列化程式。|  
    |**序列化程式**<br /><br /> **DataContract 序列化程式**|/serializer:DataContractSerializer|產生資料合約序列化程式用於序列化和還原序列化的資料型別|  
    |**序列化程式**<br /><br /> **XmlSerializer**|/serializer: xmlserializer|產生使用 XmlSerializer 來進行序列化和還原序列化的資料型別。|  
  
9. 若要產生 proxy 成品，請按一下**確定**。 成品數目會根據合約型別而異。  
  
    |合約型別|成品|Description||  
    |-------------------|--------------|-----------------|-|  
    |輸出|CLR WCF Proxy|包含合約和服務實作。||  
    |輸出||App.config|包含\<端點\>和\<繫結\>元素\<系統。ServiceModel\>\<用戶端\>。|  
    |輸入|CLR WCF 服務介面|包含的合約。||  
    |輸入||CLR WCF 服務的實作|衍生自合約的虛設常式實作。|  
    |輸入||App.config|包含\<端點\>，\<繫結\>和\<行為\>元素\<系統。ServiceModel\>\<服務\>。|  
  
10. 您現在可以在應用程式中使用 proxy。  
  
## <a name="adding-a-service-reference-by-using-svcutilexe"></a>使用 svcutil.exe 加入服務參考  
 Svcutil.exe 會是命令列公用程式可用來擷取中繼資料，並產生.NET CLR proxy 類別，然後加入至[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]專案。 如需 svcutil.exe 的詳細資訊，請參閱[ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx)。 
  
 若要從 IIS 中裝載的配接器產生 proxy 類別  
  
1.  在命令提示字元中，輸入**svcutil.exe"http://localhost/adapter/AdapterService.svc?wsdl"/config:app.config**。HTTP 路徑取代為您裝載的配接器的正確路徑。 這會建立包含.NET CLR proxy 和 output.config 所在的.cs 檔案\<繫結\>和用戶端\<端點\>如\<system.serviceModel\>。  
  
    > [!NOTE]
    >  如果您的配接器包含許多作業，您可以限制所使用的查詢字串傳回的作業 ' op =' 後面接著您感興趣的作業名稱。 例如：`svcutil.exe “http://localhost/adapter/AdapterService.svc?wsdl&op=Echo/EchoString&op=Echo/EchoArray”`產生只有 EchoString 和 EchoArray 作業的 proxy 程式碼。  
  
2.  開啟您的專案中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。  
  
    1.  在**方案總管] 中**，以滑鼠右鍵按一下專案，指向**新增**，然後按一下 [**新項目**。 在**加入現有項目**對話方塊中，選取先前建立的.cs 和 app.config 檔案。  按一下 **[加入]**。  
  
    2.  在**方案總管] 中**，以滑鼠右鍵按一下**參考**，然後按一下 [**加入參考**。 在**.NET**索引標籤上，選取**System.ServiceModel**，然後按一下 **確定**。 您現在可以在應用程式中使用 proxy。  
  
## <a name="see-also"></a>請參閱  
 [教學課程 1： 在開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)   
 [使用建立使用 WCF LOB Adapter SDK 的配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/consume-an-adapter-created-using-the-wcf-lob-adapter-sdk.md)