---
title: "步驟 1： 建立 Web 專案中使用配接器服務開發精靈 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7ea0e33c-0d8d-4656-a6f0-3008b90f93f8
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a63953b0928915a8fea5b357722cd4e34f1b900c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-use-the-adapter-service-development-wizard-to-create-the-web-project"></a>步驟 1： 建立 Web 專案中使用配接器服務開發精靈
![步驟 4 之 1](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")  
  
 **若要完成的時間：** 10 分鐘  
  
 在此步驟中，您會建立使用 Visual Studio 專案和[!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)]。 [!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)]會收集介面卡、 作業和端點組態的相關資訊，並產生可部署至 IIS 的 Web 專案。  
  
## <a name="prerequisites"></a>必要條件  
 您必須建置和部署 Echo 範例中所述[教學課程 1： 開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)再開始本教學課程。  
  
### <a name="to-start-the-adapter-service-development-wizard"></a>若要啟動配接器服務開發精靈  
  
1.  啟動 Visual Studio，然後在**檔案**功能表上，指向**新增**，然後按一下 **網站**。  
  
2.  在**新網站**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**語言**|按一下**Visual C#**。|  
    |**範本**|按一下**WCF 配接器服務**。|  
    |**位置**|選取**檔案系統**，然後輸入**C:\Tutorials\EchoWeb**做為路徑。|  
  
3.  按一下 **[確定]**。  
  
4.  在**歡迎頁面**，按一下 **下一步**。  
  
### <a name="to-select-the-adapter-and-uri"></a>若要選取的配接器和 URI  
  
1.  在**選擇要產生服務合約的作業**頁面上，選取**echoAdapterBindingV2**從**選取繫結**下拉式清單，然後再按**設定**。  
  
2.  上**安全性** 索引標籤**設定配接器** 對話方塊中，將**用戶端認證類型**至**Username**，然後設定  **使用者名稱認證**，如下所示：  
  
    |屬性|值|  
    |--------------|-----------|  
    |**使用者名稱**|username|  
    |**密碼**|密碼|  
  
    > [!NOTE]
    >  使用者名稱和密碼，在此輸入只會用來連接至配接器時執行的步驟，在精靈中，並不會保留在精靈完成之後。  
  
3.  按一下**URI 屬性**索引標籤，然後再設定的屬性，如下所示：  
  
    |屬性|值|  
    |--------------|-----------|  
    |**應用程式**|LobApplication|  
    |**EnableAuthentication**|True|  
    |**主機名稱**|lobhostname|  
    |**EchoInUpperCase**|False|  
  
    > [!NOTE]
    >  在這裡選取的 URI 屬性將用來建立\<**用戶端**>\<**端點**> web.config 檔案中的項目。  
  
4.  按一下**繫結屬性**] 索引標籤。預設值，請注意，然後按一下 [**確定**。  
  
    > [!NOTE]
    >  繫結值將會用來產生\<**繫結**>\<**echoAdapterBindingV2**> web.config 檔案中的項目。  
  
### <a name="to-select-the-contract-and-operations"></a>若要選取的合約和作業  
  
1.  在**選擇要產生服務合約的作業**頁面上，按一下**連接**。  
  
2.  在**選取類別目錄**樹狀目錄中，選取**主要類別**。 如此即會填入**可用的類別和作業**清單。  
  
    > [!NOTE]
    >  您也可以輸入中的搜尋詞彙**類別目錄中的搜尋**欄位以尋找包含搜尋詞彙的任何作業。  
  
3.  在**可用的類別和作業**清單中，選取**EchoGreetings**按一下**新增**。 這會將 EchoGreetings 作業**加入的類別和作業**清單。 在這裡選取的作業將會公開給用戶端應用程式可以透過精靈所產生的用戶端 proxy 程式碼。  
  
     ![選取合約與操作](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/de497b32-c820-480f-84f3-a9d0d2ded86b.gif "de497b32-c820-480f-84f3-a9d0d2ded86b")  
  
4.  按一下 **[下一步]**。  
  
### <a name="to-configure-service-and-endpoint-behavior"></a>若要設定服務與端點行為  
  
1.  在**設定服務與端點行為**頁面上，輸入下列值**服務行為組態**:  
  
    |屬性|值|  
    |--------------|-----------|  
    |**EnableMetadataExchange**|True|  
    |**IncludeExceptionDetailsinFault**|True|  
    |**名稱**|customServiceBehavior|  
    |**UseServiceCertificate**|False|  
  
     這些值可用來填入\< **serviceBehaviors**>。  
  
2.  輸入下列值**端點行為組態**:  
  
    |屬性|值|  
    |--------------|-----------|  
    |**名稱**|customEndpointBehavior|  
    |**AuthenticationType**|**HTTPUsernamePassword**|  
    |**UsernameHeader**|MyUserHeader|  
    |**PasswordHeader**|MyPassHeader|  
  
     這些值會用來指定**adapterSecurityBridgeType**中 <**endpointBehaviors** web.confg 中的項目。  
  
     ![端點組態](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/3fd5784c-64e5-47c1-9a6f-10f12f77f726.gif "3fd5784c-64e5-47c1-9a6f-10f12f77f726")  
  
3.  按 **[下一步]**  
  
### <a name="to-configure-the-binding"></a>若要設定的繫結  
  
1.  在**設定服務端點繫結與位址**頁面上，選取**BindingConfiguration**中的項目**設定的位址和合約繫結**，和然後按一下省略符號 (**...**) 按鈕。  
  
2.  中**自訂繫結**] 對話方塊中，將**模式**至**TransportWithMessageCredential**，然後按一下 [**確定**。  
  
3.  按一下**套用**，然後按一下 **下一步**。  
  
4.  在**摘要**頁面上，檢閱的合約和作業對於此專案中，選取，然後按一下**完成**。 您會看到有 EchoWeb 解決方案，其中包含所建立的專案檔案[!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)]  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 在此步驟中，您已經使用[!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)]產生 Web 專案，當發行至 IIS，將回應配接器開發中的主機[教學課程 1： 開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)在 IIS 中處理。 產生的 Web 專案可讓 Web 服務和 WCF 用戶端存取選取的作業。  
  
## <a name="next-steps"></a>後續步驟  
 若要建置及部署 Web 專案，請到[步驟 2： 部署 Web 專案](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-deploy-the-web-project.md)  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 1： 在開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)