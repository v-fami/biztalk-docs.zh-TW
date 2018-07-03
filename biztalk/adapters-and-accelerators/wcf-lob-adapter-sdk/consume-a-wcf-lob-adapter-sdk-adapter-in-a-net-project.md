---
title: 使用 WCF LOB 配接器 SDK 中的介面卡的.NET 專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6934b96d-5704-4f3c-b53f-4e36e352a338
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a847aeae8c3c6ee564c38acf0b87679cd8469840
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994103"
---
# <a name="consume-a-wcf-lob-adapter-sdk-adapter-in-a-net-project"></a>使用 WCF LOB 配接器 SDK 中的介面卡的.NET 專案
若要使用配接器使用來建置[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您必須加入服務參考加入專案。 您可以藉由來這樣做：  

- 使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，其中已安裝的一部分[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。  

- 使用 svcutil.exe （ServiceModel 中繼資料公用程式），它會安裝為 Windows SDK 的一部分。  

## <a name="add-a-service-reference-using-the-add-adapter-service-reference-plug-in"></a>加入服務參考使用新增的配接器服務參考外掛程式  
 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]可用來瀏覽和搜尋中繼資料，並產生.NET CLR proxy 類別使用類型與選取的作業。  


1. 開啟您的.NET 應用程式中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。  

2. 在  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，以滑鼠右鍵按一下**專案**功能表，然後再按一下**新增配接器服務參考**。  

   > [!NOTE]
   >  此選項不會出現[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案。  

3. 在 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]畫面上，從**選取的繫結**下拉式清單中，選取的配接器繫結。  

4. 若要設定選取的配接器繫結的連接 URI，並提供任何認證、 URI 屬性和繫結屬性，請按一下**設定**。 實際需求依選取的配接器繫結。  

5. 您已設定 URI，請按一下**確定**。  

6. 按一下 **[連接]**。 連線 URI 是否有效，且接受用戶端認證 （如果有的話），則**分類**窗格應該填入的類別和配接器所提供的作業。  

7. 如果配接器支援搜尋，則可使用 [搜尋] 欄位。 您可以在否則為篩選依據的合約類型、 探索類型，以及作業中的節點，即可**分類**窗格。  

8. 如需進階的 proxy 產生選項，按一下**進階**。 選項包含：  


   |                         選項                         |   對等的 svcutil.exe 選項    |                                                                     描述                                                                     |
   |--------------------------------------------------------|------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
   |           **產生非同步方法**            |               /async               | 產生這兩個同步和非同步的方法簽章。<br /><br /> 預設值 （如果尚未選取）： 產生只同步方法簽章。 |
   |             **產生訊息合約**             |          /messageContract          |                                                          產生訊息合約型別。                                                          |
   |                **讓內部類型**                 |             / 內部              |                   產生標示為內部的類別。<br /><br /> 預設值 （如果尚未選取）： 產生公用類別。                    |
   |                **啟用資料繫結**                 |         /enableDataBinding         |              實作 System.ComponentModel.INotifyPropertyChanged 介面上所有的資料合約類型，以啟用資料繫結。               |
   |     **匯入非資料類型做為 IXmlSerializable**      |          /importXmlTypes           |                        設定資料合約序列化程式，若要匯入非資料合約類型當成 IXmlSerializable 類型。                         |
   |             **產生通道的介面**             |                                    |                                                          產生的通道介面。                                                           |
   |             **可序列化標記類別**              |                                    |                                            選取是否要產生的資料類型，使用序列化程式。                                            |
   |             **不會產生 app.config**             |             /noConfig              |                                                  不會產生應用程式組態檔。                                                  |
   |          **序列化程式**<br /><br /> **Auto**           |          /serializer:Auto          |                                     會自動選取序列化和還原序列化的序列化程式。                                      |
   | **序列化程式**<br /><br /> **DataContract 序列化程式** | /serializer:DataContractSerializer |                         會產生用於序列化和還原序列化的資料合約序列化程式的資料類型                          |
   |      **序列化程式**<br /><br /> **XmlSerializer**      |     /serializer: xmlserializer      |                               產生使用 XmlSerializer 進行序列化和還原序列化的資料型別。                                |


9. 若要產生的 proxy 成品，請按一下**確定**。 成品數目而異的合約型別。  


   | 合約型別 |         成品          |                    描述                    |                                                                                                            |
   |---------------|---------------------------|---------------------------------------------------|------------------------------------------------------------------------------------------------------------|
   |   輸出    |       CLR WCF Proxy       | 包含合約和服務實作。 |                                                                                                            |
   |   輸出    |                           |                    App.config                     |         包含\<端點\>並\<繫結\>項目\<系統。ServiceModel\>\<用戶端\>。         |
   |    輸入    | CLR WCF 服務介面 |              包含的合約。               |                                                                                                            |
   |    輸入    |                           |          CLR WCF 服務實作           |                            衍生自合約的虛設常式實作。                             |
   |    輸入    |                           |                    App.config                     | 包含\<端點\>，\<繫結\>並\<行為\>項目\<系統。ServiceModel\>\<服務\>。 |


10. 您現在可以在您的應用程式中使用 proxy。  

## <a name="adding-a-service-reference-by-using-svcutilexe"></a>使用 svcutil.exe 加入服務參考  
 Svcutil.exe 會是可用來擷取中繼資料，並產生.NET CLR proxy 類別，然後新增至命令列公用程式[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]專案。 如需 svcutil.exe 的詳細資訊，請參閱[ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx)。 

 若要從裝載在 IIS 中的配接器產生的 proxy 類別  

1. 在命令提示字元中，輸入**svcutil.exe 」<http://localhost/adapter/AdapterService.svc?wsdl”> /config:app.config**。HTTP 路徑取代為您裝載的配接器的正確路徑。 這會建立包含的.NET CLR proxy 和 output.config，其中包含的.cs 檔案\<繫結\>和 用戶端\<端點\>for \<system.serviceModel\>。  

   > [!NOTE]
   >  如果您的配接器包含許多作業，您可以限制所使用的查詢字串傳回的作業 ' op =' 後面接著您感興趣之作業的名稱。 例如：`svcutil.exe “http://localhost/adapter/AdapterService.svc?wsdl&op=Echo/EchoString&op=Echo/EchoArray”`產生 proxy 程式碼，只是 EchoString 和 EchoArray 作業。  

2. 開啟您的專案中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。  

   1.  在 **方案總管 中**，以滑鼠右鍵按一下專案，指向**新增**，然後按一下 **新項目**。 在 **加入現有項目**對話方塊方塊中，選取先前建立的.cs 和 app.config 檔案。  按一下 **[加入]**。  

   2.  在 **方案總管 中**，以滑鼠右鍵按一下**參考**，然後按一下 **加入參考**。 在  **.NET**索引標籤上，選取**System.ServiceModel**，然後按一下**確定**。 您現在可以在您的應用程式中使用 proxy。  

## <a name="see-also"></a>另請參閱  
 [教學課程 1： 開發 Echo 配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)   
 [使用配接器使用 WCF LOB 配接器 SDK 所建立](../../adapters-and-accelerators/wcf-lob-adapter-sdk/consume-an-adapter-created-using-the-wcf-lob-adapter-sdk.md)