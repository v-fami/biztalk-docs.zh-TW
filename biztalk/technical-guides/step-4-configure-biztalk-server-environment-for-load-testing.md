---
title: 步驟 4： 設定負載測試的 BizTalk Server 環境 |Microsoft 文件
ms.custom: ''
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5f336c5f-5a18-493d-8fc0-a8a475ab47b3
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf2e8b2b3751f31401ef0353944be0bdad3cbb2b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25976804"
---
# <a name="step-4-configure-biztalk-server-environment-for-load-testing"></a>步驟 4： 設定負載測試 BizTalk Server 的環境
本主題提供資訊，以建立 BizTalk Server 接收位置，接收埠和傳送埠執行主題所述的範例程式碼所需[步驟 1： 建立單元測試加入至 BizTalk Server 提交的文件](~/technical-guides/step-1-create-a-unit-test-to-submit-documents-to-biztalk-server.md)和[步驟 3： 建立負載測試，以便同時執行多個單元測試](~/technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md)。  
  
## <a name="configure-biztalk-server-environment-for-load-tests"></a>設定 BizTalk Server 環境的負載測試  
 本主題中所述[步驟 3： 建立負載測試來執行多個單元測試同時](~/technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md)，負載測試**BTS_Messaging_Step**設為執行單元測試**BTSMessaging**和**BTSMessaging2**。 接著，這些單元測試載入一份郵件 C:\Projects\LoadTest\BTSLoad\TestMessages\TestXmlDocument.xml 並傳送至端點**BTSMessagingEP**和**BTSMessagingEP2**中所定義專案的應用程式組態檔 (app.config) 的下列區段：  
  
 \<\!-BTSMessagingEP-\>\<端點 address="net.tcp://*BizTalk Server 電腦*: 8123/btsloadtest 」 繫結 ="netTcpBinding"bindingConfiguration ="netTcpBinding"合約 ="System.ServiceModel.Channels.IRequestChannel 「 名稱 ="BTSMessagingEP"/\>\<端點 address="net.tcp://*BizTalk Server 電腦*: 8123/btsloadtest 」 繫結 ="netTcpBinding"bindingConfiguration ="netTcpBinding"contract="System.ServiceModel.Channels.IRequestChannel 「 名稱 ="BTSMessagingEP2"/                  \>  
  
> [!NOTE]
>  如前文所述， *BizTalk Server 電腦*是實際的 BizTalk Server 電腦名稱，或確定 BizTalk Server 電腦都設定為網路負載平衡 (NLB) 叢集; 成員的案例中的預留位置*BizTalk Server 電腦*是的名稱或位址對應的 NLB 虛擬伺服器的預留位置。  
  
 基於此範例中，兩部 BizTalk Server 電腦所使用，BizTalk Server Messagebox 資料庫已經在遠端 SQL Server 電腦上。  
  
### <a name="create-biztalk-server-send-and-receive-hosts"></a>建立 BizTalk Server 傳送和接收主控件  
 依照主題中的 BizTalk Server 文件[如何建立新的主控件](http://go.microsoft.com/fwlink/?LinkId=208595)(http://go.microsoft.com/fwlink/?LinkId=208595) 來建立 BizTalk Server 「 傳送 」 主控件的傳送埠和傳送配接器處理常式。 設定主機具有下列屬性：  
  
|屬性|值|  
|--------------|-----------|  
|名稱|TxHost|  
|類型|內含式|  
|允許主控件追蹤|請確認不勾選此方塊。|  
|信任的驗證|請確認不勾選此方塊。|  
|僅限 32 位元|請確認不勾選此方塊。|  
|將此預設主機群組中|請確認不勾選此方塊。|  
|Windows 群組|Windows 群組，用來控制對此主機與關聯的主控件執行個體的存取。 建立的預設內含式主控件為視窗群組*\<電腦名稱\>* \BizTalk 應用程式使用者 （適用於單一伺服器安裝 BizTalk Server） 或 *\<網域名稱\>* \BizTalk 應用程式使用者 （適用於 BizTalk Server 安裝，需要使用網域群組的多個伺服器）。 **注意：***\<電腦名稱\>* 和*\<網域名稱\>* 預留位置的實際電腦名稱或網域名稱建立群組時使用。   <br /><br /> 如果此主機會建立一個新的群組，則它必須 > 主題所述的權限[主機群組](http://go.microsoft.com/fwlink/?LinkId=208803)(http://go.microsoft.com/fwlink/?LinkId=208803) 中的 BizTalk Server 文件。|  
  
 重複執行建立 「 傳送 」 主控件建立 「 接收 」 主控件時，您會遵循的步驟。 設定 「 接收 」 主控件具有下列屬性值：  
  
|屬性|值|  
|--------------|-----------|  
|名稱|RxHost|  
|類型|內含式|  
|允許主控件追蹤|請確認不勾選此方塊。|  
|信任的驗證|請確認不勾選此方塊。|  
|僅限 32 位元|請確認不勾選此方塊。|  
|將此預設主機群組中|請確認不勾選此方塊。|  
|Windows 群組|Windows 群組，用來控制對此主機與關聯的主控件執行個體的存取。 建立的預設內含式主控件為視窗群組*\<電腦名稱\>* \BizTalk 應用程式使用者 （適用於單一伺服器安裝 BizTalk Server） 或 *\<網域名稱\>* \BizTalk 應用程式使用者 （適用於 BizTalk Server 安裝，需要使用網域群組的多個伺服器）。 **注意：***\<電腦名稱\>* 和*\<網域名稱\>* 預留位置的實際電腦名稱或網域名稱建立群組時使用。   <br /><br /> 如果此主機會建立一個新的群組，則它必須 > 主題所述的權限[主機群組](http://go.microsoft.com/fwlink/?LinkId=208803)(http://go.microsoft.com/fwlink/?LinkId=208803) 中的 BizTalk Server 文件。|  
  
### <a name="create-instances-of-the-biztalk-server-send-and-receive-hosts"></a>建立執行個體的 BizTalk Server 傳送和接收主控件  
 依照主題中的 BizTalk Server 文件[如何新增主控件執行個體](http://go.microsoft.com/fwlink/?LinkId=208596)(http://go.microsoft.com/fwlink/?LinkId=208596) 建立和啟動 BizTalk Server 「 傳送 」 主控件執行個體。 設定 BizTalk Server 群組中每個 BizTalk Server 上執行，並且具有下列屬性值設定每個主控件執行個體的 「 傳送 」 主控件執行個體：  
  
|屬性|值|  
|--------------|-----------|  
|**主機名稱**|選取**TxHost**旁的下拉式清單**主機名稱**。|  
|**Server**|選取 BizTalk Server 會執行此主控件執行個體的下拉式清單旁**伺服器**。|  
|**登入**|1.按一下**設定** 按鈕以顯示**登入認證** 對話方塊。<br />2.在**登入認證**對話方塊中指定的屬性中輸入下列值：<br />     **屬性**<br />     **登入**： 此 BizTalk Server 主控件相關聯的 Windows 群組成員的使用者帳戶的名稱。<br />     **密碼**： 在指定的使用者帳戶的密碼**登入**文字方塊。<br />3.按一下**確定**關閉**登入認證** 對話方塊。|  
|**停用主控件執行個體無法啟動。**|請確認不勾選此方塊。|  
  
 後建立主控件執行個體，以滑鼠右鍵按一下主控件執行個體，然後選取**啟動**從內容功能表。  
  
 重複執行建立 「 傳送 」 主控件執行個體，若要建立 「 接收 」 主控件執行個體時，您遵循的步驟。 設定 BizTalk Server 群組中每個 BizTalk Server 上執行，並且具有下列屬性值設定每個主控件執行個體的 「 接收 」 主控件執行個體：  
  
|屬性|值|  
|--------------|-----------|  
|主機名稱|選取**RxHost**旁的下拉式清單**主機名稱**。|  
|Server|選取 BizTalk Server 會執行此主控件執行個體的下拉式清單旁**伺服器**。|  
|登入|1.按一下**設定** 按鈕以顯示**登入認證** 對話方塊。<br />2.在**登入認證**對話方塊中指定的屬性中輸入下列值：<br />     **屬性**<br />     **登入**： 此 BizTalk Server 主控件相關聯的 Windows 群組成員的使用者帳戶的名稱。<br />     **密碼**： 在指定的使用者帳戶的密碼**登入**文字方塊。<br />3.按一下**確定**關閉登入認證 對話方塊。|  
|停止啟動主控件執行個體|請確認不勾選此方塊。|  
  
 後建立主控件執行個體，以滑鼠右鍵按一下主控件執行個體，然後選取**啟動**從內容功能表。  
  
### <a name="create-a-biztalk-server-receive-port"></a>建立 BizTalk Server 接收埠  
 遵循本主題中的步驟[如何建立接收埠](http://go.microsoft.com/fwlink/?LinkID=154843)(http://go.microsoft.com/fwlink/?LinkID=154843) 若要建立單向接收埠的 BizTalk Server 文件中。 建立接收埠時，保留所有屬性的預設值，但下表所述：  
  
|屬性|值|  
|--------------|-----------|  
|General\Name|BTSLoadTestMessaging.OneWay.ReceivePort|  
|General\Port 類型|單向|  
|General\Authentication|無驗證|  
|General\Enable 路由失敗訊息|請確認不勾選此方塊。|  
|General\Description|保留空白|  
|輸入對應|無|  
|追蹤|確定未核取所有的方塊。|  
|接收位置|按一下**新增**，這樣就會顯示**接收位置屬性**應在下一節中所述設定 對話方塊**建立 BizTalk Server 接收位置**.|  
  
### <a name="create-a-biztalk-server-receive-location"></a>建立 BizTalk Server 接收位置  
 在**接收位置屬性**對話方塊顯示建立 BizTalk Server 接收連接埠時，套用指定的屬性值：  
  
|屬性|值|  
|--------------|-----------|  
|名稱：|BTSLoadTest.Messaging.OneWay.WCF Customer.ReceiveLocation|  
|接收處理常式：|RxHost|  
|接收管線︰|PassThruReceive|  
|描述：|將此留白|  
|類型：|選取**Wcf-custom**從下拉式清單，然後按一下**設定** 按鈕，這會顯示**Wcf-custom 傳輸屬性**應該 對話方塊下一節所述設定**設定 Wcf-custom 接收傳輸**。|  
  
### <a name="configure-the-wcf-custom-receive-transport"></a>設定 Wcf-custom 接收傳輸  
 在**Wcf-custom 傳輸屬性**對話方塊顯示建立的 BizTalk Server 接收位置時，所有屬性都保留預設值以外，如下表所述：  
  
|屬性|值|  
|--------------|-----------|  
|General\Address (URI)|net.tcp: //localhost: 8123/btsloadtest|  
|Binding\Binding 類型|netTcpbinding|  
|Binding\NetTcpBindingElement\listenBacklog|400|  
|Binding\NetTcpBindingElement\maxConnections|400|  
|Binding\Security\NetTcpSecurityElement\mode|無|  
|Behavior\ServiceBehavior\serviceThrottling\ServiceThrottlingElement**附註：** 將 serviceThrottling 行為新增至清單的行為，以滑鼠右鍵按一下 ServiceBehavior 按一下**加入擴充**，選取**serviceThrottling**從清單中的行為延伸模組，然後按一下**確定**。|設定**ServiceThrottlingElement**屬性為下列值：<br /><br /> -   **maxConcurrentCalls** 400<br />-   **maxConcurrentInstances** 400<br />-   **maxConcurrentSessions** 400|  
|Behavior\ServiceBehavior\serviceDebug\ServiceDebugElement**附註：** 加入 serviceDebug 行為的行為，以滑鼠右鍵按一下 ServiceBehavior 清單按一下**加入擴充**，選取**serviceDebug**行為延伸模組，然後再按一下清單中**確定**。|保留的清單**ServiceDebugElement**屬性保留為預設值 （空白） 除了下列的屬性，來變更為 True 的值：<br /><br /> -   **httpHelpPageEnabled** ，則為 True<br />-   **httpsHelpPageEnabled** ，則為 True<br />-   **includeExceptionDetailInFaults** ，則為 True|  
  
 按一下**確定**來關閉 Wcf-custom 傳輸屬性 對話方塊，然後按一下**確定** 以關閉 接收位置屬性 對話方塊。  
  
### <a name="create-a-biztalk-server-send-port"></a>建立 BizTalk Server 傳送埠  
 遵循本主題中的步驟[如何建立傳送埠](http://go.microsoft.com/fwlink/?LinkID=154845)(http://go.microsoft.com/fwlink/?LinkID=154845) 中建立的 BizTalk Server 文件**靜態單向**傳送埠。 建立傳送埠時，保留所有屬性的預設值，但下表所述：  
  
|屬性|值|  
|--------------|-----------|  
|General\Name|BTSLoadTest.Messaging.Send.WCF 自訂|  
|General\Send 處理常式|TxHost|  
|General\Send 管線|PassThruTransmit|  
|Filters\Name|BTS.ReceivePortName|  
|Filters\Operator|==|  
|Filters\Value|BTSLoadTest.Messaging.OneWay.ReceivePort|  
|由 Filters\Group|和**附註：** 篩選這些屬性會設定以正確的值，如果應該顯示為`BTS.ReceivePortName == BTSLoadTest.Messaging.OneWay.ReceivePort`b 中的 [傳送埠屬性] 對話方塊的 [篩選] 頁面底部所見ox。 因為套用此篩選之後，此傳送埠訂閱透過名為 BTSLoadTest.Messaging.OneWay.ReceivePort 接收埠的 BizTalk Server 收到任何訊息。|  
|追蹤|確定未核取所有的方塊。|  
|General\Type|選取**Wcf-custom**從下拉式清單，然後按一下**設定** 按鈕，這會顯示**Wcf-custom 傳輸屬性**應該 對話方塊下一節所述設定**設定 Wcf-custom 傳送傳輸**。|  
  
### <a name="configure-the-wcf-custom-send-transport"></a>設定 Wcf-custom 傳送傳輸  
 在**Wcf-custom 傳輸屬性**建立 BizTalk Server 傳送埠時顯示的對話方塊，請將所有屬性都保留預設值，但除外下, 表所述：  
  
|屬性|值|  
|--------------|-----------|  
|General\Address (URI)|net.tcp://*\<電腦名稱\>*: 2001年/TCP1**重要事項：***\<電腦名稱\>* 這是一個預留位置用來裝載 IndigoService.exe 實際電腦名稱，它被設計來取用 WCF 透過傳送的訊息。   因為 IndigoService.exe 需要極少的資源，所以通常完全可接受用於 BizTalk Server 群組資料庫的 SQL Server 電腦上執行 IndigoService.exe。 IndigoService.exe 屬於 BizTalk 基準精靈，將會位於[BizTalk 基準精靈](http://go.microsoft.com/fwlink/?LinkID=186347)(http://go.microsoft.com/fwlink/?LinkID=186347)。|  
|Binding\Binding 類型|**customBinding**|  
  
 如同大部分的 WCF 自訂繫結類型**customBinding**繫結型別會公開一些屬性，它應該設定為下列值：  
  
1.  在下**繫結**區段沒有**CustomBindingElement**屬性相關之**組態**> 一節。 保留的所有值的組態區段中**CustomBindingElement**屬性保留為預設值。  
  
2.  然後在**CustomBindingElement**以滑鼠右鍵按一下**textMessageEncoding**選取**移除延伸模組 (Del)**。 同樣地，以滑鼠右鍵按一下**httpTransport**選取**移除延伸模組 (Del)**。  
  
3.  現在以滑鼠右鍵按一下**CustomBindingElement**選取**加入擴充功能集**顯示**選取繫結元素延伸模組** 對話方塊。  
  
4.  選取**binaryMessageEncoding**按一下**確定**新增**binaryMessageEncoding**項目延伸。 重複步驟顯示**選取繫結元素延伸模組**對話方塊和捲軸向下可用的項目延伸的清單直到您看到**tcpTransport**項目延伸，選取**tcpTransport**按一下**確定**。  
  
5.  在下**CustomBindingElement**選取**tcpTransport**項目和組態區段中**tcpTransport**，保留所有屬性的預設值以外，做為下表所述：  
  
    |屬性|值|  
    |--------------|-----------|  
    |connectionBufferSize|2097152|  
    |maxBufferSize|2097152|  
    |maxPendingAccepts|400|  
    |maxPendingConnections|400|  
    |listenBacklog|400|  
    |maxBufferPoolSize|2097152|  
    |maxReceivedMessageSize|2097152|  
  
6.  在下**tcpTransport**項目選取**n**項目並保留預設值的所有屬性都值除了**maxOutboundConnectionsPerEndpoint**屬性，來變更值為 400。  
  
7.  按一下**確定**若要關閉 [Wcf-custom 傳輸屬性] 對話方塊，然後按一下 [ **[確定]** ] 以關閉 [BTSLoadTest.Messaging.Send.WCF 自訂-傳送埠屬性] 對話方塊。  
  
### <a name="configure-a-computer-to-consume-messages-sent-by-the-biztalk-server-send-port"></a>設定電腦以使用 BizTalk Server 傳送埠所傳送的訊息  
 如先前所述，IndigoService.exe 被設計來使用透過 WCF 傳送的訊息。 IndigoService.exe 屬於 BizTalk 基準精靈，將會位於[BizTalk 基準精靈](http://go.microsoft.com/fwlink/?LinkID=186347)(http://go.microsoft.com/fwlink/?LinkID=186347)。 若要設定和執行此範例的目的 IndigoService.exe 最簡單的方式是只需下載 BizTalk 基準精靈 zip 檔案，從[BizTalk 基準精靈下載頁面](http://go.microsoft.com/fwlink/?LinkID=209100)(http://go.microsoft.com/fwlink/?LinkID = 209100)，然後將解壓縮到您想要執行 IndigoService.exe 的電腦上下列 4 個檔案：  
  
1.  \IndigoService\bin\Release\IndigoService.exe  
  
2.  \IndigoService\bin\Release\IndigoService.exe.config  
  
3.  \IndigoService\bin\Release\Response.xml  
  
4.  \IndigoService\bin\Release\StartIndigoService.bat  
  
 然後啟動 IndigoService.exe StartIndigoService.bat 上按兩下。 IndigoService.exe 取用 IndigoService.exe.config 檔案中指定的端點傳送的訊息：  
  
 \<端點位址 ="net.tcp: //localhost: 2001年/TCP1 」 繫結 ="netTcpBinding"bindingConfiguration ="Binding1"name ="endpoint1"contract="IndigoService.IServiceTwoWaysVoidNonTransactional"/\>  
  
 這就是為什麼傳送連接埠設定位址的位址 (URI) 的 net.tcp://*\<電腦名稱\>*: 2001年/TCP1  
  
 因為 IndigoService.exe 需要極少的資源，所以通常完全可接受用於 BizTalk Server 資料庫的 SQL Server 電腦上執行 IndigoService.exe。  
  
### <a name="disable-tracking-and-throttling-for-the-biztalk-server-group"></a>停用追蹤和節流在 BizTalk Server 群組  
 若要判斷絕對最大持續輸送量的系統，這兩個訊息追蹤和節流應該停用開始負載測試之前。 這可以使用 BizTalk Server 管理主控台，依照下列步驟：  
  
1.  啟動 BizTalk Server 管理主控台。 按一下**啟動**，指向 **所有程式**，指向  **BizTalk Server 2010** ，然後按一下  **BizTalk Server 管理**。  
  
2.  在下**BizTalk Server 管理**、 選取您的 BizTalk 群組，如果有列出，或如果未列出，以滑鼠右鍵按一下**BizTalk Server 管理**，選取**連接至現有的群組**，輸入裝載 BizTalk 群組的 BizTalk Server 管理資料庫旁的 SQL Server 名稱**SQL Server 名稱：**，輸入的 BizTalk 群組的管理資料庫名稱旁邊**資料庫名稱：** ，然後按一下 **確定**。  
  
3.  以滑鼠右鍵按一下 [BizTalk 群組] 節點，然後選取**設定**顯示**BizTalk 設定儀表板**。  
  
4.  按一下以選取**主機**BizTalk 設定儀表板的左窗格中。  
  
5.  按一下下拉式清單旁**主機**選取其中一個會在效能測試期間使用的主機。  
  
6.  將內容保留其預設值以外，如下列表格中所述：  
  
    |屬性|值|  
    |--------------|-----------|  
    |**追蹤資料到 DTA DB General\Move**|如果已核取，請取消選取此方塊。|  
    |**僅限 General\32 位元**|如果已核取，請取消選取此方塊。|  
    |**General\Polling Intervals\Messaging**|設為 20000000 值|  
    |**General\Polling Intervals\Orchestrations**|設為 20000000 值|  
    |**資源型 Throttling\In 處理訊息**|設為值的 10000 倍|  
    |**資源型 Throttling\Internal 訊息佇列大小**|設為值的 10000 倍|  
    |**在 DB 中的資源型 Throttling\Message 計數**|設定為 0 的值|  
    |**虛擬的 資源型 Throttling\Memory Usage\Process**|設定為 0 的值|  
    |**根據速率的 Throttling\Publishing\Throttling 覆寫**|設定為不要節流|  
    |**根據速率的 Throttling\Delivery\Throttling 覆寫**|設定為不要節流|  
  
7.  重複步驟 6 中所述的效能測試期間將會使用每個主控件程序。  
  
8.  按一下以選取**主控件執行個體**BizTalk 設定儀表板的左窗格中。  
  
9. 按一下下拉式清單旁**主控件執行個體：** 選取其中一個用於效能測試的主控件執行個體。  
  
10. 屬性值保留為預設設定，除了變更 **.NET CLR 最大工作者執行緒**為**100**並變更**上最小.NET CLR 工作者執行緒**至值**25**。  
  
11. 重複步驟 10 期間的效能測試將會使用每個主控件執行個體中所述的程序。  
  
 即使停用追蹤和節流並不以任何方式代表要如何處理在生產案例中，因為這些作業會從效能觀點來看很合理停用它們了解，則為 true 最大持續因此高度耗費資源BizTalk Server 環境的輸送量 (MST)。 這可讓測試人員，清楚看到的調整，任何效能影響已套用至環境。 確實應該不會停用追蹤，而且如果您從一開始，您的 BizTalk Server 應用程式需要追蹤然後您應該啟用追蹤，無法讓引數。 也就是說，**致力應該要對停用節流基於效能測試**。 節流是防止 BizTalk Server 」 下降 「 由於過多的負載，在生產環境中非常有用。 不過，您不想節流啟用期間，如果在負載測試期間節流中的是否已盡力而為然後您必須判斷何種效能層級很難因為從效能觀點來看昂貴的效能測試程式BizTalk Server 應用程式可以實際達成的。 下一個主題說明如何執行步驟負載測試以推入超過 MST BizTalk Server 環境，並回到實際常數負載測試時，MST 再擴充。 如果已啟用節流設定，然後就會變成幾乎難以推超過 MST BizTalk 環境，讓您接著可能會發現 MST 是何種 true。