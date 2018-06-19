---
title: MQSCorrelationSetOrchestration （BizTalk Server 範例） |Microsoft 文件
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
- examples, messages
- messages, examples
- MQSeries adapters, examples
ms.assetid: fcda65d0-e3ec-4ead-978d-3904903b8762
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75ac63fe0fee593f927e854ce425ff7f631f9475
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25974980"
---
# <a name="mqscorrelationsetorchestration-biztalk-server-sample"></a>MQSCorrelationSetOrchestration (BizTalk Server 範例)
MQSCorrelationSetOrchestration 範例會示範如何使用 MQSeries 相互關聯識別項，將傳送至 MQSeries 佇列的相互關聯訊息送回到執行中的協調流程。 協調流程設定 MQSeries 相互關聯識別項和訊息使用的識別碼值**MQMD_CorrelId**和**MQMD_MsgID**屬性。 MQSeries 佇列管理員會將 MessageID 值複製到訊息的 CorrelationID 屬性。  
  
## <a name="prerequisites"></a>必要條件  
 此範例假設您已經在執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的相同伺服器上安裝 IBM WebSphere MQSeries。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 此範例會示範如何在傳送至 IBM WebSphere MQSeries Server 的訊息中，設定訊息識別項和相互關聯識別項。 這是將訊息相互關聯回執行中之協調流程執行個體的一種方法。 MQSeries 佇列管理員在收到訊息時，便會將 MessageID 值複製到訊息的 CorrelationID 屬性。 這個 CorrelationID (**MQMD_CorrelId**) 然後協調流程中使用 MQSeries 上的回應訊息與用來將訊息傳送至 MQSeries 的執行個體。  
  
## <a name="how-this-sample-is-designed-and-why"></a>此範例的設計方式和原因  
 這個範例所示範的實例中，將由協調流程處理的文件可以傳送至 MQSeries 佇列 (假設會進行其他處理)，並會傳回到執行中的協調流程。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 *\<範例路徑\>* \AdaptersUsage\MQSeriesAdapter\MQSCorrelationSetOrchestration  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|**檔案**|**說明**|  
|--------------|---------------------|  
|**MQSCorrelationSetOrchestration.btproj，**<br /><br /> **MQSCorrelationSetOrchestration.sln**|應用程式的專案和方案檔。|  
|**MQSCorrelationSetOrchestration.odx**|應用程式的協調流程。|  
|**MQSCorrelationSetOrchestration.snk**|強式命名金鑰檔。|  
|**Setup.bat**|建置並初始化此範例。|  
  
## <a name="how-to-use-this-sample"></a>如何使用此範例  
 如果需要將訊息傳送至 MQSeries Server 以做為整體工作流程中的一個步驟，請併入此範例中所採用的邏輯。  
  
### <a name="to-create-the-mqseries-queue-through-the-websphere-mq-explorer"></a>若要透過 WebSphere MQ Explorer 建立 MQSeries 佇列  
  
1.  按一下**啟動**，指向 **程式**，指向  **IBM WebSphere MQ**，然後按一下  **WebSphere MQ Explorer**。  
  
2.  按兩下**佇列管理員**，然後按兩下預設佇列管理員。 預設佇列管理員通常會命名為**Qm_< < machine_name >** 其中*machine_name*是您的電腦名稱。  
  
3.  以滑鼠右鍵按一下**佇列**，指向 **新增**，然後按一下 **本機佇列**。  
  
4.  在**建立本機佇列**對話方塊中，於**佇列名稱**，輸入"MQCorrelation"，然後按**確定**。  
  
### <a name="to-create-the-receive-location-and-the-mqseries-queue"></a>建立接收位置與 MQSeries 佇列  
  
1.  開啟 BizTalk Server 管理主控台。  
  
2.  展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開所需的應用程式。  
  
3.  以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**。  
  
4.  在**單向接收埠屬性**對話方塊中，於**名稱**方塊中輸入"MQIn"，然後按一下**確定**。  
  
5.  在左窗格中，按一下 **接收位置**索引標籤，然後再按一下**新增**。  
  
6.  在**接收位置屬性**對話方塊中，於**名稱**方塊中，輸入"MQIn"。  
  
7.  在**傳輸類型**方塊中，選取**MQSeries**。  
  
8.  在**接收處理常式**方塊中，選取**BizTalkServerApplication**。  
  
9. 在**接收管線**方塊中，選取**Microsoft.BizTalk.DefaultPipelines.PassThruReceive**。  
  
10. 按一下**設定**。  
  
11. 在**MQSeries 傳輸屬性**對話方塊中，於**輪詢間隔**方塊中，輸入"10"。  
  
12. 在**佇列定義**方塊中，按一下省略符號 （...） 按鈕。  
  
13. 在**佇列定義**對話方塊中，於**伺服器名稱**方塊中，輸入您的電腦名稱。  
  
14. 在**佇列管理員**方塊中，選取預設佇列管理員。  
  
15. 在**佇列**方塊中輸入"MQCorrelation"，然後再按一下**匯出**。  
  
16. 在**匯出**對話方塊中，按一下**Create Queue**，然後按一下**確定**或**完成**直到結束所有對話方塊。  
  
### <a name="to-create-the-send-port-to-mqseries"></a>若要建立通往 MQSeries 的傳送埠  
  
1.  以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。  
  
2.  在**傳送埠屬性**對話方塊中，於**名稱**方塊中，輸入"MQOut"。  
  
3.  在**傳輸類型**方塊中，選取**MQSeries**。  
  
4.  在**傳送管線**方塊中，選取**Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**。  
  
5.  按一下**設定**。  
  
6.  在**MQSeries 傳輸屬性**對話方塊中，於**佇列定義**方塊中，按一下省略符號 （...） 按鈕。  
  
7.  在**佇列定義**對話方塊中，於**伺服器名稱**方塊中，輸入您的電腦名稱。  
  
8.  在**佇列管理員**方塊中，選取預設佇列管理員。  
  
9. 在**佇列**方塊中輸入"MQCorrelation"，然後再按一下**確定**。  
  
10. 按一下**確定**直到結束所有對話方塊。  
  
### <a name="to-enable-the-receive-location-and-start-the-send-port"></a>啟用接收位置和啟動傳送埠  
  
1.  在 BizTalk Server 管理主控台中，按一下 **接收埠**。  
  
2.  在詳細資料窗格中，以滑鼠右鍵按一下**MQIn**接收位置，然後按一下 **啟用**。  
  
3.  在詳細資料窗格中，以滑鼠右鍵按一下**MQOut**傳送連接埠，然後按一下**開始。**  
  
### <a name="to-create-the-folders-used-by-the-application"></a>若要建立應用程式使用的資料夾  
  
1.  在您**c:\\** 磁碟機，請建立名為"temp"如果不存在的資料夾。  
  
2.  在下**C:\temp**目錄中，建立名為"Pickup"和"dropit 的資料夾"的資料夾。  
  
### <a name="building-and-deploying-this-sample"></a>建置和部署此範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     `<Samples Path>\AdaptersUsage\MQSeriesAdapter\MQSCorrelationSetOrchestration`  
  
2.  執行檔案 Setup.bat，這會執行下列動作：  
  
    1.  為專案建立強式名稱金鑰。  
  
    2.  編譯和部署協調流程專案。  
  
    3.  使用 FILE 配接器建立傳送埠和接收埠。  
  
### <a name="bind-and-start-the-orchestration"></a>繫結並啟動協調流程  
  
1.  在 BizTalk Server 管理主控台中，展開 **協調流程**資料夾。  
  
2.  在詳細資料窗格中，以滑鼠右鍵按一下**MQSCorrelationSetOrchestration**協調流程，然後再按一下**繫結**。  
  
3.  將協調流程連接埠繫結至下列傳送埠和接收位置：  
  
    |**協調流程連接埠**|**傳送埠 / 接收位置**|  
    |----------------------------|--------------------------------------------|  
    |FileReceivePort|MQSCorrelationSetOrchestration.FileReceivePort|  
    |MQSeriesResponseReceivePort|MQIn|  
    |MQSeriesRequestSendPort|MQOut|  
    |FileSendPort|MQSCorrelationSetOrchestration.FileSendPort|  
  
4.  按一下**主機**。  
  
5.  在**主機**方塊中，選取**BizTalkServerApplication**，按一下**確定**。  
  
6.  在**傳送埠**，以滑鼠右鍵按一下 **[mqscorrelationsetorchestration.filesendport]**，然後選取**啟動**。  
  
7.  在**接收位置**，以滑鼠右鍵按一下**mqscorrelationsetorchestration.filereceiveport** ，然後選取 **啟用**。  
  
8.  以滑鼠右鍵按一下協調流程，然後按一下**啟動**。  
  
    > [!NOTE]
    >  啟動協調流程也會自動登錄協調流程。  
  
### <a name="to-test-the-application"></a>若要測試應用程式  
  
1.  將放入檔案**C:\Temp\Pickup**資料夾。  
  
2.  查看中的檔案**C:\Temp\Dropit**資料夾。  
  
    > [!NOTE]
    >  如果您停用**MQIn**接收位置，您可以檢查 WebSphere MQ Explorer 中的訊息，並查看所設定的訊息和相互關聯識別項。 若要這樣做，請啟動**WebSphere MQ Explorer**並檢查訊息置於**MQCorrelation**佇列。 訊息和相互關聯識別碼會顯示在**識別碼** 索引標籤**Message properties**  對話方塊。  
  
    > [!NOTE]
    >  在實際生產實例中，您會為每個傳送給 MQSeries 佇列的訊息指派唯一識別碼。 這可以藉由修改協調流程中的 [運算式] 圖形來完成。 請變更下面幾行，將這些屬性設定為唯一的 24 位元組識別碼：  
    >   
    >  MQSeriesRequestSendMessageModified(MQSeries.MQMD_MsgId) = "111213141516171819202122232425262728293031323334";  
    >   
    >  MQSeriesRequestSendMessageModified(MQSeries.MQMD_CorrelId) = "111213141516171819202122232425262728293031323334";  
    >   
    >  如果您想要設定唯一的 24 位元組識別碼，如這些屬性，請參閱 > 一節**來建立唯一的 24 位元組識別碼傳送至 MQSeries 的訊息**。  
  
### <a name="to-create-a-unique-24-byte-id-for-messages-sent-to-mqseries"></a>若要為傳送至 MQSeries 的訊息建立唯一的 24 位元組識別碼  
  
1.  在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中建立新的 C# 類別庫專案。  
  
2.  將下列程式碼貼到該類別的 .cs 檔案中：  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Security.Cryptography;  
  
    namespace MQId  
    {[Serializable]  
        public class GetId  
        {  
            RNGCryptoServiceProvider randomCryptoString = new RNGCryptoServiceProvider();  
  
            public string getGuidstr()  
            {  
                byte[] newGuid = GetRandomData(24);  
                return ConvertToHex(newGuid);  
            }  
  
            private byte[] GetRandomData(int keySize)  
            {  
                byte[] randomData = new byte[keySize];  
                randomCryptoString.GetBytes(randomData);  
                return randomData;  
            }  
  
            private string ConvertToHex(byte[] key)  
            {  
                StringBuilder hexString = new StringBuilder();  
                for (int i = 0; i < key.Length; ++i)  
                {  
                    hexString.Append(String.Format("{0:X2}", key[i]));  
                }  
                return hexString.ToString();  
            }  
        }  
    }  
    ```  
  
3.  指定**預設命名空間**的**MQId**和**組件名稱**的**GetId**的專案屬性**應用程式**頁面。  
  
4.  指定強式名稱金鑰檔簽署組件的專案屬性**簽署**頁面上，然後建置專案。  
  
5.  若要編譯的組件載入至 GAC 中使用全域組件快取工具 (gacutil.exe) (gacutil /i \<*的已編譯的 dll 檔案名稱*\>)。  
  
6.  在此範例的 BizTalk 專案中新增 GetId 組件的參考。  
  
7.  將兩個變數新增至此範例中所使用的協調流程：  
  
    |變數名稱 (識別項)|類型|  
    |----------------------------------|----------|  
    |GetId|MQId.GetId|  
    |strGuid|System.String|  
  
8.  將下列程式碼貼到此範例的協調流程中所使用的運算式圖形，此識別碼應覆寫現有的程式碼：  
  
    ```  
    GetId = new MQId.GetId();  
    strGuid = GetId.getGuidstr();  
    MQSeriesRequestSendMessageModified = MQSeriesRequestSendMessage;  
    MQSeriesRequestSendMessageModified(MQSeries.MQMD_MsgId) = strGuid;  
    MQSeriesRequestSendMessageModified(MQSeries.MQMD_CorrelId) = strGuid;  
    ```  
  
9. 在「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台」中停止並移除協調流程 (如果已部署的話)。 然後請依照下列各節中的步驟**建置和部署此範例**，**繫結並啟動協調流程**和**測試應用程式**。  
  
    > [!NOTE]
    >  使用此方法為傳送至 MQSeries 的訊息建立唯一的 24 位元組識別碼，並無法 100% 保證所有傳送的訊息都會有唯一的識別碼，而只能說訊息識別碼重複的可能性會很低。 如果企業需要 100% 保證沒有重複的訊息識別碼，您需要採用不同的自訂程式碼來確保此功能。  
  
## <a name="classes-or-methods-used-in-this-sample"></a>在此範例中使用的類別或方法  
 此範例沒有明確使用任何類別或方法。  
  
## <a name="see-also"></a>請參閱  
 [使用要求-回覆相互關聯訊息](../core/correlating-messages-using-request-reply.md)   
 [MQSeries 配接器範例](../core/mqseries-adapter-samples.md)