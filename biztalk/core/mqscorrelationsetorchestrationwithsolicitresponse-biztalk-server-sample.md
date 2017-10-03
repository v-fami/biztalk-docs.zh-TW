---
title: "MQSCorrelationSetOrchestrationWithSolicitResponse （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, MQSeries adapters
- orchestrations, examples
- examples, orchestrations
- examples, messages
- messages, examples
- MQSeries adapters, examples
ms.assetid: 5127d743-bb79-4e97-a2f3-446892e1bfa0
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2665967e27cf708fcdbbddf61a7b66c619757223
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="mqscorrelationsetorchestrationwithsolicitresponse-biztalk-server-sample"></a>MQSCorrelationSetOrchestrationWithSolicitResponse (BizTalk Server 範例)
MQSCorrelationSetOrchestrationWithSolicitResponse 範例將示範如何使用 MQSeries Server (而非 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]) 產生的相互關聯識別項。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 協調流程傳送的值是空的訊息**MQMD_MsgID**訊息標頭中的屬性。 MQSeries 產生 MessageID 和 CorrelationID，並傳回一則訊息，並將值指派至**MQMD_MsgID**和**MQMD_CorrelId**一部分的回應請求-回應傳送配接器的連接埠. 協調流程使用產生的相互關聯識別項來初始化相互關聯集的相互關聯集在後續接收位置和藉由檢查**MQMD_CorrelId**訊息屬性。 配接器也會將指派的相互關聯識別項**BizTalk_CorrelationID**，您也可以使用協調流程中。 如需使用相互關聯識別項使用配接器的詳細資訊，請參閱[相互關聯訊息使用要求-回覆](../core/correlating-messages-using-request-reply.md)。  
  
> [!IMPORTANT]
>  如果 MQSeries Server 傳送的訊息比相互關聯識別項先抵達，使用這種方式的協調流程可能會發生問題。 請確定您在設計協調流程時，給予 MQSeries Server 足夠的時間傳回相互關聯識別項。 本範例並未將這種可能的競爭情形列入考量。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 *\<範例路徑 >*\AdaptersUsage\MQSeriesAdapter\MQSCorrelationSetOrchestrationWithSolicitResponse  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|**檔案**|**說明**|  
|--------------|---------------------|  
|**MQSCorrelationSolicitResponse.btproj，**<br /><br /> **[Mqscorrelationsolicitresponse.sln]**|應用程式的專案和方案檔。|  
|**[Mqscorrelationsolicitresponse.odx]**|應用程式的 BizTalk 協調流程檔案。|  
|**MQSCorrelationSolicitResponse.snk**|強式命名金鑰檔。|  
|Setup.bat|建置並初始化此範例。|  
  
## <a name="how-to-use-this-sample"></a>如何使用此範例  
 若要建立此應用程式，您必須完成下列步驟：  
  
-   建立兩個 MQSeries 佇列。  
  
-   設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置和傳送埠。  
  
-   啟用接收位置。  
  
-   啟動傳送埠。  
  
-   建立適當的資料夾。  
  
-   修改協調流程。  
  
-   部署、繫結和啟動協調流程。  
  
 如果您有 MQSeries Server for Windows 安裝的必要權限，則可以透過配接器對話方塊建立 MQSeries 佇列並略過下一個程序。 如果您沒有這類存取權限，可以使用 IBM WebSphere MQ Explorer 來建立佇列。 若要透過 WebSphere MQ Explorer 建立佇列，請完成下列步驟：  
  
## <a name="creating-the-mqseries-queues-through-the-websphere-mq-explorer"></a>透過 WebSphere MQ Explorer 建立 MQSeries 佇列  
  
#### <a name="to-create-the-mqseries-queues-through-the-websphere-mq-explorer"></a>若要透過 WebSphere MQ Explorer 建立 MQSeries 佇列  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **IBM WebSphere MQ**，然後按一下  **WebSphere MQ Explorer**。  
  
2.  按兩下**佇列管理員**，然後按兩下預設佇列管理員。 預設佇列管理員通常會命名為**Qm_<***< machine_name >*其中*machine_name*是您的電腦名稱。  
  
3.  以滑鼠右鍵按一下**佇列**，指向 **新增**，然後按一下 **本機佇列**。  
  
4.  在**建立本機佇列**對話方塊中，於**佇列名稱**，輸入"REPLYTOQ"，然後按**確定**。  
  
5.  以滑鼠右鍵按一下**佇列**，按一下 **新增**，然後按一下 **本機佇列**。  
  
6.  在**建立本機佇列**對話方塊中，於**佇列名稱**，輸入"SOLICITRESPONSEQ"，然後按**確定**。  
  
## <a name="creating-the-receive-location-and-the-mqseries-queue"></a>建立接收位置與 MQSeries 佇列  
 此程序會建立傳送埠和接收位置，以傳送訊息至 MQSeries 以及接收來自 MQSeries 的相互關聯訊息。 如果您還沒有建立 MQSeries 佇列，則在建立接收位置時，也會建立 MQSeries 佇列。  
  
#### <a name="to-create-the-receive-location-and-the-mqseries-queue"></a>建立接收位置與 MQSeries 佇列  
  
1.  開啟 BizTalk Server 管理主控台。  
  
2.  展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開所需的應用程式。  
  
3.  以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**。  
  
4.  在**單向接收埠屬性**對話方塊中，於**名稱**方塊中輸入"MQReply"，然後按一下 **確定**。  
  
5.  在左窗格中，按一下 **接收位置**索引標籤，然後再按一下**新增**。  
  
6.  在**接收位置屬性**對話方塊中，於**名稱**方塊中，輸入"MQReply"。  
  
7.  在**傳輸類型**方塊中，選取**MQSeries**。  
  
8.  在**接收處理常式**方塊中，選取**BizTalkServerApplication**。  
  
9. 在**接收管線**方塊中，選取**Microsoft.BizTalk.DefaultPipelines.PassThruReceive**。  
  
10. 按一下**設定**。  
  
11. 在**MQSeries 傳輸屬性**對話方塊中，於**輪詢間隔**方塊中，輸入"10"。  
  
12. 在**佇列定義**方塊中，按一下省略符號 （...） 按鈕。  
  
13. 在**佇列定義**對話方塊中，於**伺服器名稱**方塊中，輸入您的電腦名稱。  
  
14. 在**佇列管理員**方塊中，選取預設佇列管理員。  
  
15. 在**佇列**方塊中輸入"REPLYTOQ"，然後再按一下**匯出**。  
  
16. 在**匯出**對話方塊中，按一下**Create Queue**，然後按一下**確定**或**完成**直到結束所有對話方塊。  
  
## <a name="creating-the-send-port-and-mqseries-queue"></a>建立傳送埠和 MQSeries 佇列  
  
#### <a name="to-create-the-send-port-and-mqseries-queue"></a>若要建立傳送埠和 MQSeries 佇列  
  
1.  以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。  
  
2.  在**傳送埠屬性**對話方塊中，於**名稱**方塊中，輸入"MQSolicitResponse"。  
  
3.  在**傳輸類型**方塊中，選取**MQSeries**。  
  
4.  在**傳送管線**方塊中，選取**Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**。  
  
5.  在**接收管線**方塊中，選取**Microsoft.BizTalk.DefaultPipelines.PassThruReceive**。  
  
6.  按一下**設定**。  
  
7.  在**MQSeries 傳輸屬性**對話方塊中，於**佇列定義**方塊中，按一下省略符號 （...） 按鈕。  
  
8.  在**佇列定義**對話方塊中，於**伺服器名稱**方塊中，輸入您的電腦名稱。  
  
9. 在**佇列管理員**方塊中，選取預設佇列管理員。  
  
10. 在**佇列**方塊中輸入"SOLICITRESPONSEQ"，然後再按一下**匯出**。  
  
11. 在 匯出 對話方塊中，按一下  **Create Queue**，然後按一下 **確定**或**完成**直到結束所有對話方塊。  
  
## <a name="enabling-the-receive-location-and-starting-the-send-port"></a>啟用接收位置及啟動傳送埠  
 這個程序會建立協調流程接收檔案所需的資料夾，並將相互關聯訊息和回應訊息傳送到輸出資料夾。  
  
#### <a name="to-enable-the-receive-location-and-start-the-send-port"></a>啟用接收位置和啟動傳送埠  
  
1.  在 BizTalk Server 管理主控台中，按一下 **接收埠**。  
  
2.  在詳細資料窗格中，以滑鼠右鍵按一下**MQIn**接收位置，然後按一下 **啟用**。  
  
3.  在詳細資料窗格中，以滑鼠右鍵按一下**MQOut**傳送連接埠，然後按一下**開始。**  
  
## <a name="creating-the-folders-used-by-the-application"></a>建立應用程式使用的資料夾  
  
#### <a name="to-create-the-folders-used-by-the-application"></a>若要建立應用程式使用的資料夾  
  
1.  在 C:\ 磁碟機上建立名為 "temp" 的資料夾 (如果沒有的話)。  
  
2.  建立資料夾下的**C:\temp**目錄名為"Pickup2"、"Dropit2"和"MoveIt"。  
  
## <a name="modifying-the-orchestration-used-by-the-application"></a>修改應用程式使用的協調流程  
 這個程序會修改應用程式使用的協調流程。  
  
||  
|-|  
|若要修改應用程式使用的協調流程|  
|-在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，按兩下方案檔， **[mqscorrelationsolicitresponse.sln]**，若要開啟的方案。<br /><br /> -從 方案總管 窗格中，按兩下 協調流程**mqscorrelationsolicitresponse.odx**檢視協調流程。<br /><br /> -按兩下訊息指派圖形**MessageAssignment_1**以啟動 BizTalk 運算式編輯器。<br /><br /> 輸入下列運算式為適當的 MQSeries 佇列管理員名稱：<br /><br /> `MQSeriesRequestSendMessage(MQSeries.MQMD_ReplyToQMgr) = "QM_<machine_name>";`<br /><br /> -如果您想要從 BizTalk 傳送到包含原始訊息而不是只有前 100 個位元組的整個內容的回應訊息，修改下列行在 「 BizTalk 運算式編輯器。<br /><br /> -原始行：<br /><br /> `MQSeriesRequestSendMessage(MQSeries.MQMD_Report) = 768;`<br /><br /> 若要變更：<br /><br /> `MQSeriesRequestSendMessage(MQSeries.MQMD_Report) = 1792;`<br /><br /> -在 BizTalk 運算式編輯器 」 中，按一下**確定**以儲存修改過的運算式。<br /><br /> -在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，選取**檔案**，然後選取**全部儲存**。|  
  
## <a name="building-and-deploying-the-sample"></a>建置和部署範例  
 這個程序會建置和部署包含此應用程式所使用協調流程的方案。  
  
#### <a name="to-build-and-deploy-the-sample"></a>若要建置和部署範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     `<Samples Path>\AdaptersUsage\MQSeriesAdapter\MQSCorrelationSetOrchestrationWithSolicitResponse`  
  
2.  執行檔案 Setup.bat，這會執行下列動作：  
  
    1.  為專案建立強式名稱金鑰。  
  
    2.  編譯和部署協調流程專案。  
  
    3.  使用 FILE 配接器建立傳送埠和接收埠。  
  
    > [!NOTE]
    >  由於這個協調流程指定使用 FILE 配接器傳送和接收檔案的繫結，因此當您部署協調流程時，會建立必要的傳送埠、接收埠和接收位置，以供協調流程接收檔案並輸出相互關聯訊息和回應訊息。  
  
## <a name="binding-and-starting-the-orchestration"></a>繫結與啟動協調流程  
 這個程序會繫結協調流程與主控件以及適當的傳送埠和接收位置。  
  
#### <a name="to-bind-and-start-the-orchestration"></a>若要繫結並啟動協調流程  
  
1.  在 BizTalk Server 管理主控台中，展開 **協調流程**資料夾。  
  
2.  在詳細資料窗格中，以滑鼠右鍵按一下**[mqscorrelationsolicitresponse]**協調流程，然後按一下**繫結**。  
  
3.  將協調流程連接埠繫結至下列傳送埠和接收位置：  
  
    |**協調流程連接埠**|**傳送埠 / 接收位置**|  
    |----------------------------|--------------------------------------------|  
    |FileReceivePort|MQSCorrelationSolicitResponse.Orchestration.FileReceivePort|  
    |MQSeriesResponseReceivePort|MQReply|  
    |SolicitResponsePort|MQSolicitResponse|  
    |TempPort|MQSCorrelationSolicitResponse.Orchestration.TempPort|  
    |FileSendPort|MQSCorrelationSolicitResponse.Orchestration.FileSendPort|  
  
4.  按一下**主機**。  
  
5.  在**主機**方塊中，選取**BizTalkServerApplication**按一下**確定**。  
  
6.  在**傳送埠**，以滑鼠右鍵按一下**[mqscorrelationsolicitresponse.orchestration.tempport]**，然後選取**啟動**。  
  
7.  在**傳送埠**，以滑鼠右鍵按一下**[mqscorrelationsolicitresponse.orchestration.filesendport]**，然後選取**啟動**。  
  
8.  在**接收位置**，以滑鼠右鍵按一下**[mqscorrelationsolicitresponse.orchestration.filereceiveport]**，然後選取**啟用**。  
  
9. 以滑鼠右鍵按一下協調流程，然後按一下**啟動**。  
  
    > [!NOTE]
    >  啟動協調流程也會自動登錄協調流程。  
  
## <a name="testing-the-application"></a>測試應用程式  
 這個程序會測試應用程式。  
  
#### <a name="to-test-the-application"></a>若要測試應用程式  
  
1.  將檔案放在**C:\Temp\Pickup2**資料夾。  
  
2.  檢查中的檔案**C:\Temp\Dropit2**資料夾和**C:\Temp\Moveit**資料夾。  
  
    -   **C:\Temp\Dropit2**資料夾應包含已原本收取訊息的複本[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
    -   **C:\Temp\Moveit**資料夾應包含回應文件的訊息識別項 (MQMD_MsgId) 和相互關聯識別項 (MQMD_CorrelId)。  
  
    > [!NOTE]
    >  如果您停用**MQReply**接收位置，您可以檢查 WebSphere MQ Explorer 中的訊息，並查看所設定的訊息和相互關聯識別項。 若要這樣做，請啟動**WebSphere MQ Explorer**並檢查訊息置於**REPLYTOQ**佇列。 訊息和相互關聯識別碼會顯示在**識別碼** 索引標籤**Messageproperties**  對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [使用要求-回覆相互關聯訊息](../core/correlating-messages-using-request-reply.md)   
 [MQSeries 配接器範例](../core/mqseries-adapter-samples.md)