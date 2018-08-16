---
title: 步驟 4： 設定 BizTalk Server 環境的負載測試 |Microsoft Docs
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
ms.openlocfilehash: cf3ab4c913a55be391d1e92522c257c4cd82d272
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990351"
---
# <a name="step-4-configure-biztalk-server-environment-for-load-testing"></a>步驟 4： 設定 BizTalk Server 環境的負載測試
本主題提供資訊，以建立 BizTalk Server 接收位置，接收埠和傳送埠，才能執行主題所述的程式碼範例[步驟 1： 建立單元測試，提交至 BizTalk Server 的文件](~/technical-guides/step-1-create-a-unit-test-to-submit-documents-to-biztalk-server.md)並[步驟 3： 建立負載測試，以便同時執行多個單元測試](~/technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md)。  

## <a name="configure-biztalk-server-environment-for-load-tests"></a>設定 BizTalk Server 環境的負載測試  
 本主題中所述[步驟 3： 建立負載測試來執行多個單元測試同時](~/technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md)，在負載測試**BTS_Messaging_Step**設定為執行單元測試**BTSMessaging**並**BTSMessaging2**。 這些單元測試的載入一份訊息 C:\Projects\LoadTest\BTSLoad\TestMessages\TestXmlDocument.xml 依次，並將它傳送至的端點**BTSMessagingEP**並**BTSMessagingEP2**中所定義專案的應用程式組態檔 (app.config) 的下一節：  

 \<\!-BTSMessagingEP-\>\<端點 address="net.tcp://*BizTalk Server 電腦*: 8123/btsloadtest 」 繫結 ="netTcpBinding"bindingConfiguration ="netTcpBinding"合約 ="System.ServiceModel.Channels.IRequestChannel 「 名稱 ="BTSMessagingEP"/\>\<端點 address="net.tcp://*BizTalk Server 電腦*: 8123/btsloadtest 」 繫結 ="netTcpBinding"bindingConfiguration ="netTcpBinding"contract="System.ServiceModel.Channels.IRequestChannel 「 名稱 ="BTSMessagingEP2"/                  \>  

> [!NOTE]
>  如前文所述， *BizTalk Server 電腦*是實際的 BizTalk Server 電腦名稱，或在案例中，BizTalk Server 電腦設定為的網路負載平衡 (NLB) 叢集; 成員的預留位置*BizTalk Server 電腦*是預留位置的名稱或對應的 NLB 虛擬伺服器的位址。  

 基於此範例的詳細資訊，使用兩部 BizTalk Server 電腦，並已在遠端 SQL Server 電腦上的 BizTalk Server Messagebox 資料庫。  

### <a name="create-biztalk-server-send-and-receive-hosts"></a>建立 BizTalk Server 傳送和接收主控件  
 請依照下列 BizTalk Server 文件主題中的步驟[如何建立新的主控](http://go.microsoft.com/fwlink/?LinkId=208595)(http://go.microsoft.com/fwlink/?LinkId=208595)建立 BizTalk Server 「 傳送 」 主控件的傳送埠和傳送配接器處理常式。 設定主應用程式具有下列屬性：  

|屬性|值|  
|--------------|-----------|  
|名稱|TxHost|  
|類型|內含式|  
|允許主控件追蹤|確定不會核取此方塊。|  
|信任的驗證|確定不會核取此方塊。|  
|僅限 32 位元|確定不會核取此方塊。|  
|將此預設主機群組中|確定不會核取此方塊。|  
|Windows 群組|用來控制對此主控件和相關聯的主控件執行個體的 Windows 群組。 建立的預設內含式主控件名稱為 視窗群組*\<電腦名稱\>* \BizTalk 應用程式使用者 （適用於單一伺服器安裝 BizTalk Server） 或 *\<網域名稱\>* \BizTalk 應用程式使用者 （適用於多部伺服器需要使用網域群組的 BizTalk Server 安裝）。 **注意︰***\<電腦名稱\>* 並*\<網域名稱\>* 都是實際的電腦名稱或使用的網域名稱的預留位置當已建立的群組。   <br /><br /> 如果此主機會建立一個新的群組，則它必須具有主題所述的權限[主機群組](http://go.microsoft.com/fwlink/?LinkId=208803)(http://go.microsoft.com/fwlink/?LinkId=208803) BizTalk Server 文件。|  

 重複執行建立 「 傳送 」 主控件，來建立 「 接收 」 主控件時遵循的步驟。 使用下列屬性值來設定 「 接收 」 主控件：  

|屬性|值|  
|--------------|-----------|  
|名稱|RxHost|  
|類型|內含式|  
|允許主控件追蹤|確定不會核取此方塊。|  
|信任的驗證|確定不會核取此方塊。|  
|僅限 32 位元|確定不會核取此方塊。|  
|將此預設主機群組中|確定不會核取此方塊。|  
|Windows 群組|用來控制對此主控件和相關聯的主控件執行個體的 Windows 群組。 建立的預設內含式主控件名稱為 視窗群組*\<電腦名稱\>* \BizTalk 應用程式使用者 （適用於單一伺服器安裝 BizTalk Server） 或 *\<網域名稱\>* \BizTalk 應用程式使用者 （適用於多部伺服器需要使用網域群組的 BizTalk Server 安裝）。 **注意︰***\<電腦名稱\>* 並*\<網域名稱\>* 都是實際的電腦名稱或使用的網域名稱的預留位置當已建立的群組。   <br /><br /> 如果此主機會建立一個新的群組，則它必須具有主題所述的權限[主機群組](http://go.microsoft.com/fwlink/?LinkId=208803)(http://go.microsoft.com/fwlink/?LinkId=208803) BizTalk Server 文件。|  

### <a name="create-instances-of-the-biztalk-server-send-and-receive-hosts"></a>建立執行個體的 BizTalk Server 傳送和接收主控件  
 請依照下列 BizTalk Server 文件主題中的步驟[如何新增主控件執行個體](http://go.microsoft.com/fwlink/?LinkId=208596)(http://go.microsoft.com/fwlink/?LinkId=208596)建立和啟動 BizTalk Server 「 傳送 」 主控件執行個體。 設定 BizTalk Server 群組中每個 BizTalk Server 上執行，並使用下列屬性值來設定每個主控件執行個體的 「 傳送 」 主控件執行個體：  

|屬性|值|  
|--------------|-----------|  
|**主機名稱**|選取  **TxHost**下拉式清單中下一步**主機名稱**。|  
|**Server**|選取 BizTalk Server 會執行此主控件執行個體的下拉式清單旁**Server**。|  
|**登入**|1.按一下 **設定** 按鈕以顯示**登入認證** 對話方塊。<br />2.在 [**登入認證**] 對話方塊中指定屬性中輸入下列值：<br />     **屬性**<br />     **登入**： 此 BizTalk Server 主控件相關聯的 Windows 群組成員的使用者帳戶的名稱。<br />     **密碼**： 在指定的使用者帳戶的密碼**登入**文字方塊中。<br />3.按一下 [ **[確定]** 以關閉**登入認證**] 對話方塊。|  
|**停用主控件執行個體無法啟動。**|確定不會核取此方塊。|  

 後建立主控件執行個體，以滑鼠右鍵按一下主控件執行個體，然後選取**啟動**從內容功能表。  

 重複執行建立 「 傳送 」 主控件執行個體，來建立 「 接收 」 主控件執行個體時遵循的步驟。 設定 BizTalk Server 群組中每個 BizTalk Server 上執行，並使用下列屬性值來設定每個主控件執行個體的 「 接收 」 主控件執行個體：  

|屬性|值|  
|--------------|-----------|  
|主機名稱|選取  **RxHost**下拉式清單中下一步**主機名稱**。|  
|[伺服器]|選取 BizTalk Server 會執行此主控件執行個體的下拉式清單旁**Server**。|  
|登入|1.按一下 **設定** 按鈕以顯示**登入認證** 對話方塊。<br />2.在 [**登入認證**] 對話方塊中指定屬性中輸入下列值：<br />     **屬性**<br />     **登入**： 此 BizTalk Server 主控件相關聯的 Windows 群組成員的使用者帳戶的名稱。<br />     **密碼**： 在指定的使用者帳戶的密碼**登入**文字方塊中。<br />3.按一下 **確定**以關閉 登入認證 對話方塊。|  
|停止啟動主控件執行個體|確定不會核取此方塊。|  

 後建立主控件執行個體，以滑鼠右鍵按一下主控件執行個體，然後選取**啟動**從內容功能表。  

### <a name="create-a-biztalk-server-receive-port"></a>建立 BizTalk Server 接收埠  
 請依照下列主題中的步驟[如何建立接收埠](http://go.microsoft.com/fwlink/?LinkID=154843)(http://go.microsoft.com/fwlink/?LinkID=154843)建立單向接收埠的 BizTalk Server 文件中。 建立接收埠時，保留所有屬性的預設值，除非下表所述：  

|屬性|值|  
|--------------|-----------|  
|General\Name|BTSLoadTestMessaging.OneWay.ReceivePort|  
|General\Port 類型|單向|  
|General\Authentication|無驗證|  
|General\Enable 路由失敗訊息|確定不會核取此方塊。|  
|General\Description|保留空白|  
|輸入對應|無|  
|追蹤|確定不會核取所有方塊。|  
|接收位置|按一下 **的新**，這會顯示**接收位置屬性**對話方塊應該在下一節所述設定**建立 BizTalk Server 接收位置**.|  

### <a name="create-a-biztalk-server-receive-location"></a>建立 BizTalk Server 接收位置  
 在 **接收位置屬性**對話方塊顯示在建立 BizTalk Server 接收連接埠時，套用指定的屬性值：  

|屬性|值|  
|--------------|-----------|  
|名稱：|BTSLoadTest.Messaging.OneWay.WCF Customer.ReceiveLocation|  
|接收處理常式：|RxHost|  
|接收管線︰|PassThruReceive|  
|描述：|將此保留空白|  
|類型：|選取 [ **Wcf-custom**從下拉式清單，然後按一下**設定**] 按鈕，這會顯示**Wcf-custom 傳輸屬性**對話方塊中，這應該是下一節所述設定**來設定 Wcf-custom 接收傳輸**。|  

### <a name="configure-the-wcf-custom-receive-transport"></a>設定 WCF 自訂接收傳輸  
 在  **Wcf-custom 傳輸屬性**對話方塊顯示在建立 BizTalk Server 接收位置時，所有屬性都保留預設值以外下, 表所述：  

|屬性|值|  
|--------------|-----------|  
|General\Address (URI)|net.tcp: //localhost: 8123/btsloadtest|  
|Binding\Binding 類型|netTcpbinding|  
|Binding\NetTcpBindingElement\listenBacklog|400|  
|Binding\NetTcpBindingElement\maxConnections|400|  
|Binding\Security\NetTcpSecurityElement\mode|無|  
|Behavior\ServiceBehavior\serviceThrottling\ServiceThrottlingElement**附註：** 將 serviceThrottling 行為新增至行為，以滑鼠右鍵按一下 ServiceBehavior 的清單中，按一下**加入擴充**，選取**serviceThrottling**從清單中的行為延伸模組，然後按一下 **[確定]**。|設定**ServiceThrottlingElement**屬性為下列值：<br /><br /> -   **maxConcurrentCalls** 400<br />-   **maxConcurrentInstances** 400<br />-   **maxConcurrentSessions** 400|  
|Behavior\ServiceBehavior\serviceDebug\ServiceDebugElement**附註：** 將 serviceDebug 行為新增至行為，以滑鼠右鍵按一下 ServiceBehavior 的清單中，按一下**加入延伸模組**，選取**serviceDebug**從清單中的行為延伸模組，然後再按一下**確定**。|保留的清單**ServiceDebugElement**屬性的預設值 （空白） 除了下列的屬性，來變更為 True 的值：<br /><br /> -   **httpHelpPageEnabled** ，則為 True<br />-   **httpsHelpPageEnabled** ，則為 True<br />-   **includeExceptionDetailInFaults** ，則為 True|  

 按一下 [ **[確定]** 以關閉 [Wcf-custom 傳輸屬性] 對話方塊中，然後按一下**確定**] 以關閉 [接收位置屬性] 對話方塊。  

### <a name="create-a-biztalk-server-send-port"></a>建立 BizTalk Server 傳送埠  
 請依照下列主題中的步驟[如何建立傳送埠](http://go.microsoft.com/fwlink/?LinkID=154845)(http://go.microsoft.com/fwlink/?LinkID=154845) BizTalk Server 文件，來建立**靜態單向**傳送埠。 建立傳送埠時，保留所有屬性的預設值，除非下表所述：  

|屬性|值|  
|--------------|-----------|  
|General\Name|BTSLoadTest.Messaging.Send.WCF 自訂|  
|General\Send 處理常式|TxHost|  
|General\Send 管線|PassThruTransmit|  
|Filters\Name|BTS.ReceivePortName|  
|Filters\Operator|==|  
|Filters\Value|BTSLoadTest.Messaging.OneWay.ReceivePort|  
|藉由 Filters\Group|並**附註：** 篩選以正確的值設定這些屬性，如果應該顯示為`BTS.ReceivePortName == BTSLoadTest.Messaging.OneWay.ReceivePort`b 中的 [傳送埠屬性] 對話方塊的 [篩選] 頁面的底部所示ox。 因為套用此篩選之後，此傳送埠訂閱透過名為 BTSLoadTest.Messaging.OneWay.ReceivePort 接收埠的 BizTalk Server 收到任何訊息。|  
|追蹤|確定不會核取所有方塊。|  
|General\Type|選取 [ **Wcf-custom**從下拉式清單，然後按一下**設定**] 按鈕，這會顯示**Wcf-custom 傳輸屬性**對話方塊中，這應該是下一節所述設定**來設定 Wcf-custom 傳送傳輸**。|  

### <a name="configure-the-wcf-custom-send-transport"></a>設定 Wcf-custom 傳送傳輸  
 在  **Wcf-custom 傳輸屬性**對話方塊顯示在建立 BizTalk Server 傳送埠時，所有屬性都保留預設值以外下, 表所述：  

|屬性|值|  
|--------------|-----------|  
|General\Address (URI)|net.tcp://*\<電腦名稱\>*: 2001年/TCP1**重要事項：***\<電腦名稱\>* 是預留位置用來裝載 IndigoService.exe 實際電腦名稱，可使用透過 WCF 傳送的訊息。   因為 IndigoService.exe 需要極少的資源，通常是使用 BizTalk Server 群組資料庫的 SQL Server 電腦上執行 IndigoService.exe 完全可以接受。 IndigoService.exe 屬於 BizTalk 基準測試精靈，將會位於[BizTalk 基準精靈](http://go.microsoft.com/fwlink/?LinkID=186347)(http://go.microsoft.com/fwlink/?LinkID=186347)。|  
|Binding\Binding 類型|**customBinding**|  

 如同 WCF 自訂繫結類型大多**customBinding**繫結型別會公開數個屬性，它應該設定為下列值：  

1.  底下**繫結**沒有 區段**CustomBindingElement**以及相關聯的屬性**組態**一節。 保留的所有值中的組態區段**CustomBindingElement**屬性的預設值。  

2.  然後在**CustomBindingElement**上按一下滑鼠右鍵**textMessageEncoding** ，然後選取**移除延伸模組 (Del)**。 同樣地，以滑鼠右鍵按一下**httpTransport** ，然後選取**移除延伸模組 (Del)**。  

3.  現在以滑鼠右鍵按一下**CustomBindingElement** ，然後選取**新增擴充功能集**以顯示**選取繫結元素延伸模組** 對話方塊。  

4.  選取  **binaryMessageEncoding**然後按一下**確定**加入**binaryMessageEncoding**項目延伸。 重複步驟，以顯示**選取繫結元素延伸模組**對話方塊並捲軸下可用的項目延伸的清單直到您看到**tcpTransport**元素延伸模組，選取**tcpTransport**然後按一下**確定**。  

5.  底下**CustomBindingElement**選取**tcpTransport**項目和中的組態區段**tcpTransport**，保留所有屬性的預設值以外，做為下表所述：  

    |屬性|值|  
    |--------------|-----------|  
    |connectionBufferSize|2097152|  
    |maxBufferSize|2097152|  
    |maxPendingAccepts|400|  
    |maxPendingConnections|400|  
    |listenBacklog|400|  
    |maxBufferPoolSize|2097152|  
    |maxReceivedMessageSize|2097152|  

6.  底下**tcpTransport**項目選取**Namedpipetransport**項目，並保留預設值的所有屬性都值除了**maxOutboundConnectionsPerEndpoint**應設為 400 的值變更的屬性。  

7.  按一下 [ **[確定]** 若要關閉 [Wcf-custom 傳輸屬性] 對話方塊中，然後按一下**確定**] 以關閉 [BTSLoadTest.Messaging.Send.WCF-自訂-傳送埠屬性] 對話方塊。  

### <a name="configure-a-computer-to-consume-messages-sent-by-the-biztalk-server-send-port"></a>將電腦設定為使用 BizTalk Server 傳送埠所傳送的訊息  
 如先前所述，IndigoService.exe 被設計來使用透過 WCF 傳送的訊息。 IndigoService.exe 屬於 BizTalk 基準測試精靈，將會位於[BizTalk 基準精靈](http://go.microsoft.com/fwlink/?LinkID=186347)(http://go.microsoft.com/fwlink/?LinkID=186347)。 若要設定及執行 IndigoService.exe 基於此範例的最簡單的方式是直接下載 BizTalk 基準測試精靈 的 zip 檔案，從[BizTalk 基準測試精靈 下載頁面](http://go.microsoft.com/fwlink/?LinkID=209100)(http://go.microsoft.com/fwlink/?LinkID=209100)並擷取下列 4 個您想要執行 IndigoService.exe 電腦上的檔案：  

1. \IndigoService\bin\Release\IndigoService.exe  

2. \IndigoService\bin\Release\IndigoService.exe.config  

3. \IndigoService\bin\Release\Response.xml  

4. \IndigoService\bin\Release\StartIndigoService.bat  

   然後啟動 IndigoService.exe StartIndigoService.bat 上按兩下。 IndigoService.exe 會取用訊息傳送至 IndigoService.exe.config 檔案中指定的端點：  

   \<端點位址 ="net.tcp: //localhost: 2001年/TCP1 」 繫結 ="netTcpBinding"bindingConfiguration ="Binding1"name ="endpoint1"contract="IndigoService.IServiceTwoWaysVoidNonTransactional"/\>  

   這就是為什麼傳送連接埠位址已與位址 (URI) 的 net.tcp://*\<電腦名稱\>*: 2001年/TCP1  

   因為 IndigoService.exe 需要極少的資源，通常是使用 BizTalk Server 資料庫的 SQL Server 電腦上執行 IndigoService.exe 完全可以接受。  

### <a name="disable-tracking-and-throttling-for-the-biztalk-server-group"></a>停用追蹤和節流 BizTalk Server 群組  
 若要判斷系統，這兩個訊息的絕對最大持續輸送量追蹤和節流應該停用開始負載測試之前。 這可以使用 BizTalk Server 管理主控台，依照下列步驟：  

1. 啟動 BizTalk Server 管理主控台。 按一下 **開始**，指向**所有程式**，指向**BizTalk Server 2010**然後按一下**BizTalk Server 管理**。  

2. 底下**BizTalk Server 管理**、 選取您的 BizTalk 群組，如果有列出，或如果未列出，以滑鼠右鍵按一下**BizTalk Server 管理**，選取**連接至現有的群組**，輸入裝載 BizTalk 群組的 BizTalk Server 管理資料庫旁邊的 SQL Server 名稱**SQL Server 名稱：**，輸入 BizTalk 群組的管理資料庫名稱旁邊**資料庫名稱：** ，然後按一下  **確定**。  

3. 以滑鼠右鍵按一下 [BizTalk 群組] 節點，然後選取**設定**顯示**BizTalk 設定儀表板**。  

4. 按一下以選取**主機**BizTalk 設定儀表板的左側窗格中。  

5. 按一下下拉式清單旁**主機**選取其中一個會在效能測試期間使用的主機。  

6. 將內容保留在其預設值以外下, 表所述：  


   |                          屬性                          |               值                |
   |------------------------------------------------------------|------------------------------------|
   |          **General\Move 至 DTA 資料庫中追蹤資料**          | 如果有勾選，取消核取此方塊。 |
   |                  **僅限 General\32 位元**                   | 如果有勾選，取消核取此方塊。 |
   |          **General\Polling Intervals\Messaging**           |     設為 20000000 值     |
   |        **General\Polling Intervals\Orchestrations**        |     設為 20000000 值     |
   |     **資源型 Throttling\In 同處理序訊息**      |      設定為值為 10000       |
   | **資源型 Throttling\Internal 訊息佇列大小**  |      設定為值為 10000       |
   |     **在 DB 中的資源為基礎 Throttling\Message 計數**      |        設為 0 的值         |
   | **虛擬的 資源為基礎 Throttling\Memory Usage\Process** |        設為 0 的值         |
   |  **根據速率的 Throttling\Publishing\Throttling 覆寫**  |       設定為不要節流       |
   |   **根據速率的 Throttling\Delivery\Throttling 覆寫**   |       設定為不要節流       |


7. 重複步驟 6 中所述，每個主控件的效能測試期間，會使用此程序。  

8. 按一下以選取**主控件執行個體**BizTalk 設定儀表板的左側窗格中。  

9. 按一下下拉式清單旁**主控件執行個體：** 選取其中一個主控件執行個體將用於進行效能測試。  

10. 屬性值保留其預設設定，變更除了 **.NET CLR 最大工作者執行緒**的值**100**並變更 **.NET CLR 最少的背景工作執行緒**到值**25**。  

11. 重複步驟 10 中的效能測試期間，會使用每個主控件執行個體中所述的程序。  

    即使停用追蹤和節流並不以任何方式代表應該要如何處理在生產案例中，因為這些作業會從效能觀點來看，停用它們來了解，則為 true 最大持續性合理，因此耗費資源BizTalk Server 環境的輸送量 (MST)。 這可讓測試人員，清楚看到的調整，任何效能影響已套用至環境。 肯定應該不會停用追蹤，而且如果您一開始就知道您的 BizTalk Server 應用程式，需要追蹤然後您應該啟用追蹤，無法進行引數。 也就是說，**全力應停用節流的效能測試的目的**。 節流是非常適合防止 」 將 「 由於在生產環境中的負載過度而 BizTalk Server。 不過，您不想在效能測試，因為它很昂貴，從效能觀點來看，而且如果節流會在負載測試期間則您必須判斷何種效能層級很難時間期間已啟用節流您BizTalk Server 應用程式可以實際達成的。 下一步 的主題描述如何執行推播超過 MST BizTalk Server 環境，並再調整回使用常數負載測試的實際 MST 的步驟負載測試。 如果已啟用節流設定，然後它會變成幾乎不可能將超過 MST BizTalk 環境，讓您接著可以探索 MST 是什麼真正。