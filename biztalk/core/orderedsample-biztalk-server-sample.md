---
title: OrderedSample （BizTalk Server 範例） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples, MQSeries adapters
- orchestrations, examples
- examples, orchestrations
- MQSeries adapters, examples
ms.assetid: 7e59ff43-d425-40cd-9725-af13084f83d9
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b9e93c7bb9cb59088e465dc53dd992ffd5f1c11
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25974748"
---
# <a name="orderedsample-biztalk-server-sample"></a>OrderedSample (BizTalk Server 範例)
OrderedSample 範例會示範如何使用協調流程，以往返方式接收和傳送已排序的訊息序列。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 此範例會假設 MQSeries 佇列中有訊息存在，以便從其中接收訊息。 當配接器從 MQSeries 佇列讀取訊息時，會依序讀取訊息並將其提交至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
 在協調流程，接收埠**mqreceive**，具有其**排序的傳遞**屬性設定為**True**。  
  
 至於傳送端，協調流程會傳送訊息並等待傳遞通知，收到通知後才會傳送下一則訊息。 傳送埠， **mqsend**具有其**傳遞通知**屬性設定為**Transmitted**。 為了讓此範例簡單好用，協調流程將使用無限迴圈。  
  
 協調流程可以接收批次訊息和單一訊息。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 *\<範例路徑\>* \AdaptersUsage\MQSeriesAdapter\OrderedSample  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|----------|-----------------|  
|OrderedReceiveSend.btproj、<br /><br /> OrderedReceiveSend.sln|應用程式的專案和方案檔。|  
|OrderedReceiveSendOrchestration.odx|應用程式的協調流程。|  
|OrderedSample.snk|強式命名金鑰檔。|  
|**Setup.bat**|建置並初始化此範例。|  
  
## <a name="building-and-running-the-sample"></a>建置和執行範例  
  
#### <a name="to-build-and-deploy-the-sample"></a>若要建置和部署範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     `<Samples Path>\AdaptersUsage\MQSeriesAdapter\OrderedSample`  
  
2.  執行檔案 Setup.bat，這會執行下列動作：  
  
    1.  為專案建立強式名稱金鑰。  
  
    2.  編譯和部署協調流程專案。  
  
 如果您有 MQSeries Server for Windows 安裝的必要權限，則可以透過配接器對話方塊建立 MQSeries 佇列並略過下一個程序。 如果您沒有這類存取權限，可以使用 IBM WebSphere MQ Explorer 來建立佇列。 若要透過 WebSphere MQ Explorer 建立佇列，請完成下列步驟：  
  
## <a name="creating-the-mqseries-queues-through-the-websphere-mq-explorer"></a>透過 WebSphere MQ Explorer 建立 MQSeries 佇列  
  
#### <a name="to-create-the-mqseries-queues-through-the-websphere-mq-explorer"></a>若要透過 WebSphere MQ Explorer 建立 MQSeries 佇列  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **IBM WebSphere MQ**，然後按一下  **WebSphere MQ Explorer**。  
  
2.  按兩下**佇列管理員**，然後按兩下**預設佇列管理員**。 預設佇列管理員的名稱通常為 QM_<machine_name>，其中 machine_name 是電腦的名稱。  
  
3.  以滑鼠右鍵按一下**佇列**，指向 **新增**，然後按一下 **本機佇列**。  
  
4.  在**建立本機佇列**對話方塊中，於**佇列名稱**，型別 **"queue1"**，然後按一下  **確定**。  
  
5.  以滑鼠右鍵按一下**佇列**，按一下 **新增**，然後按一下 **本機佇列**。  
  
6.  中**建立本機佇列**對話方塊中，於**佇列名稱**，型別 **"queue2"**，然後按一下 **確定**。  
  
## <a name="creating-the-receive-location-and-the-mqseries-queue"></a>建立接收位置與 MQSeries 佇列  
 此程序會建立傳送埠和接收位置，以傳送訊息至 MQSeries 以及接收來自 MQSeries 的相互關聯訊息。 如果您還沒有建立 MQSeries 佇列，則在建立接收位置時，也會建立 MQSeries 佇列。  
  
#### <a name="to-create-the-receive-location-and-the-mqseries-queue"></a>建立接收位置與 MQSeries 佇列  
  
1.  開啟 BizTalk Server 管理主控台。  
  
2.  展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開所需的應用程式。  
  
3.  以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**。  
  
4.  在**單向接收埠屬性**對話方塊方塊中，輸入，在**名稱**方塊中，輸入**OrderedSampleReceive**按一下**確定**。  
  
5.  在左窗格中，按一下 **接收位置**索引標籤，然後再按一下**新增**。  
  
6.  在**接收位置屬性**對話方塊中，於**名稱**方塊中，輸入 「**OrderedSampleReceiveLocation**"。  
  
7.  在**傳輸類型**方塊中，選取**MQSeries**。  
  
8.  在**接收處理常式**方塊中，選取**BizTalkServerApplication**。  
  
9. 在**接收管線**方塊中，選取**Microsoft.BizTalk.DefaultPipelines.PassThruReceive**。  
  
10. 按一下**設定**。  
  
11. 在**MQSeries 傳輸屬性**對話方塊中，於**輪詢間隔**方塊中，輸入 **"10"**。  
  
12. 在**佇列定義**方塊中，按一下**省略符號 （...）**  按鈕。  
  
13. 在**佇列定義**對話方塊中，於**伺服器名稱**方塊中，輸入您的電腦名稱。  
  
14. 在**佇列管理員**方塊中，選取**預設佇列管理員**。  
  
15. 在**佇列**方塊中，輸入 「 **queue1**"，然後按一下 **匯出**。  
  
16. 在**匯出**對話方塊中，按一下**Create Queue**，然後按一下**確定**或**完成**直到結束所有對話方塊。  
  
## <a name="creating-the-send-port-and-mqseries-queue"></a>建立傳送埠和 MQSeries 佇列  
  
#### <a name="to-create-the-send-port-and-mqseries-queue"></a>若要建立傳送埠和 MQSeries 佇列  
  
1.  以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。  
  
2.  在**靜態連接埠屬性**對話方塊方塊中，輸入，在**名稱**方塊中，輸入 「**OrderedSampleSend**"。  
  
3.  在**傳輸類型**方塊中，選取**MQSeries**。  
  
4.  在**傳送管線**方塊中，選取**Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**。  
  
5.  按一下**設定**。  
  
6.  在**MQSeries 傳輸屬性**對話方塊中，於**佇列定義**方塊中，按一下**省略符號 （...）**  按鈕。  
  
7.  在**佇列定義**對話方塊中，於**伺服器名稱**方塊中，輸入您的電腦名稱。  
  
8.  在**佇列管理員**方塊中，選取**預設佇列管理員**。  
  
9. 在**佇列**方塊中，輸入 「 **queue2**"，然後按一下 **匯出**。  
  
10. 在**匯出**對話方塊中，按一下**Create Queue**，然後按一下**確定**或**完成**直到結束所有對話方塊。  
  
#### <a name="to-enable-the-receive-location-and-start-the-send-port"></a>啟用接收位置和啟動傳送埠  
  
1.  在 BizTalk Server 管理主控台中，按一下 **接收埠**。  
  
2.  在詳細資料窗格中，以滑鼠右鍵按一下**MQIn**接收位置，然後按一下 **啟用**。  
  
3.  在詳細資料窗格中，以滑鼠右鍵按一下**MQOut**傳送連接埠，然後按一下**開始。**  
  
#### <a name="to-bind-and-start-the-orchestration"></a>若要繫結並啟動協調流程  
  
1.  在 BizTalk Server 管理主控台中，展開 **協調流程**資料夾。  
  
2.  按兩下 **[orderedsampleorchestration]** 協調流程，然後再按一下**繫結**。  
  
3.  將協調流程連接埠繫結至下列傳送埠和接收位置：  
  
    |協調流程連接埠|傳送埠/接收位置|  
    |------------------------|----------------------------------------|  
    |mqreceive|OrderedSampleReceive|  
    |mqsend|OrderedSampleSend|  
  
4.  按一下**主機**。  
  
5.  在**主機**方塊中，選取**BizTalkServerApplication**，按一下**確定**。  
  
6.  以滑鼠右鍵按一下**協調流程**按一下**啟動**。  
  
#### <a name="to-run-the-sample"></a>執行範例  
  
1.  啟動協調流程。  
  
2.  將訊息放入您已設定接收位置要從中讀取的 MQSeries 佇列。  
  
3.  使用 WebSphere MQ Explorer 檢視傳送佇列 (您已設定傳送埠要將訊息傳送至此佇列) 內的訊息。  
  
## <a name="see-also"></a>請參閱  
 [MQSeries 配接器範例](../core/mqseries-adapter-samples.md)