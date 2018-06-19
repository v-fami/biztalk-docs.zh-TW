---
title: 大型訊息至 MSMQ |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fb87b46-5656-42c0-be99-8ab66e51bb4d
caps.latest.revision: 35
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 008e6c2d775fc5d46977ca4672b6d3376349b3f0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25976108"
---
# <a name="large-message-to-msmq"></a>用於 MSMQ 的大型訊息
大型的訊息至 MSMQ 範例示範如何傳送的.xml 文件大於 4 mb 從 Message Queuing (也稱為 MSMQ) BizTalk MSMQ 配接器使用**MQSendLargeMessage**藉由應用程式開發介面MQRTLarge.dll。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 範例的運作方式如下：  
  
1.  使用者使用 SendLargeMessage.exe，將大型.xml 檔案傳送至本機電腦上的佇列。  
  
2.  BizTalk Server 會從佇列接收大型.xml 檔案，並將它複製到本機目錄。  
  
 訊息佇列中的許多作業都是非同步的。 也就是說，許多 MSMQ API 呼叫 (例如， **MQSendLargeMessage**) 傳回給呼叫端要求的作業完全完成之前。  
  
 MSMQ 提供一項機制，會在作業全部完成之後將回應傳遞至應用程式。 這個機制需要用到「管理佇列」。 MSMQ 管理佇列中訊息的形式，傳回的意見反應。 當進行原始 MSMQ API 呼叫時，便會指定 MSMQ 要將回應傳送所至的管理佇列。 因此，範例中，當傳送訊息，使用**MQSendLargeMessage** API，應用程式可以指定管理佇列的名稱使用**PROPID_M_ADMIN_QUEUE**訊息在訊息上的屬性傳入呼叫**MQSendLargeMessage**。 即使應用程式可能取得成功的傳回碼**MQSendLargeMessage**呼叫時，如果後續訊息傳送作業失敗，MSMQ 訊息寫入該效果指定管理佇列。  
  
 如果應用程式未指定管理佇列，傳送失敗將會導致訊息遺失而無法擷取診斷資訊，訊息將會毫無跡象地消失。 MSMQ 中的錯誤情況的數目可能會造成這種情形，例如，非交易式傳送至異動式佇列。  
  
 在此範例的內容，是很重要的程式碼呼叫中指定交易類型**MQSendLargeMessage**這與指定傳送訊息佇列的交易支援一致。 如果未進行此設定，而且如果沒有指定管理佇列是 （在此情況下在此範例中），MSMQ 捨棄傳送的訊息，它確實會留下任何跡象 （也就是沒有錯誤碼傳回至應用程式，而不將診斷資訊寫入事件記錄檔依此類推)。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 \<範例路徑\>\AdaptersUsage\MSMQLarge  
  
> [!NOTE]
>  如果使用 64 位元版本的 Windows 和 BizTalk Server，將範例安裝在**C:\Program Files (x86) \Microsoft BizTalk Server\<版本\>\SDK\Samples\AdaptersUsage\MSMQLarge**資料夾。  請注意這項變更，在此文件中使用的其他指示**C:\Program Files**資料夾。  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|**檔案**|**說明**|  
|--------------|---------------------|  
|**MQRTLarge.dll**|提供原生訊息佇列的附加元件。 公開**MQSendLargeMessage**和**MQReceiveLargeMessage**應用程式開發介面。<br /><br /> 若要存取 MQRTLarge.dll 的 64 位元版本，您必須在 64 位元版本的 Windows 上安裝 BizTalk Server。<br /><br /> MSMQ 未搭配 BizTalk Server 解決方案，MQRTLarge.dll 可能仍正常運作。 不過，這不是建議的設定，Microsoft 支援，而且如果在 BizTalk Server 環境之外使用，可能會發生非預期的結果。|  
|||  
|**LargeMessages.sln**|提供 Visual Studio 解決方案以建立範例中使用的 SendLargeMessage 可執行檔。|  
|**XMLCreator.sln**|提供 Visual Studio 解決方案來建立 XMLCreator 可執行檔，以產生 SDK 範例的測試 .xml 檔案。|  
  
## <a name="configure-biztalk-and-create-the-msmq-queue"></a>將 BizTalk 設定，並建立 MSMQ 佇列  
 請確定 Visual Studio、 Microsoft Message Queuing 與 BizTalk Server 安裝。  
  
#### <a name="to-configure-biztalk-server"></a>設定 BizTalk Server  
  
1.  在 Visual Studio 中開啟**C:\Program Files\Microsoft BizTalk Server\<版本\>\SDK\Samples\AdaptersUsage\MSMQLarge\LargeMessages.sln**方案檔。  建立此範例。  
  
2.  建立**C:\Demo** BizTalk Server 將放置從 MSMQ 訊息目錄。  
  
3.  開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
4.  建立傳送埠將訊息寫入範例。  
  
    -   展開**BizTalk 群組**，依序展開**應用程式**，依序展開**BizTalk Application 1**，以滑鼠右鍵按一下**傳送埠**，按一下**新增**，然後按一下 **靜態單向傳送埠**。  
  
5.  在**靜態單向傳送埠屬性**對話方塊方塊中，設定之連接埠名稱**MySendPort**。  
  
6.  將傳輸類型設定為**檔案**。  
  
7.  按一下**設定** 按鈕以開啟**File 傳輸屬性**表單。 輸入**C:\Demo**中**目的地資料夾**。 請確認主控件執行個體識別具有存取權 C:\Demo 資料夾。  
  
8.  請確認**檔案名稱**設 **%MessageID%.xml**。 按一下 **[確定]**。  
  
9. 按一下 **[篩選]**。  
  
    1.  設定**屬性**至**BTS。ReceivePortName**。  
  
    2.  設定**運算子**至 **=** 。  
  
    3.  設定**值**至**MyReceivePort**。  
  
    4.  按一下 **[確定]**。  
  
10. 建立接收埠以接受來自 MSMQ 訊息。  
  
    1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**接收埠**。  
  
    2.  按一下**新增**，然後按一下 **單向接收埠**。  
  
11. 在**接收埠屬性**對話方塊方塊中，設定之連接埠名稱**MyReceivePort**，然後按一下 **確定**。  
  
12. 建立範例的接收埠之後，您必須建立一個接收位置。  
  
    1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**接收位置**。  
  
    2.  按一下**新增**，然後按一下 **單向接收位置**。  
  
    3.  設定接收位置的名稱**MSMQReceiveLocation**。  
  
    4.  在**選取接收埠**對話方塊中，選取**MyReceivePort**。  
  
    5.  在**接收位置屬性** 對話方塊中，將**傳輸類型**至**MSMQ**。  
  
    6.  在**位址 (URI)** 區段中，按一下**設定**開啟**MSMQ 傳輸屬性**表單。 設定**佇列**至**localhost\private$ \test**。  
  
    7.  設定**交易式**至`True`，然後按一下 **確定**。  
  
13. 您必須讓連接埠和接收位置可供使用，透過[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
    1.  以滑鼠右鍵按一下**MySendPort**，然後按一下 **登錄**。  
  
    2.  以滑鼠右鍵按一下**MySendPort**，然後按一下 **啟動**。  
  
    3.  以滑鼠右鍵按一下**MSMQReceiveLocation**，然後按一下 **啟用**。  
  
#### <a name="to-create-the-msmq-queue-in-windows-server"></a>若要在 Windows Server 中建立 MSMQ 佇列
  
1.  按一下**啟動**，以滑鼠右鍵按一下**電腦**，然後按一下 **管理**。  
  
2.  展開**功能**節點。  
  
3.  展開**訊息佇列**節點。  
  
4.  以滑鼠右鍵按一下**私用佇列**節點中，按一下 **新增**，然後按一下 **私用佇列**。  
  
5.  在下**佇列名稱**，輸入**測試**。 請確認**交易式**選取核取方塊。  
  
6.  按一下 **[確定]**。  
  
#### <a name="to-create-the-msmq-queue-in-windows"></a>若要在 Windows 中建立 MSMQ 佇列 
  
1.  按一下**啟動**，以滑鼠右鍵按一下**電腦**，然後按一下 **管理**。  
  
2.  展開**服務和應用程式**，然後展開**訊息佇列**節點。  
  
    > [!NOTE]
    >  如果**訊息佇列**未安裝在電腦中，移至**控制台 > 程式 > 程式和功能**，然後選取**開啟或關閉 Windows 功能**。 檢查下的所有功能**Microsoft Message Queue (MSMQ) 伺服器**，然後按一下 **確定**。  
  
3.  以滑鼠右鍵按一下**私用佇列**節點中，按一下 **新增**，然後按一下 **私用佇列**。  
  
4.  在下**佇列名稱**，輸入**測試**。 請確認**交易式**選取核取方塊。  
  
5.  按一下 **[確定]**。  
  
## <a name="creating-a-test-file-and-running-the-sample"></a>建立測試檔案並執行範例  
  
#### <a name="to-create-a-large-test-file"></a>若要建立大型的測試檔案  
  
1.  在 Visual Studio 中開啟方案**C:\Program Files\Microsoft BizTalk Server\<版本\>\SDK\Samples\AdaptersUsage\MSMQLarge\XMLCreator\XMLCreator.sln**。  
  
2.  建置並執行專案。  
  
3.  在下**XML 主體**，型別**這是測試訊息**。  
  
4.  在下**的次數来複製的 XML 主體 #**，型別`250000`。  
  
5.  在下**XML 檔案位置**，型別`C:\Program Files\Microsoft BizTalk Server <version>\SDK\Samples\AdaptersUsage\MSMQLarge\LargeFile.xml`。  
  
6.  按一下**建立 XML**，然後按一下 **確定**。  
  
#### <a name="to-run-the-sample"></a>執行範例  
  
1.  開啟命令提示字元，然後將目錄切換至**C:\Program Files\Microsoft BizTalk Server\<版本\>\SDK\Samples\AdaptersUsage\MSMQLarge\SendLargeMessage\bin\debug**。  
  
2.  在命令提示字元中，執行**SendLargeMessage.exe**。 SendLargeMessage 可執行檔接受兩個變數，第一個是 MSMQ 佇列的位置，第二個是要傳送的.xml 檔案的位置：  
  
    ```  
    DIRECT=OS:localhost\private$\Test  "C:\Program Files\Microsoft BizTalk Server <version>\SDK\Samples\AdaptersUsage\MSMQLarge\LargeFile.xml"  
    ```  
  
3.  確認已在 BizTalk Server 電腦上建立相同大小的檔案**C:\Demo**目錄。 這是您在 MySendPort 傳送埠中找到的目錄。  
  
## <a name="comments"></a>註解  
 SendLargeMessage.exe 參考**LargeMessages**又參考 BizTalk 訊息佇列大型訊息延伸模組 (MQRTLarge.dll) API 的 API。 訊息佇列大型訊息延伸模組 API 是原生訊息佇列的附加元件可讓處理大於 4 MB 限制的原生訊息佇列的訊息。  
  
 這個範例會使用**MQSendLargeMessage** API 並公開 API 的.NET framework 使用**LargeMessages**應用程式開發介面。  
  
## <a name="see-also"></a>請參閱  
 [BizTalk 訊息佇列大型訊息延伸模組](../core/biztalk-message-queuing-large-message-extension.md)   
 [配接器範例 - 用法](../core/adapter-samples-usage.md)