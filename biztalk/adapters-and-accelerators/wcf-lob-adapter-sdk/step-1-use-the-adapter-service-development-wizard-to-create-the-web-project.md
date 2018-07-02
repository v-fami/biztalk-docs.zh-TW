---
title: 步驟 1： 使用配接器服務開發精靈來建立 Web 專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7ea0e33c-0d8d-4656-a6f0-3008b90f93f8
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fb8737f51f9e0b6afe3d61218f69015c1cd5d72
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984031"
---
# <a name="step-1-use-the-adapter-service-development-wizard-to-create-the-web-project"></a>步驟 1： 使用配接器服務開發精靈來建立 Web 專案
![步驟 4 之 1](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")  
  
 **若要完成的時間：** 10 分鐘  
  
 在此步驟中，您會建立使用 Visual Studio 專案和[!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)]。 [!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)]會收集介面卡、 作業和端點組態的相關資訊，並產生可部署至 IIS 的 Web 專案。  
  
## <a name="prerequisites"></a>必要條件  
 您必須建置並部署 Echo 範例中所述[教學課程 1： 開發 Echo 配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)再開始本教學課程。  
  
### <a name="to-start-the-adapter-service-development-wizard"></a>若要啟動配接器服務開發精靈  
  
1.  啟動 Visual Studio，然後在**檔案**功能表上，指向**新增**，然後按一下**網站**。  
  
2.  在 **新的網站**對話方塊方塊中，執行下列動作：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |**語言**|按一下  **Visual C#**。|  
    |**範本**|按一下  **WCF 配接器服務**。|  
    |**位置**|選取 **檔案系統**，然後輸入**C:\Tutorials\EchoWeb**作為路徑。|  
  
3.  按一下 [確定] 。  
  
4.  在 [**歡迎頁面**，按一下**下一步]**。  
  
### <a name="to-select-the-adapter-and-uri"></a>若要選取的配接器和 URI  
  
1.  在上**選擇要產生服務合約作業**頁面上，選取**echoAdapterBindingV2**從**選取的繫結**下拉式清單，然後再按**設定**。  
  
2.  上**安全性**索引標籤**設定介面卡**] 對話方塊中，將**用戶端認證類型**至**使用者名稱**，然後將 [ **使用者名稱認證**，如下所示：  
  
    |屬性|ReplTest1|  
    |--------------|-----------|  
    |**使用者名稱**|username|  
    |**密碼**|密碼|  
  
    > [!NOTE]
    >  使用者名稱和密碼，在此輸入只會用來連接至配接器時執行的步驟，在精靈中，並在精靈完成之後，不會保留。  
  
3.  按一下  **URI 屬性**索引標籤，然後再設定屬性，如下所示：  
  
    |屬性|ReplTest1|  
    |--------------|-----------|  
    |**應用程式**|LobApplication|  
    |**EnableAuthentication**|True|  
    |**主機名稱**|lobhostname|  
    |**EchoInUpperCase**|False|  
  
    > [!NOTE]
    >  此處所選取的 URI 屬性將用來建立\<**用戶端**\>\<**端點**\> web.config 檔案中的項目。  
  
4.  按一下 [**繫結屬性**] 索引標籤。請注意預設值，然後按一下**確定**。  
  
    > [!NOTE]
    >  繫結值將用來產生\<**繫結**\>\<**echoAdapterBindingV2** \> web.config 檔案中的項目。  
  
### <a name="to-select-the-contract-and-operations"></a>若要選取的合約和作業  
  
1.  在 **選擇要產生服務合約作業**頁面上，按一下**Connect**。  
  
2.  在 **選取類別目錄**樹狀目錄中，選取**主要類別**。 這會填入**可用的類別和作業**清單。  
  
    > [!NOTE]
    >  您也可以輸入中的搜尋詞彙**分類中的搜尋**欄位，以尋找包含搜尋詞彙的任何作業。  
  
3.  在 **可用的類別和作業**清單中，選取**EchoGreetings** ，按一下 **新增**。 這會將 EchoGreetings 作業移**新增的類別和作業**清單。 此處所選取的作業將會公開用戶端應用程式，透過精靈所產生的用戶端 proxy 程式碼。  
  
     ![選取合約與操作](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/de497b32-c820-480f-84f3-a9d0d2ded86b.gif "de497b32-c820-480f-84f3-a9d0d2ded86b")  
  
4.  按 [下一步] 。  
  
### <a name="to-configure-service-and-endpoint-behavior"></a>若要設定服務和端點行為  
  
1.  在 **設定服務與端點行為**頁面上，輸入下列值**服務行為組態**:  
  
    |屬性|ReplTest1|  
    |--------------|-----------|  
    |**EnableMetadataExchange**|True|  
    |**IncludeExceptionDetailsinFault**|True|  
    |**名稱**|customServiceBehavior|  
    |**UseServiceCertificate**|False|  
  
     這些值會用來填入\< **serviceBehaviors**\>。  
  
2.  輸入下列值**端點行為組態**:  
  
    |屬性|ReplTest1|  
    |--------------|-----------|  
    |**名稱**|customEndpointBehavior|  
    |**AuthenticationType**|**HTTPUsernamePassword**|  
    |**UsernameHeader**|MyUserHeader|  
    |**PasswordHeader**|MyPassHeader|  
  
     這些值將用來指定**adapterSecurityBridgeType**中 <**endpointBehaviors** web.confg 中的項目。  
  
     ![端點組態](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/3fd5784c-64e5-47c1-9a6f-10f12f77f726.gif "3fd5784c-64e5-47c1-9a6f-10f12f77f726")  
  
3.  按 **[下一步]**  
  
### <a name="to-configure-the-binding"></a>若要設定繫結  
  
1. 在上**設定的服務端點繫結和位址**頁面上，選取**BindingConfiguration**中的項目**設定的位址和合約繫結**，及然後按一下省略符號 (**...**) 按鈕。  
  
2. 中**自訂繫結** 對話方塊中，將**模式**來**TransportWithMessageCredential**，然後按一下**確定**。  
  
3. 按一下 [**套用**，然後按一下**下一步]**。  
  
4. 在 **摘要**頁面上，檢閱的合約和作業為此專案中，選取，然後按一下**完成**。 您會看到 EchoWeb 方案，其中包含所建立的專案檔案 [!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)]  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 在此步驟中，您已使用[!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)]來產生 Web 專案，當發行至 IIS，會在開發 Echo 配接器的主機[教學課程 1： 開發 Echo 配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)在 IIS 程序。 產生的 Web 專案可讓 Web 服務和 WCF 用戶端存取選取的作業。  
  
## <a name="next-steps"></a>後續步驟  
 若要建置和部署 Web 專案，請繼續到[步驟 2： 部署 Web 專案](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-deploy-the-web-project.md)  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 1：開發 Echo 配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)