---
title: "步驟 1： 使用 WCF LOB 配接器開發精靈來建立回應配接器專案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 634a6498-55b0-462d-a5ca-16507b3787f5
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ffad8f817cf3a13b3d3af3264438bafa639181a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-use-the-wcf-lob-adapter-development-wizard-to-create-the-echo-adapter-project"></a>步驟 1： 使用 WCF LOB 配接器開發精靈來建立回應配接器專案
![步驟 1 的 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-1of9.gif "Step_1of9")  
  
 **若要完成的時間：** 15 分鐘  
  
 在此步驟中，您將建立的專案使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]和[!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]。 [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]將引導您完成開發自訂配接器系統的相關步驟。 它會收集有關訊息交換模式、 中繼資料功能、 配接器屬性和連接屬性。 精靈成功完成後，它會產生一組檔案。  
  
## <a name="prerequisites"></a>必要條件  
 您必須擁有中所述的知識[開始本教學課程之前](../../core/before-you-begin-the-tutorial.md)和已成功設定您的電腦，針對配接器開發使用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。  
  
## <a name="choose-wcf-lob-adapter-plug-in-in-visual-studio"></a>選擇 Visual Studio 中外掛程式的 WCF LOB 配接器  
  
1.  啟動 Visual Studio，然後在**檔案**功能表上，指向**新增**，然後按一下 **專案**。  
  
2.  在**新專案**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**專案類型**|按一下**Visual C#**。|  
    |**範本**|按一下**WCF LOB 配接器**。|  
    |**名稱**|型別**EchoAdapter**。|  
    |**位置**|型別**C:\Tutorials**。|  
    |**為方案建立目錄**|選取此核取方塊以建立方案檔案的目錄。|  
    |**方案名稱**|型別**EchoAdapterSampleV2**。|  
  
     下圖顯示**新專案** 對話方塊。  
  
     ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/3a349be4-1a7d-480a-8e9d-cfcba63cd14a.gif "3a349be4-1a7d-480a-8e9d-cfcba63cd14a")  
  
3.  按一下 **[確定]**。  
  
4.  在**歡迎**頁面上，按一下**下一步**。 下圖顯示**歡迎**頁面。  
  
     ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/0b8ef97f-044d-481f-8c7c-0d034fdba37d.gif "0b8ef97f-044d-481f-8c7c-0d034fdba37d")  
  
5.  按一下 **[下一步]**。  
  
## <a name="enter-the-scheme-and-namespace-information"></a>輸入配置與命名空間資訊  
  
1.  在**配置、 命名空間和 URI 資訊**頁面上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**配置**|型別**echov2**。|  
    |**專案的命名空間**|型別**Microsoft.Adapters.Samples.EchoV2**。|  
  
     下圖顯示**配置、 命名空間和 URI 資訊**頁面。  
  
     ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/0d72dab2-7992-47e4-bc4e-3e720b1cde38.gif "0d72dab2-7992-47e4-bc4e-3e720b1cde38")  
  
2.  按一下 **[下一步]**。  
  
## <a name="enter-the-data-flow-and-metadata-features"></a>輸入資料流和中繼資料功能  
  
1.  在**資料流程**和**中繼資料功能**頁面上，執行下列動作：  
  
     **訊息交換模式**  
  
    |使用|動作|  
    |--------------|----------------|  
    |**同步輸出**|選取此核取方塊。|  
    |**同步輸入**|選取此核取方塊。|  
  
     **中繼資料功能**  
  
    |使用|動作|  
    |--------------|----------------|  
    |**擷取**|選取此核取方塊。|  
    |**瀏覽**|選取此核取方塊。|  
    |**搜尋**|選取此核取方塊。|  
  
    > [!NOTE]
    >  在此內容中的資料流表示訊息交換模式，與相同概念性主題中所使用的詞彙。  
  
     下圖顯示**資料流程**和**中繼資料功能**頁面。  
  
     ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/4fa6f67d-4703-41db-b5f3-28cf9d6a40d2.gif "4fa6f67d-4703-41db-b5f3-28cf9d6a40d2")  
  
2.  按一下 **[下一步]**。  
  
## <a name="enter-the-adapter-properties"></a>輸入配接器屬性  
  
1.  在**配接器屬性**頁面上，執行下列動作：  
  
2.  加入呼叫屬性**計數**。 每一項作業的回應配接器會使用這個數字。 每個作業會傳回輸入的值**計數**的次數。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**屬性名稱**|型別**計數**。|  
    |**資料類型**|選取**System.Int32**。|  
    |**預設值**|型別**5**。|  
    |**加入**|按一下以加入新的配接器屬性。|  
  
3.  加入呼叫屬性**EnableConnectionPooling**。 這個旗標由[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]啟用或停用執行階段連接共用。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**屬性名稱**|型別**EnableConnectionPooling**。|  
    |**資料類型**|選取**System.Boolean**。|  
    |**預設值**|型別**true**。|  
    |**加入**|按一下以加入新的配接器屬性。|  
  
4.  加入呼叫屬性**InboundFileFilter**。 這個屬性供 FileSystemWatcher 監視此副檔名的檔案。 這個屬性是適用於僅限輸入的案例。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**屬性名稱**|型別**InboundFileFilter**。|  
    |**資料類型**|選取**System.String**。|  
    |**預設值**|型別 **\*.txt**。|  
    |**加入**|按一下以加入新的配接器屬性。|  
  
5.  加入呼叫屬性**InboundFileSystemWatcherFolder**。 這個屬性用來設定其中的檔案就會卸除 FileSystemWatcher 以引發通知配接器的資料夾。 這個屬性是適用於僅限輸入的案例。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**屬性名稱**|型別**InboundFileSystemWatcherFolder**。|  
    |**資料類型**|選取**System.String**。|  
    |**預設值**|型別**c:\\\inbound\\\watcher**。|  
    |**加入**|按一下以加入新的配接器屬性。|  
  
     下圖顯示**配接器屬性**頁面。  
  
     ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/84de11a5-a737-4aa5-96c8-61922e704f2b.gif "84de11a5-a737-4aa5-96c8-61922e704f2b")  
  
6.  按一下 **[下一步]**。  
  
## <a name="enter-the-connection-properties"></a>輸入連接屬性  
  
1.  在**連接屬性**頁面上，執行下列動作：  
  
2.  加入呼叫屬性**應用程式**。 此屬性適用於只說明用途。 回應配接器並不包含任何 LOB 系統。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**屬性名稱**|型別**應用程式**。|  
    |**資料類型**|選取**System.String**。|  
    |**預設值**|型別**lobapplication**。|  
    |**加入**|按一下以加入新的配接器屬性。|  
  
3.  加入呼叫屬性**EnableAuthentication**。 當`true`，配接器預期在用戶端認證的使用者名稱欄位中的值。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**屬性名稱**|型別**EnableAuthentication**。|  
    |**資料類型**|選取**System.Boolean**。|  
    |**預設值**|型別**false**。|  
    |**加入**|按一下以加入新的配接器屬性。|  
  
4.  加入呼叫屬性**HostName**。 此屬性適用於說明用途，類似於屬性**應用程式**。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**屬性名稱**|型別**Hostname**。|  
    |**資料類型**|選取**System.String**。|  
    |**預設值**|型別**lobhostname**。|  
    |**加入**|按一下以加入新的配接器屬性。|  
  
5.  加入呼叫屬性**EchoInUpperCase**。 這個屬性會控制是否將轉換成某些作業回應為大寫的字串，或將其保留其原始格式。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**屬性名稱**|型別**EchoInUpperCase**。|  
    |**資料類型**|選取**System.Boolean**。|  
    |**預設值**|型別**False**。|  
    |**加入**|按一下以加入新的配接器屬性。|  
  
6.  按一下 **[下一步]**。  
  
## <a name="end-the-wizard"></a>結束精靈  
  
1.  在**摘要**頁面上，按一下**完成**。 下圖顯示**方案總管 中**與**EchoAdapter**專案。  
  
     ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/06b45c3e-d056-48f4-a246-642d9ac5e23e.gif "06b45c3e-d056-48f4-a246-642d9ac5e23e")  
  
     您的專案應包含相同的檔案。 如果未出現，請結束 Visual Studio，刪除**EchoAdapterSampleV2**資料夾，然後重新啟動此教學課程的步驟。  
  
2.  在 Visual Studio 中，在**檔案**功能表上，按一下 **全部儲存**。  
  
    > [!NOTE]
    >  您應該已經儲存您的工作結果。 您可以安全地關閉目前的 Visual Studio 或移至下一個步驟中，[步驟 2： 分類的介面卡和連接屬性](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-categorize-the-adapter-and-connection-properties.md)。  
  
## <a name="what-did-i-just-do"></a>我剛剛做什麼？  
 在此步驟中，您必須建立回應配接器解決方案使用 Visual Studio 和[!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]。 下表包含檔案和每個檔案已針對的集合。  
  
|**檔案名稱**|**說明**|  
|-------------------|---------------------|  
|EchoAdapter.cs|這是主要的配接器類別會繼承自`Microsoft.ServiceModel.Channels.Common.Adapter`。<br /><br /> 不不需要回應配接器的任何變更。|  
|EchoAdapterBinding.cs|這是建立配接器的繫結時所使用的類別。<br /><br /> 不不需要回應配接器的任何變更。|  
|EchoAdapterBindingCollectionElement.cs|這是實作的繫結的集合項目類別`System.ServiceModel.Configuration.StandardBindingCollectionElement`。<br /><br /> 不不需要回應配接器的任何變更。|  
|EchoAdapterBindingElement.cs|這個組態項目提供基底類別。<br /><br /> 若要回應配接器的配接器和連接屬性的分類，請遵循[步驟 2： 分類的介面卡和連接屬性](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-categorize-the-adapter-and-connection-properties.md)。|  
|EchoAdapterBindingElementExtensionElement.cs|這個類別提供的繫結項目，以表示配接器，使用於使用者定義 WCF 自訂繫結。<br /><br /> 若要回應配接器的配接器和連接屬性的分類，請遵循[步驟 2： 分類的介面卡和連接屬性](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-categorize-the-adapter-and-connection-properties.md)。|  
|EchoAdapterHandlerBase.cs|這是用來儲存您的基底類別所公開的通用屬性/helper 函式的處理常式的基底類別。<br /><br /> 若要回應配接器的配接器和連接屬性的分類，請遵循[步驟 2： 分類的介面卡和連接屬性](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-categorize-the-adapter-and-connection-properties.md)。|  
|EchoAdapterConnection.cs|這會定義連線到目標系統。<br /><br /> 若要支援回應配接器的連線到目標系統，請遵循[步驟 3： 實作 Echo 介面卡的連線](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md)。|  
|EchoAdapterConnectionFactory.cs|這會定義目標系統的連線 factory。<br /><br /> 若要支援回應配接器的連線到目標系統，請遵循[步驟 3： 實作 Echo 介面卡的連線](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md)。|  
|EchoAdapterConnectionUri.cs|這是表示配接器的連線 Uri 的類別。<br /><br /> 若要支援回應配接器的連線到目標系統，請遵循[步驟 3： 實作 Echo 介面卡的連線](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md))。|  
|EchoAdapterMetadataBrowseHandler.cs|從目標系統的中繼資料執行連線為基礎的瀏覽時，會使用這個類別。<br /><br /> 若要支援中繼資料瀏覽回應配接器的功能，請遵循[步驟 4： 實作回應配接器中繼資料瀏覽的處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md)。|  
|EchoAdapterMetadataSearchHandler.cs|這個類別是用來執行從目標系統的連線為基礎的搜尋中繼資料。<br /><br /> 若要支援搜尋回應配接器的功能的中繼資料，請遵循[步驟 5： 回應配接器實作中繼資料的搜尋處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-5-implement-the-metadata-search-handler-for-the-echo-adapter.md)。|  
|EchoAdapterMetadataResolve.cs|這個類別用來執行從目標系統的連線為基礎的中繼資料擷取。<br /><br /> 若要支援中繼資料解析回應配接器的功能，請遵循[步驟 6： 實作回應配接器中繼資料解析的處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md)。|  
|EchoAdapterOutboundHandler.cs|這個類別用於將資料傳送到目標系統。<br /><br /> 若要回應配接器支援的輸出訊息交換，請遵循[步驟 7： 回應配接器實作同步輸出的處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-7-implement-the-synchronous-outbound-handler-for-the-echo-adapter.md)。|  
|EchoAdapterInboundHandler.cs|這個類別會實作監聽或輪詢資料的介面。<br /><br /> 若要回應配接器支援的輸入的訊息交換，請遵循[步驟 8： 為回應配接器實作同步的輸入處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-8-implement-the-synchronous-inbound-handler-for-the-echo-adapter.md)。|  
|EchoAdapterTrace.cs|這個類別會實作配接器追蹤，偵錯和疑難排解。|  
  
## <a name="next-steps"></a>後續步驟  
 您分類其 UI 邏輯分組，配接器和連接屬性，而接下來實作連接、 中繼資料瀏覽、 搜尋和解析功能，以及在傳出和傳入的訊息交換。 最後，您會建置並部署回應配接器。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 2： 分類的介面卡和連接屬性](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-categorize-the-adapter-and-connection-properties.md)   
 [教學課程 1： 在開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)