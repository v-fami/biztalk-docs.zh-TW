---
title: MQSSendPipelineComponent （BizTalk Server 範例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples, MQSeries adapters
- pipelines, examples
- MQSeries adapters, examples
- examples, pipelines
ms.assetid: ac709e45-524b-45ab-9673-060790ecbed2
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cc89b19f1e493c46e6128d390774479eb59bc6b0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975911"
---
# <a name="mqssendpipelinecomponent-biztalk-server-sample"></a>MQSSendPipelineComponent (BizTalk Server 範例)
本範例示範如何撰寫可從 XML 檔案讀取一組 MQSeries 屬性值，並將這些屬性值套用至訊息的管線元件。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 本範例由兩個 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案組成，分別是一個管線元件專案以及一個可利用該管線元件的管線專案。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
  
- *\<SamplesPath\>* \AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent\SetMQSeriesHeaderPropertyComponent  
  
- *\<SamplesPath\>* \AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent\SetMQSeriesHeaderPropertyPipeline  
  
  下表顯示此範例中的檔案，並描述其用途。  
  
|                                                                              **檔案**                                                                               |                                         **說明**                                          |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|
| SetMQSeriesHeaderPropertyComponent\SetMQSeriesHeaderPropertyComponent.sln,<br /><br /> SetMQSeriesHeaderPropertyComponent\SetMQSeriesHeaderPropertyComponent.csproj |                    管線元件的專案和方案檔。                    |
|                                              SetMQSeriesHeaderPropertyComponent\CSetMQSeriesHeaderPropertyComponent.cs                                              |                      管線元件的 Visual C#® 原始程式檔。                      |
|                                                      SetMQSeriesHeaderPropertyComponent\SetMQSMQMDHdrProps.xml                                                      |                 管線元件讀取及使用的 MQSeries 屬性。                 |
|   SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.btproj,<br /><br /> SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.sln   |                     BizTalk 管線的專案和方案檔。                     |
|                                               SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.snk                                               |                   BizTalk 管線元件的強式命名金鑰檔案。                   |
|                                               SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.btp                                               | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管線。 |
  
## <a name="how-to-use-this-sample"></a>如何使用此範例  
 若要建立此應用程式，您必須完成下列步驟：  
  
1. 建立應用程式的資料夾。  
  
2. 修改及編譯管線元件的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。  
  
3. 將編譯後的組件和標頭檔複製到適當的資料夾。  
  
4. 修改 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 管線的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 專案。  
  
5. 編譯及部署 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管線專案。  
  
6. 設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置。  
  
7. 建立 MQSeries 佇列。  
  
8. 設定傳送埠。  
  
9. 啟用接收位置並啟動傳送埠。  
  
## <a name="creating-the-folders-for-the-application"></a>為應用程式建立資料夾  
 這個程序會為應用程式建立適當的資料夾。  
  
#### <a name="to-create-the-folders-for-the-application"></a>若要為應用程式建立資料夾  
  
1.  建立名為的資料夾**temp**在 C:\ 磁碟機不存在時。  
  
2.  下建立資料夾**C:\temp**名為目錄**Pickup3**。  
  
## <a name="modifying-and-compiling-the-project-for-the-pipeline-component"></a>修改及編譯管線元件的專案  
 這個程序會修改及編譯管線元件的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。  
  
#### <a name="to-modify-and-compile-the-project-for-the-pipeline-component"></a>若要修改及編譯管線元件的專案  
  
1. 按兩下方案檔 **[setmqseriesheaderpropertycomponent\setmqseriesheaderpropertycomponent.sln]** 來開啟的方案中[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。  
  
2. 按兩下類別檔 **[csetmqseriesheaderpropertycomponent.cs]** 以開啟中的類別檔案[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。  
  
3. 找出變數**samplesDir**，確認這個變數設為位置**C:\temp**。  
  
4. 以滑鼠右鍵按一下 方案總管 中的方案，然後按一下 **建置**。 這會將專案編譯成 dll，位於**SetMQSeriesHeaderPropertyComponent\SetMQSeriesHeaderPropertyComponent\bin\Debug\\** 目錄。  
  
## <a name="copying-the-assembly-and-header-file-to-appropriate-folders"></a>將組件和標頭檔複製到適當的資料夾  
 這個程序會將編譯後的組件和標頭檔複製到適當的資料夾。  
  
#### <a name="to-copy-the-compiled-assembly-and-header-file-to-the-appropriate-folders"></a>若要將編譯後的組件和標頭檔複製到適當的資料夾  
  
1. 將已編譯的組件複製**SetMQSeriesHeaderPropertyComponent.dll** BizTalk 管線元件資料夾。 BizTalk 管線元件資料夾的預設位置是 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Pipeline Components。  
  
2. 將 MQHeader 屬性檔複製**SetMQSMQMDHdrProps.xml**要**C:\temp**目錄。  
  
## <a name="modifying-the-project-for-the-biztalk-server-pipeline"></a>修改 BizTalk Server 管線的專案  
 這個程序會修改 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 管線的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 專案。  
  
#### <a name="to-modify-the-project-for-the-biztalk-server-pipeline"></a>若要修改 BizTalk Server 管線的專案  
  
1. 在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，按兩下方案檔中，開啟方案 **[setmqseriesheaderpropertypipeline\setmqseriesheaderpropertypipeline.sln]**。  
  
2. 為專案建立強式名稱金鑰檔案。 若要這樣做，請執行以下動作：  
  
   1. 開啟 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 命令提示字元。  
  
   2. 將目錄變更為\<範例路徑\>\AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent。  
  
   3. 輸入以下內容：  
  
       `sn -k MQSSendPipelineComponent.snk`  
  
   4. 按 ENTER 鍵。 金鑰檔隨即建立。  
  
3. 在 **方案總管**，以滑鼠右鍵按一下專案，然後按一下**屬性**專案期間 （在 中心 視窗中） 為啟動專案設計工具。  
  
   1.  在 [專案設計工具中，按一下**簽署**] 索引標籤。  
  
   2.  在右窗格中，選取**簽署組件**選項...  
  
   3.  按一下下拉式清單，如**選擇強式名稱金鑰檔**選項，然後按一下**瀏覽**。  
  
   4.  瀏覽至\<範例路徑\>\AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent\MQSSendPipelineComponent.snk，按一下**開啟**。  
  
4. 您稍早建立的管線元件已加入至**Pre-assemble**這個管線專案的階段。 如果這個元件尚未加入，您必須完成下列步驟將它加入：  
  
   1. 在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] IDE 中，按一下**工具箱**左邊的索引標籤。  
  
   2. 以滑鼠右鍵按一下**工具箱**，然後按一下**選擇項目**。  
  
   3. 在 [**選擇工具箱項目**] 對話方塊中，按一下**BizTalk 管線元件**索引標籤上，選取**自訂元件以設定 MQseries 標頭屬性**元件，並然後按一下**確定**。  
  
   4. 拖曳**自訂元件以設定 MQseries 標頭屬性**元件至**Pre-assemble**此管線的階段。  
  
## <a name="compiling-and-deploying-the-pipeline-project"></a>編譯及部署管線專案  
 這個程序會編譯及部署 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管線專案。  
  
#### <a name="to-compile-and-deploy-the-pipeline-project"></a>若要編譯及部署管線專案  
  
1.  在 [方案總管] 視窗中，以滑鼠右鍵按一下方案，然後**部署方案**。 這樣會建置解決方案並將組件部署至 BizTalk 管理資料庫。  
  
2.  確認組件已部署至 BizTalk 管理資料庫：  
  
    1.  開啟 [BizTalk 管理主控台]。  
  
    2.  按一下以展開**BizTalk 群組 [\<servername\>:\<管理資料庫\>]**，然後按一下以展開**組件**資料夾。  
  
         已部署的管線組件應該會顯示在**組件**資料夾。  
  
## <a name="creating-the-receive-location"></a>建立接收位置  
 這個程序會建立 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置。  
  
#### <a name="to-create-the-receive-location"></a>若要建立接收位置  
  
1.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**接收連接埠**，指向**新增**，然後按一下**單向接收埠**。  
  
2.  在 **單向接收埠屬性**對話方塊中，於**名稱**方塊中輸入"MQReply"，然後按一下**確定**。  
  
3.  在左窗格中，按一下**接收位置**索引標籤，然後再按一下**新增**。  
  
4.  在 **接收位置屬性**對話方塊中，於**名稱**欄位中，輸入"ReceiveFile"。  
  
5.  在 **傳輸類型**方塊中，選取**檔案**。  
  
6.  在 **接收處理常式**欄位中，選取**BizTalkServerApplication**。  
  
7.  在 **接收管線**欄位中，選取**Microsoft.BizTalk.DefaultPipelines.PassThruReceive**。  
  
8.  在 **接收資料夾**欄位中，輸入"C:\temp\Pickup3"。  
  
9. 在 **檔案遮罩**欄位中，輸入"*。\*"。  
  
10. 按一下  **確定**，然後按一下**確定**  以結束**接收位置屬性** 對話方塊。  
  
## <a name="creating-a-mqseries-queue-through-the-mqseries-explorer"></a>透過 MQSeries Explorer 建立 MQSeries 佇列  
 如果您有 MQSeries Server for Windows 安裝的必要權限，則可以透過配接器對話方塊建立 MQSeries 佇列並略過下一個程序。  
  
 如果您沒有這類存取權限，可以依照下列程序使用 IBM WebSphere MQ Explorer 來建立佇列。  
  
#### <a name="to-create-a-mqseries-queue-through-the-mqseries-explorer"></a>若要透過 MQSeries Explorer 建立 MQSeries 佇列  
  
1.  按一下 **開始**，指向**程式**，指向**IBM WebSphere MQ**，然後按一下**WebSphere MQ Explorer**。  
  
2.  按兩下**佇列管理員**，然後按兩下預設佇列管理員。 預設佇列管理員通常會命名為**Qm_&lt**\<*machine_name* \>其中*machine_name*是您電腦的名稱。  
  
3.  以滑鼠右鍵按一下**佇列**，指向**新增**，然後按一下**本機佇列**。  
  
4.  中**建立本機佇列**對話方塊中，於**佇列名稱**，型別**SETHEADER**，然後按一下 **確定**。  
  
## <a name="creating-the-send-port-and-mqseries-queue"></a>建立傳送埠和 MQSeries 佇列  
 這個程序會建立輸出訊息所使用的傳送埠。 如果您還沒有建立 MQSeries 佇列，在建立傳送埠時，也會建立 MQSeries 佇列。  
  
#### <a name="to-create-the-send-port-and-mqseries-queue"></a>若要建立傳送埠和 MQSeries 佇列  
  
1.  以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下**靜態單向傳送埠**。  
  
2.  在 **傳送埠屬性**對話方塊中，於**名稱**方塊中，輸入"MQSolicitResponse"。  
  
3.  在 **傳輸類型**方塊中，選取**MQSeries**。  
  
4.  在 **傳送管線**方塊中，選取**setmqseriesheaderpropertypipeline.setmqseriesheaderssendpipeline**。  
  
5.  在 **篩選**，具有下列名稱/值組加入新項目：  
  
    -   設定**屬性**來 「 BTS。ReceivePortName"。  
  
    -   設定**運算子**以 「 = = 」。  
  
    -   設定**值**為"ReceiveFile"。  
  
        > [!NOTE]
        >  這樣會將傳送埠設定為訂閱到達 ReceiveFile 接收埠的訊息。  
  
6.  按一下 **傳輸**。  
  
7.  在 **位址 (URI)** 欄位中，按一下省略符號 （...） 按鈕。  
  
8.  在  **MQSeries 傳輸屬性**對話方塊中，於**佇列定義**欄位中，按一下省略符號 （...） 按鈕。  
  
9. 在 **佇列定義**對話方塊中，於**伺服器名稱**欄位中，輸入您的電腦名稱。  
  
10. 在 **佇列管理員**欄位中，選取預設佇列管理員。  
  
11. 在 [佇列] 欄位中，輸入"SETHEADER"，然後再按一下**匯出**。  
  
12. 在 **匯出** 對話方塊中，按一下**Create Queue**，然後按一下  **確定**或**完成**直到結束所有對話方塊為止。  
  
## <a name="enabling-the-receive-location-and-starting-the-send-port"></a>啟用接收位置及啟動傳送埠  
 這個程序會啟用接收位置及啟動傳送埠。  
  
#### <a name="to-enable-the-receive-location-and-start-the-send-port"></a>啟用接收位置和啟動傳送埠  
  
1.  在 BizTalk Server 管理主控台中，按一下**接收埠**。  
  
2.  在 [詳細資料] 窗格中，以滑鼠右鍵按一下**MQIn**接收位置，然後按一下**啟用**。  
  
3.  在 [詳細資料] 窗格中，以滑鼠右鍵按一下 **[setmqheader]** 傳送埠，然後按一下**開始**。  
  
## <a name="testing-the-application"></a>測試應用程式  
 這個程序會測試應用程式。  
  
#### <a name="to-test-the-application"></a>若要測試應用程式  
  
1.  將檔案放**C:\Temp\Pickup3**資料夾。  
  
2.  啟動 WebSphere MQ Explorer，然後按兩下 [SETHEADER] 佇列，檢查 SETHEADER 佇列中的訊息。  
  
     若要查看 SETHEADER 佇列中訊息的所有內容屬性，請完成下列步驟：  
  
    1.  按兩下**SETHEADER**佇列，以便顯示**訊息瀏覽器** 對話方塊。  
  
    2.  在 **訊息瀏覽器** 對話方塊中，按一下**資料行**以顯示**訊息的顯示/隱藏資料行** 對話方塊。  
  
    3.  底下**可用的資料行**，連按兩下 若要顯示在每個項目**訊息瀏覽器**對話方塊，然後再按一下**確定**。  
  
3.  每個訊息的訊息內容屬性應該會顯示在**訊息瀏覽器** 對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [MQSeries 配接器範例](../core/mqseries-adapter-samples.md)